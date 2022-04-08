# Vocabulary Maintenance 

## Content maintenance

The goal is for each controlled vocabulary to be stored and published using a 'semantic web' representation - typically using [SKOS](https://www.w3.org/TR/skos-primer/) for basic terms, definitions and (optionally) hierarchy; else using a domain-specific ontology if available. 
However, while it is eminently suitable for this application, it is a rather esoteric technology, unfamilar to most scientists and developers, and generally unsuitable for the development and maintenance of vocabaularies by subject-matter experts. 

For most users, the most convenient tool for development and maintenance of vocabaulary content is an Excel file (.xls or .xlsx format). 
Provided this is set up using a suitable template, the semantic web representation can be generated directly using [SKOS Play!](https://skos-play.sparna.fr/play/convert), 

## Generating RDF (SKOS) 

Go to https://skos-play.sparna.fr/play/convert 
Check **In a local file on my computer** and select the xslx file. 

**Convert**

Copy result into `xxxx.ttl` file. 

**Edit for Loading in RVA**

In your editor of choice, in the .ttl file delete all `skos:inScheme` links (e.g. `skos:inScheme s:swcm-1992;`) that are associated with resources of `rdf:type skos:Collection`. 

(This deals with the fact that RVA applies a more rigorous interpretation of the SKOS conformance than SKOS-Play!.)

## Loading in RVA

Login to https://vocabs.ardc.edu.au and go to 'My Vocabs'. 

+ Add a new Vocabulary

Select owner

Enter metadata. 

Add a version - give the version a name like 'FedUni Version' 

Add Access Point
- TTL
- Select scma.ttl
- Add
- Display Collections (**not ConceptScheme**)
- Import, make available

Add this version

Publish


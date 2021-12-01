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

Copy result into `scma.ttl` file. 

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

## Loading in LDR

### Preparing RDF for LDR

#### 1. Register file

1. make a copy of scma.ttl as `scma-register.ttl`
2. edit `scma-register.ttl`
    - remove everything exept the `skos:ConceptScheme` resource
    - Make it (also) a `reg:Register`
        - replace `skos:ConceptScheme` with `<http://purl.org/linked-data/registry#Register> , skos:ConceptScheme` 
    - convert its URI to a relative address 
        - replace `<http://anzsoil.org/def/au/scma>` with `<scma>`
    - remove the `skos:hasTopConcept` links

This file can now be loaded into LDR to create a new 'Register', whose URI will be an immediate child of the parent register. 

#### 2. Content file

1. Make a second copy of scma.ttl as `scma-content.ttl` 
2. edit `scma-content.ttl`
    - remove the `skos:ConceptScheme` resource
    - convert all the concept and collection URIs to relative addresses 
        - replace regex `s:([0-9][0-9A-Za-z_\-]*)` with `<$1>`
    - convert the navigation links to use the relative address 
        - replace `ui:topMemberOf <http://anzsoil.org/def/au/scma>` with `ui:topMemberOf <>` 

### Loading RDF into LDR

1. navigate to the register where you want to load the vocabaulary
2. Create register 
    - Admin -> Add registration 
    - Upload -> Choose files --> choose `scma-register.ttl`
    - Upload and register
3. Load content
    - navigate to the register that you just created
    - Admin -> Add registration 
    - Upload -> Choose files --> choose `scma-content.ttl`
    - Upload and register

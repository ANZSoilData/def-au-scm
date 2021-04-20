# aus-vocab
Australian soil vocabularies.

Well governed soil vocabularies from various national and other recognised authorities (for example the handbooks issued by the Australian National Committee on Soil and Terrain).
Excel spreadsheets are converted to RDF vocabularies (SKOS) using https://skos-play.sparna.fr/play/home

Both the excel spreadsheets and the https://skos-play.sparna.fr/play/home outputs, RDF serialisation files (e.g. ttl.) are stored in this repository where they are managed and versioned.
These RDF serialisation files are loaded into CSIRO linked data registry (LDR). The LDR ervice provides management and public access to codes, codelists, vocabularies, ontologies and other reference resources authorized or adopted by CSIRO.

The experimental (sandbox) into which these files are lodaded for checking is http://registry.it.csiro.au/sandbox/soil/
The permanent location is http://anzsoil.org/def/au/
 
To make it easy to load in the sandbox and then transfer to the permanent location, the entries should have local identifiers. This regex will make the change the `s:` identifiers throughout the file – 
Find s:([0-9][0-9a-zA-Z]*)
Replace <$1>

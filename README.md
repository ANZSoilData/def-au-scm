# aus-vocab
Australian soil vocabularies.

Well governed soil vocabularies from various national and other recognised authorities (for example the handbooks issued by the Australian National Committee on Soil and Terrain).

Excel spreadsheets of structure compatable with https://skos-play.sparna.fr/play/home are stored here, as are the skos-play ouputs RDF serialisation files (e.g. ttl.) 

The Excel spreadsheets are converted to RDF vocabularies (SKOS) using https://skos-play.sparna.fr/play/home

Here both the Excel sheets and RDF serialisation files (e.g. ttl.) are stored for managing requests and change control

The RDF serialisation files are loaded into CSIRO linked data registry (LDR). The LDR Service provides management and public access to codes, codelists, vocabularies, ontologies and other reference resources authorized or adopted by CSIRO.

The experimental (sandbox) into which these files are lodaded for checking is http://registry.it.csiro.au/sandbox/soil/
The permanent location is http://anzsoil.org/def/au/
 
To make it easy to load in the sandbox and then transfer to the permanent location, the entries should have local identifiers. This regex will make the change the `s:` identifiers throughout the file – 
Find s:([0-9][0-9a-zA-Z]*)
Replace <$1>

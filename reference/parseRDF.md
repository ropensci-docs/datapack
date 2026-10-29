# Parse an RDF/XML resource map from a file

parseRDF reads a file containing an RDF model in RDF/XML format and
initializes a ResourceMap based on this content.

## Usage

``` r
parseRDF(x, rdf, ...)

# S4 method for class 'ResourceMap'
parseRDF(
  x,
  rdf,
  asText = FALSE,
  name = "rdfxml",
  mimeType = "application/rdf+xml",
  ...
)
```

## Arguments

- x:

  ResourceMap

- rdf:

  A file or character value containing a resource map that will be
  parsed into the ResourceMap object

- ...:

  Additional parameters (not yet used).

- asText:

  A logical value. If TRUE, then the 'rdf' parameter is a character
  vector, if FALSE then it is the name of a file to read.

- name:

  The name of the RDF xml parser, the default is "rdfxml".

- mimeType:

  A character value containing the RDF format type. The default is
  "application/rdf+xml".

## Value

x the ResourceMap containing the parsed RDF/XML content

## Details

This method resets the slot ResourceMap@world so any previously stored
triples are discarded, allowing for a clean model object in which to
parse the new RDF content into. It is assumed that the content is a
valid ORE resource map therefor no validation checks specific to the
OAI-ORE content model are performed.

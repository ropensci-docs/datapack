# Serialize a ResouceMap

The Redland RDF library is used to serialize the ResourceMap RDF model
to a file as RDF/XML.

## Usage

``` r
serializeRDF(x, ...)

# S4 method for class 'ResourceMap'
serializeRDF(
  x,
  file,
  syntaxName = "rdfxml",
  mimeType = "application/rdf+xml",
  namespaces = data.frame(namespace = character(), prefix = character(), stringsAsFactors
    = FALSE),
  syntaxURI = NA_character_
)
```

## Arguments

- x:

  a ResourceMap

- ...:

  Additional parameters

- file:

  the file to which the ResourceMap will be serialized

- syntaxName:

  name of the syntax to use for serialization - default is "rdfxml"

- mimeType:

  the mimetype of the serialized output - the default is
  "application/rdf+xml"

- namespaces:

  a data frame containing one or more namespaces and their associated
  prefix

- syntaxURI:

  A URI of the serialized syntax

## Value

status of the serialization (non)

## See also

[`ResourceMap-class`](https://docs.ropensci.org/datapack/reference/ResourceMap-class.md)

## Examples

``` r
dp <- new("DataPackage")
data <- charToRaw("1,2,3\n4,5,6")
do1 <- new("DataObject", id="id1", data, format="text/csv")
do2 <- new("DataObject", id="id2", data, format="text/csv")
dp <- addMember(dp, do1)
dp <- addMember(dp, do2)
dp <- insertRelationship(dp, subjectID="id1", objectIDs="id2", 
  predicate="http://www.w3.org/ns/prov#wasDerivedFrom")
relations <- getRelationships(dp)
resmap <- new("ResourceMap")
resmap <- createFromTriples(resmap, relations, id="myuniqueid")
if (FALSE) { # \dontrun{
tf <- tempfile(fileext=".xml")
serializeRDF(resmap, tf)
} # }
```

# Create an OAI-ORE resource map from the package

The DataPackage is serialized as a OAI-ORE resource map to the specified
file.

## Usage

``` r
serializePackage(x, ...)

# S4 method for class 'DataPackage'
serializePackage(
  x,
  file,
  id = NA_character_,
  syntaxName = "rdfxml",
  mimeType = "application/rdf+xml",
  namespaces = data.frame(namespace = character(), prefix = character(), stringsAsFactors
    = FALSE),
  syntaxURI = NA_character_,
  resolveURI = NA_character_,
  creator = NA_character_
)
```

## Arguments

- x:

  A DataPackage object

- ...:

  Additional arguments

- file:

  The file to which the ResourceMap will be serialized

- id:

  A unique identifier for the serialization. The default value is the id
  assigned to the DataPackage when it was created.

- syntaxName:

  The name of the syntax to use for serialization - default is "rdfxml"

- mimeType:

  The mimetype of the serialized output - the default is
  "application/rdf+xml"

- namespaces:

  A data frame containing one or more namespaces and their associated
  prefix

- syntaxURI:

  URI of the serialization syntax

- resolveURI:

  A character string containing a URI to prepend to datapackage
  identifiers

- creator:

  A `character` string containing the creator of the package.

## Details

The resource map that is created is serialized by default as RDF/XML.
Other serialization formats can be specified using the `syntaxName` and
`mimeType` parameters. Other available formats include:

|                |                       |
|----------------|-----------------------|
| **syntaxName** | **mimeType**          |
| json           | application/json      |
| ntriples       | application/n-triples |
| turtle         | text/turtle           |
| dot            | text/x-graphviz       |

Note that the `syntaxName` and `mimeType` arguments together specify o
serialization format.

Also, for packages that will be uploaded to the DataONE network,
"rdfxml" is the only accepted format.

The resolveURI string value is prepended to DataPackage member
identifiers in the resulting resource map. If no resolveURI value is
specified, then 'https://cn.dataone.org/cn/v1/resolve' is used.

## See also

[`DataPackage-class`](https://docs.ropensci.org/datapack/reference/DataPackage-class.md)

## Examples

``` r
dp <- new("DataPackage")
data <- charToRaw("1,2,3\n4,5,6")
do <- new("DataObject", id="do1", dataobj=data, format="text/csv", user="jsmith")
dp <- addMember(dp, do)
data2 <- charToRaw("7,8,9\n10,11,12")
do2 <- new("DataObject", id="do2", dataobj=data2, format="text/csv", user="jsmith")
dp <- addMember(dp, do2)
dp <- describeWorkflow(dp, sources=do, derivations=do2)
if (FALSE) { # \dontrun{
td <- tempdir()
status <- serializePackage(dp, file=paste(td, "resmap.json", sep="/"), syntaxName="json",  
    mimeType="application/json")
status <- serializePackage(dp, file=paste(td, "resmap.xml", sep="/"), syntaxName="rdfxml", 
    mimeType="application/rdf+xml")
status <- serializePackage(dp, file=paste(td, "resmap.ttl", sep="/"), syntaxName="turtle", 
    mimeType="text/turtle")
} # }
```

# Serialize A DataPackage into a BagIt Archive File

The BagIt packaging format
<https://datatracker.ietf.org/doc/html/draft-kunze-bagit-08> is used to
prepare an archive file that contains the contents of a DataPackage.

## Usage

``` r
serializeToBagIt(x, ...)

# S4 method for class 'DataPackage'
serializeToBagIt(
  x,
  mapId = NA_character_,
  syntaxName = NA_character_,
  namespaces = data.frame(),
  mimeType = NA_character_,
  syntaxURI = NA_character_,
  resolveURI = NA_character_,
  creator = NA_character_,
  ...
)
```

## Arguments

- x:

  A DataPackage object

- ...:

  Additional arguments

- mapId:

  A unique identifier for the package resource map. If not specified,
  one will be automatically generated.

- syntaxName:

  The name of the syntax to use for the resource map serialization,
  defaults to "rdfxml"

- namespaces:

  An optional data frame containing one or more namespaces and their
  associated prefix for the resource map serialization.

- mimeType:

  The mimetype for the resource map serialization, defaults to
  "application/rdf+xml".

- syntaxURI:

  An optional string specifying the URI for the resource map
  serialization.

- resolveURI:

  A character string containing a URI to prepend to datapackage
  identifiers for the resource map.

- creator:

  A `character` string containing the creator of the package.

## Value

The file name that contains the BagIt zip archive. Recursively
determines the name for a science metadata object. The base file name
(eml, datacite, science-metadata, etc) should stay the same. Call the
method with the base name and the number of existing files to start
with. This is most likely 0. If there's a count defined, add it to the
end of the file in () Then call the method again with count += 1
Eventually a free file name will be found, and then the function returns
that name

## Details

A BagIt Archive File is created by copying each member of a DataPackage,
and preparing files that describe the files in the archive, including
information about the size of the files and a checksum for each file. An
OAI-ORE resource map is automatically created and added to the archive.
These metadata files and the data files are then packaged into a single
zip file.

## See also

[`DataPackage-class`](https://docs.ropensci.org/datapack/reference/DataPackage-class.md)

For more information and examples regarding the parameters specifying
the creation of the resource map, see
[serializePackage](https://docs.ropensci.org/datapack/reference/serializePackage.md).

## Examples

``` r
# Create the first data object
dp <- new("DataPackage")
data <- charToRaw("1,2,3,5,6")
do <- new("DataObject", id="do1", dataobj=data, format="text/csv", user="jsmith")
dp <- addMember(dp, do)
# Create a second data object
data2 <- charToRaw("7,8,9,4,10,11")
do2 <- new("DataObject", id="do2", dataobj=data2, format="text/csv", user="jsmith")
dp <- addMember(dp, do2)
# Create a relationship between the two data objects
dp <- describeWorkflow(dp, sources="do2", derivations="do2")
# Write out the data package to a BagIt file
if (FALSE) { # \dontrun{
bagitFile <- serializeToBagIt(dp, syntaxName="json", mimeType="application/json")
} # }
```

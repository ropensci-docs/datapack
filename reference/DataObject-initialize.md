# Initialize a DataObject

When initializing a DataObject using passed in data, one can either pass
in the `'id'` param as a `'SystemMetadata'` object, or as a
`'character'` string representing the identifier for an object along
with parameters for format, user,and associated member node. If `'data'`
is not missing, the `'data'` param holds the `'raw'` data. Otherwise,
the `'filename'` parameter must be provided, and points at a file
containing the bytes of the data.

## Usage

``` r
# S4 method for class 'DataObject'
initialize(
  .Object,
  id = NA_character_,
  dataobj = NA,
  format = NA_character_,
  user = NA_character_,
  mnNodeId = NA_character_,
  filename = NA_character_,
  seriesId = NA_character_,
  mediaType = NA_character_,
  mediaTypeProperty = list(),
  dataURL = NA_character_,
  targetPath = NA_character_,
  checksumAlgorithm = "SHA-256"
)
```

## Arguments

- .Object:

  the DataObject instance to be initialized

- id:

  the identifier for the DataObject, unique within its repository.
  Optionally this can be an existing SystemMetadata object

- dataobj:

  the bytes of the data for this object in `'raw'` format, optional if
  `'filename'` is provided

- format:

  the format identifier for the object, e.g."text/csv",
  "eml://ecoinformatics.org/eml-2.1.1"

- user:

  the identity of the user owning the package, typically in X.509 format

- mnNodeId:

  the node identifier for the repository to which this object belongs.

- filename:

  the filename for the fully qualified path to the data on disk,
  optional if `'data'` is provided

- seriesId:

  A unique string to identifier the latest of multiple revisions of the
  object.

- mediaType:

  The When specified, indicates the IANA Media Type (aka MIME-Type) of
  the object. The value should include the media type and subtype (e.g.
  text/csv).

- mediaTypeProperty:

  A list, indicates IANA Media Type properties to be associated with the
  parameter `"mediaType"`

- dataURL:

  A character string containing a URL to remote data (a repository) that
  this DataObject represents.

- targetPath:

  An optional string that denotes where the file should go in a
  downloaded package

- checksumAlgorithm:

  A character string specifying the checksum algorithm to use

## Details

If filesystem storage is used for the data associated with a DataObject,
care must be taken to not modify or remove that file in R or via other
facilities while the DataObject exists in the R session. Changes to the
object are not detected and will result in unexpected results. Also, if
the `'dataobj'` parameter is used to specify the data source, then
`'filename'` argument may also be specified, but in this case the value
`'filename'` parameter is used to tell DataONE the filename to create
when this file is downloaded from a repository.

## See also

[`DataObject-class`](https://docs.ropensci.org/datapack/reference/DataObject-class.md)

## Examples

``` r
data <- charToRaw("1,2,3\n4,5,6\n")
do <- new("DataObject", "id1", dataobj=data, "text/csv", 
  "uid=jones,DC=example,DC=com", "urn:node:KNB", targetPath="data/rasters/data.tiff")
```

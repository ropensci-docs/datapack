# DataObject wraps raw data with system-level metadata

DataObject is a wrapper class that associates raw data or a data file
with system-level metadata describing the data. The system metadata
includes attributes such as the object's identifier, type, size,
checksum, owner, version relationship to other objects, access rules,
and other critical metadata. The SystemMetadata is compliant with the
DataONE federated repository network's definition of SystemMetadata, and
is encapsulated as a separate object of type
[`SystemMetadata`](https://docs.ropensci.org/datapack/reference/SystemMetadata.md)
that can be manipulated as needed. Additional science-level and
domain-specific metadata is out-of-scope for SystemMetadata, which is
intended only for critical metadata for managing objects in a repository
system.

## Details

A DataObject can be constructed by passing the data and SystemMetadata
to the new() method, or by passing an identifier, data, format, user,
and DataONE node identifier, in which case a SystemMetadata instance
will be generated with these fields and others that are calculated (such
as size and checksum).

Data are associated with the DataObject either by passing it as a
`'raw'` value to the `'dataobj'` parameter in the constructor, which is
then stored in memory, or by passing a fully qualified file path to the
data in the `'filename'` parameter, which is then stored on disk. One of
dataobj or filename is required. Use the `'filename'` approach when data
are too large to be managed effectively in memory. Callers can access
the `'filename'` slot to get direct access to the file, or can call
`'getData()'` to retrieve the contents of the data or file as a raw
value (but this will read all of the data into memory).

## Slots

- `sysmeta`:

  A value of type `"SystemMetadata"`, containing the metadata about the
  object

- `data`:

  A value of type `"raw"`, containing the data represented in this
  object

- `filename`:

  A character value that contains the fully-qualified path to the object
  data on disk

- `dataURL`:

  A character value for the URL used to load data into this DataObject

- `updated`:

  A list containing logical values which indicate if system metadata or
  the data object have been updated since object creation.

- `oldId`:

  A character string containing the previous identifier used, before a
  `"replaceMember"` call.

- `targetPath`:

  An optional character string holding the path of where the file is
  placed in a downloaded package.

## Methods

- [`initialize`](https://docs.ropensci.org/datapack/reference/DataObject-initialize.md):

  : Initialize a DataObject

- [`addAccessRule`](https://docs.ropensci.org/datapack/reference/addAccessRule.md):

  : Add a Rule to the AccessPolicy

- [`canRead`](https://docs.ropensci.org/datapack/reference/canRead.md):

  : Test whether the provided subject can read an object.

- [`getData`](https://docs.ropensci.org/datapack/reference/getData.md):

  : Get the data content of a specified data object

- [`getFormatId`](https://docs.ropensci.org/datapack/reference/getFormatId.md):

  : Get the FormatId of the DataObject

- [`getIdentifier`](https://docs.ropensci.org/datapack/reference/getIdentifier.md):

  : Get the Identifier of the DataObject

- [`hasAccessRule`](https://docs.ropensci.org/datapack/reference/hasAccessRule.md):

  : Determine if an access rules exists for a DataObject.

- [`setPublicAccess`](https://docs.ropensci.org/datapack/reference/setPublicAccess.md):

  : Add a Rule to the AccessPolicy to make the object publicly readable.

- [`updateXML`](https://docs.ropensci.org/datapack/reference/updateXML.md):

  : Update selected elements of the xml content of a DataObject

## See also

[`datapack`](https://docs.ropensci.org/datapack/reference/datapack.md)

## Examples

``` r
data <- charToRaw("1,2,3\n4,5,6\n")
targetPath <- "myData/time-trials/trial_data.csv"
do <- new("DataObject", "id1", dataobj=data, "text/csv", 
  "uid=jones,DC=example,DC=com", "urn:node:KNB", targetPath=targetPath)
getIdentifier(do)
#> [1] "id1"
getFormatId(do)
#> [1] "text/csv"
getData(do)
#>  [1] 31 2c 32 2c 33 0a 34 2c 35 2c 36 0a
canRead(do, "uid=anybody,DC=example,DC=com")
#> [1] FALSE
do <- setPublicAccess(do)
canRead(do, "public")
#> [1] TRUE
canRead(do, "uid=anybody,DC=example,DC=com")
#> [1] TRUE
# Also can create using a file for storage, rather than memory
if (FALSE) { # \dontrun{
tf <- tempfile()
con <- file(tf, "wb")
writeBin(data, con)
close(con)
targetPath <- "myData/time-trials/trial_data.csv"
do <- new("DataObject", "id1", format="text/csv", user="uid=jones,DC=example,DC=com", 
  mnNodeId="urn:node:KNB", filename=tf, targetPath=targetPath)
} # }
```

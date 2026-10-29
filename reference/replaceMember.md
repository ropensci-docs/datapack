# Replace the raw data or file associated with a DataObject

A DataObject is a container for data that can be either an R raw object
or a file on local disk. The `replaceMember` method can be used to
update the date that a DataObject contains, for a DataObject that is a
member of a DataPackage, substituting a new file or raw object in the
specified DataObject.

## Usage

``` r
replaceMember(x, do, ...)

# S4 method for class 'DataPackage'
replaceMember(
  x,
  do,
  replacement,
  formatId = NA_character_,
  mediaType = NA_character_,
  mediaTypeProperty = NA_character_,
  newId = NA_character_,
  ...
)
```

## Arguments

- x:

  A DataPackage instance

- do:

  A DataObject instance

- ...:

  (Not yet used)

- replacement:

  A `raw` object or `character` (for filename) that will replace the
  current value in the DataObject `do`.

- formatId:

  A value of type `"character"`, the DataONE object format for the
  object.

- mediaType:

  A value of type `"character"`, the IANA Media Type (aka MIME-Type) of
  the object, e.g. "text/csv".

- mediaTypeProperty:

  A value of type `"list"` of `"character"`, IANA Media Type properties
  for the `"mediaType"` argument.

- newId:

  A value of type `"character"` which will replace the identifier for
  this DataObject.

## Details

The data that is replacing the existing DataObject data may be of a
different format or type than the existing data. Because the data type
and format may change, the system metadata that describes the data can
be updated as well. The `replaceMember` method will update the
SystemMetadata `size`, `checksum` values automatically, but does not
update the `formatId`, `mediaType`, `mediaTypeProperty` unless
requested, so these should be specified in the call to `replaceMember`
if necessary. If the `newId` argument is used, the specified new
identifier will be assigned to the object, otherwise one will be
generated if necessary. This new identifier will be used if the
DataPackage is uploaded to DataONE, and this object is updating an
existing object in DataONE.

## See also

[`DataPackage-class`](https://docs.ropensci.org/datapack/reference/DataPackage-class.md)

## Examples

``` r
# Create a DataObject and add it to the DataPackage
dp <- new("DataPackage")
doIn <- new("DataObject", format="text/csv", 
            filename=system.file("./extdata/pkg-example/binary.csv", package="datapack"))
dp <- addMember(dp, doIn)

# Use the zipped version of the file instead by updating the DataObject
dp <- replaceMember(dp, doIn, 
          replacement=system.file("./extdata/pkg-example/binary.csv.zip", 
          package="datapack"),
                    formatId="application/zip")
```

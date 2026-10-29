# Remove the Specified Member from the Package

Given the identifier of a DataObject in a DataPackage, delete the
DataObject from the DataPackage.

## Usage

``` r
removeMember(x, ...)

# S4 method for class 'DataPackage'
removeMember(x, do, removeRelationships = FALSE)
```

## Arguments

- x:

  a DataPackage object

- ...:

  (Not yet used)

- do:

  The package member to remove, either as a `"DataObject"` or
  `"character"` (for the object identifier)

- removeRelationships:

  A `logical` value. If TRUE, package relationships for this package
  member are removed. Default is FALSE.

## Details

The `removeMember` method removes the specified DataObject from the
DataPackage. In addition, any package relationships that included the
DataObject are removed.

## See also

[`DataPackage-class`](https://docs.ropensci.org/datapack/reference/DataPackage-class.md)

## Examples

``` r
dp <- new("DataPackage")
data <- charToRaw("1,2,3\n4,5,6")
do <- new("DataObject", id="myNewId", dataobj=data, format="text/csv", user="jsmith")
dp <- addMember(dp, do)
# Remove the package member and any provenance relationships that reference it.
removeMember(dp, "myNewId", removeRelationships=TRUE)
#> This package does not contain any DataObjects.
```

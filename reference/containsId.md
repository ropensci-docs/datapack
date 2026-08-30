# Returns true if the specified object is a member of the package

Returns true if the specified object is a member of the package

## Usage

``` r
containsId(x, ...)

# S4 method for class 'DataPackage'
containsId(x, identifier)
```

## Arguments

- x:

  A DataPackage object

- ...:

  (Not yet used)

- identifier:

  The DataObject identifier to check for inclusion in the DataPackage

## Value

A logical - a value of TRUE indicates that the DataObject is in the
DataPackage

## See also

[`DataPackage-class`](https://docs.ropensci.org/datapack/reference/DataPackage-class.md)

## Examples

``` r
dp <- new("DataPackage")
data <- charToRaw("1,2,3\n4,5,6")
id <- "myNewId"
do <- new("DataObject", id=id, dataobj=data, format="text/csv", user="jsmith")
dp <- addMember(dp, do)
isInPackage <- containsId(dp, identifier="myNewId")
```

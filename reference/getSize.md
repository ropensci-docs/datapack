# Get the Count of Objects in the Package

Get the Count of Objects in the Package

## Usage

``` r
getSize(x, ...)

# S4 method for class 'DataPackage'
getSize(x)
```

## Arguments

- x:

  A DataPackage instance

- ...:

  (not yet used)

## Value

The number of object in the Package

## See also

[`DataPackage-class`](https://docs.ropensci.org/datapack/reference/DataPackage-class.md)

## Examples

``` r
dp <- new("DataPackage")
data <- charToRaw("1,2,3\n4,5,6")
do <- new("DataObject", dataobj=data, format="text/csv", user="jsmith")
dp <- addMember(dp, do)
getSize(dp)
#> [1] 1
```

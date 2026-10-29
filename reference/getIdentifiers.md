# Get the Identifiers of Package Members

The identifiers of the objects in the package are retrieved and returned
as a list.

## Usage

``` r
getIdentifiers(x, ...)

# S4 method for class 'DataPackage'
getIdentifiers(x)
```

## Arguments

- x:

  A DataPackage instance

- ...:

  (not yet used)

## Value

A list of identifiers

## See also

[`DataPackage-class`](https://docs.ropensci.org/datapack/reference/DataPackage-class.md)

## Examples

``` r
dp <- new("DataPackage")
data <- charToRaw("1,2,3\n4,5,6")
do <- new("DataObject", dataobj=data, format="text/csv", user="jsmith")
dp <- addMember(dp, do)
getIdentifiers(dp)
#> [1] "urn:uuid:0232b4b3-163e-4536-977d-9eaf1180db7e"
```

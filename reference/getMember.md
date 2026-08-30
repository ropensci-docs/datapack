# Return the Package Member by Identifier

Given the identifier of a member of the data package, return the
DataObject representation of the member.

## Usage

``` r
getMember(x, ...)

# S4 method for class 'DataPackage'
getMember(x, identifier)
```

## Arguments

- x:

  A DataPackage instance

- ...:

  (Not yet used)

- identifier:

  A DataObject identifier

## Value

A DataObject if the member is found, or NULL if not

## See also

[`DataPackage-class`](https://docs.ropensci.org/datapack/reference/DataPackage-class.md)

## Examples

``` r
dp <- new("DataPackage")
data <- charToRaw("1,2,3\n4,5,6")
do <- new("DataObject", id="myNewId", dataobj=data, format="text/csv", user="jsmith")
dp <- addMember(dp, do)
do2 <- getMember(dp, "myNewId")
```

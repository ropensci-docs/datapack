# Get the data content of a specified data object

Get the data content of a specified data object

## Usage

``` r
getData(x, ...)

# S4 method for class 'DataObject'
getData(x)

# S4 method for class 'DataPackage'
getData(x, id)
```

## Arguments

- x:

  DataObject or DataPackage: the data structure from where to get the
  data

- ...:

  Additional arguments

- id:

  Missing or character: if `'x'` is DataPackage, the identifier of the
  package member to get data from

## Value

raw representation of the data

## See also

[`DataObject-class`](https://docs.ropensci.org/datapack/reference/DataObject-class.md)

## Examples

``` r
data <- charToRaw("1,2,3\n4,5,6\n")
do <- new("DataObject", "id1", dataobj=data, "text/csv", 
  "uid=jones,DC=example,DC=com", "urn:node:KNB")
bytes <- getData(do)
dp <- new("DataPackage")
data <- charToRaw("1,2,3\n4,5,6")
do1 <- new("DataObject", id="id1", data, format="text/csv", user="smith", mnNodeId="urn:node:KNB")
dp <- addMember(dp, do1)
bytes <- getData(dp, "id1")
```

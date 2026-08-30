# Get the FormatId of the DataObject

Get the FormatId of the DataObject

## Usage

``` r
getFormatId(x, ...)

# S4 method for class 'DataObject'
getFormatId(x)
```

## Arguments

- x:

  DataObject

- ...:

  (not yet used)

## Value

the formatId

## See also

[`DataObject-class`](https://docs.ropensci.org/datapack/reference/DataObject-class.md)

## Examples

``` r
data <- charToRaw("1,2,3\n4,5,6\n")
do <- new("DataObject", "id1", dataobj=data, "text/csv", 
  "uid=jones,DC=example,DC=com", "urn:node:KNB")
fmtId <- getFormatId(do)
```

# Retrieve relationships of package objects

Relationships of objects in a package are defined using the
`'insertRelationship'` call and retrieved using `getRetaionships`. These
relationships are returned in a data frame with `'subject'`,
`'predicate'`, `'objects'` as the columns, ordered by "subject"

## Usage

``` r
getRelationships(x, ...)

# S4 method for class 'DataPackage'
getRelationships(x, condense = F, ...)
```

## Arguments

- x:

  A DataPackage object

- ...:

  (Not yet used)

- condense:

  A logical value, if TRUE then a more easily viewed version of
  relationships are returned.

## See also

[`DataPackage-class`](https://docs.ropensci.org/datapack/reference/DataPackage-class.md)

## Examples

``` r
dp <- new("DataPackage")
insertRelationship(dp, "/Users/smith/scripts/genFields.R",
    "http://www.w3.org/ns/prov#used",
    "https://knb.ecoinformatics.org/knb/d1/mn/v1/object/doi:1234/_030MXTI009R00_20030812.40.1")
#> This package does not contain any DataObjects.
rels <- getRelationships(dp)
```

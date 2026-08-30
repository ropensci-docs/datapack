# Update package relationships by replacing an old identifier with a new one

When package members are updated, they receive a new identifier
(replaceMember). It is therefor necessary to update the package
relationships to update occurrences of the old identifier with the new
one when the old identifier appears in the "subject" or "object" of a
relationship.

## Usage

``` r
updateRelationships(x, ...)

# S4 method for class 'DataPackage'
updateRelationships(x, id, newId, ...)
```

## Arguments

- x:

  A DataPackage object

- ...:

  (Not yet used)

- id:

  A character value containing the identifier to be replaced.

- newId:

  A character value containing the identifier that will replace the old
  identifier.

## See also

[`DataPackage-class`](https://docs.ropensci.org/datapack/reference/DataPackage-class.md)

# Get the RDF relationships stored in the ResourceMap

The `getTriples` method extracts the RDF relationships from a
ResourceMap.

## Usage

``` r
getTriples(x, ...)

# S4 method for class 'ResourceMap'
getTriples(x, filter = TRUE, identifiers = list(), ...)
```

## Arguments

- x:

  ResourceMap

- ...:

  Additional parameters (not yet implemented).

- filter:

  A `logical` value. If TRUE, then DataONE packaging relationships are
  omitted.

- identifiers:

  A list of `character` values of the identifiers of DataPackage
  members.

## Value

x A data.frame containing the relationships from the ResourceMap

## Details

The `filter` argument causes DataONE packaging relationships to be
removed. A description of these can be viewed at
https://purl.dataone.org/architecture/design/DataPackage.html. The
`identifiers` parameter can contain a list of DataPackage members for
which the identifiers will be 'demoted', that is any relationship that
has these identifiers as a URL as the subject or object will be changed
to the 'bare' identifier. The intent of these two parameter is to
transform the DataPackage to a 'local' state, so that it can be more
easily updated locally.

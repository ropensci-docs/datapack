# Record derivation relationships between objects in a DataPackage

Record a derivation relationship that expresses that a target object has
been derived from a source object. For use with DataONE, a best practice
is to specify the subject and predicate as DataONE persistent
identifiers
(https://mule1.dataone.org/ArchitectureDocs-current/design/PIDs.html).
If the objects are not known to DataONE, then local identifiers can be
used, and these local identifiers may be promoted to DataONE PIDs when
the package is uploaded to a DataONE member node.

## Usage

``` r
recordDerivation(x, ...)

# S4 method for class 'DataPackage'
recordDerivation(x, sourceID, derivedIDs, ...)
```

## Arguments

- x:

  a DataPackage object

- ...:

  Additional parameters

- sourceID:

  the identifier of the source object in the relationship

- derivedIDs:

  an identifier or list of identifiers of objects that were derived from
  the source

## Details

A derived relationship is created for each value in the list
"objectIDs". For each derivedId, one statement will be added expressing
that it was derived from the sourceId. The predicate is will be an RDF
property (as a IRI) from the W3C PROV specification, namely,
"http://www.w3.org/ns/prov#wasDerivedFrom"

## See also

[`DataPackage-class`](https://docs.ropensci.org/datapack/reference/DataPackage-class.md)

## Examples

``` r
if (FALSE) { # \dontrun{
dp <- new("DataPackage")
recordDerivation(dp, "doi:1234/_030MXTI009R00_20030812.40.1", 
                 "doi:1234/_030MXTI009R00_20030812.45.1")
                     } # }
```

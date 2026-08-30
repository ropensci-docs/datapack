# Add a DataObject to the DataPackage

The DataObject is added to the DataPackage.

## Usage

``` r
addData(x, do, ...)

# S4 method for class 'DataPackage,DataObject'
addData(x, do, mo = NA_character_)
```

## Arguments

- x:

  A DataPackage instance

- do:

  A DataObject instance

- ...:

  (Additional parameters)

- mo:

  A DataObject (containing metadata describing `"do"` ) to associate
  with the science object.

## Value

the updated DataPackage object

## Details

The DataObject `"do"` is added to the DataPackage. If the optional
`"mo"` parameter is specified, then it is assumed that the DataObject
`"mo"` is a metadata object that describes the science object `"do"`
that is being added. The `addData` function will add a relationship to
the DataPackage resource map that indicates that the metadata object
describes the science object using the Citation Typing Ontology (CITO).
Note: this method updates the passed-in DataPackage object. `documents`
and `isDocumentedBy` relationship.

## See also

[`DataPackage-class`](https://docs.ropensci.org/datapack/reference/DataPackage-class.md)

## Examples

``` r
dpkg <- new("DataPackage")
data <- charToRaw("1,2,3\n4,5,6")
metadata <- charToRaw("EML or other metadata document text goes here\n")
md <- new("DataObject", id="md1", dataobj=metadata, format="text/xml", user="smith", 
  mnNodeId="urn:node:KNB")
do <- new("DataObject", id="id1", dataobj=data, format="text/csv", user="smith", 
  mnNodeId="urn:node:KNB")
# Associate the metadata object with the science object. The 'mo' object will be added 
# to the package  automatically, since it hasn't been added yet.
# This method is now deprecated, so suppress warnings if desired. 
suppressWarnings(dpkg <- addData(dpkg, do, md))
```

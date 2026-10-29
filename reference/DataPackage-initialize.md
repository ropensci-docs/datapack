# Initialize a DataPackage object

Initialize a DataPackage object

## Usage

``` r
# S4 method for class 'DataPackage'
initialize(.Object, packageId)
```

## Arguments

- .Object:

  The object being initialized

- packageId:

  The package id to assign to the package

## See also

[`DataPackage-class`](https://docs.ropensci.org/datapack/reference/DataPackage-class.md)

## Examples

``` r
# Create a DataPackage with undefined package id (to be set manually later)
pkg <- new("DataPackage")
# Alternatively, manually assign the package id when the DataPackage object is created
pkg <- new("DataPackage", "urn:uuid:4f953288-f593-49a1-adc2-5881f815e946")
```

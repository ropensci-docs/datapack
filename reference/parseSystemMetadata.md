# Parse an external XML document and populate a SystemMetadata object with the parsed data

Parse an XML representation of system metadata, and set the object slots
of a SystemMetadata object the with obtained values.

## Usage

``` r
parseSystemMetadata(x, ...)

# S4 method for class 'SystemMetadata'
parseSystemMetadata(x, xml, ...)
```

## Arguments

- x:

  The `SystemMetadata` object

- ...:

  Additional arguments passed to other functions or methods

- xml:

  The XML representation of the capabilities, as an
  XMLInternalElementNode

## Value

the SystemMetadata object representing an object

## See also

[`SystemMetadata-class`](https://docs.ropensci.org/datapack/reference/SystemMetadata-class.md)

## Examples

``` r
library(XML)
doc <- xmlParseDoc(system.file("testfiles/sysmeta.xml", package="datapack"), asText=FALSE)
sysmeta <- new("SystemMetadata")
sysmeta <- parseSystemMetadata(sysmeta, xmlRoot(doc))
```

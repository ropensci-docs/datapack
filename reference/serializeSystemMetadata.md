# Serialize a SystemMetadata object to an XML representation

The SystemMetadata object is converted to XML and written to a file.

## Usage

``` r
serializeSystemMetadata(x, ...)

# S4 method for class 'SystemMetadata'
serializeSystemMetadata(x, version = "v1", ...)
```

## Arguments

- x:

  The SystemMetadata instance to be serialized.

- ...:

  (Not currently used)

- version:

  A character string representing the DataONE API version that this
  system will be used with (e.g. "v1", "v2").

## Value

A character value of the filename that the XML representation of the
SystemMetadata object was written to.

the character string representing a SystemMetadata object

## Details

If the `'version'` parameter is specified as \*v2\* then the
SystemMetadata object is serialized according to the DataONE version 2.0
system metadata format.

## See also

[`SystemMetadata-class`](https://docs.ropensci.org/datapack/reference/SystemMetadata-class.md)

## Examples

``` r
library(XML)
doc <- xmlParseDoc(system.file("testfiles/sysmeta.xml", package="datapack"), asText=FALSE)
sysmeta <- new("SystemMetadata")
sysmeta <- parseSystemMetadata(sysmeta, xmlRoot(doc))
sysmetaXML <- serializeSystemMetadata(sysmeta, version="v2")
```

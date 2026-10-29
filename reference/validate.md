# Validate a SystemMetadata object

Validate a system metadata object, ensuring that required fields are
present and of the right type.

## Usage

``` r
validate(x, ...)

# S4 method for class 'SystemMetadata'
validate(x, ...)
```

## Arguments

- x:

  the instance to be validated

- ...:

  (Additional parameters)

## Value

logical, `TRUE` if the SystemMetadata object is valid, else a list of
strings detailing errors

## See also

[`SystemMetadata-class`](https://docs.ropensci.org/datapack/reference/SystemMetadata-class.md)

## Examples

``` r
library(XML)
doc <- xmlParseDoc(system.file("testfiles/sysmeta.xml", package="datapack"), asText=FALSE)
sysmeta <- new("SystemMetadata")
sysmeta <- parseSystemMetadata(sysmeta, xmlRoot(doc))
valid <- validate(sysmeta)
```

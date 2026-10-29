# Update selected elements of the XML content of a DataObject

The data content of the DataObject is updated by using the `xpath`
argument to locate the elements to update with the character value
specified in the `replacement` argument.

## Usage

``` r
updateXML(x, ...)

# S4 method for class 'DataObject'
updateXML(x, xpath = NA_character_, replacement = NA_character_, ...)
```

## Arguments

- x:

  A DataObject instance

- ...:

  Additional parameters (not yet used)

- xpath:

  A `character` value specifying the location in the XML to update.

- replacement:

  A `character` value that will replace the elements found with the
  `xpath`.

## Value

The modified DataObject

## See also

[`DataObject-class`](https://docs.ropensci.org/datapack/reference/DataObject-class.md)

## Examples

``` r
if (FALSE) { # \dontrun{
library(datapack)
dataObj <- new("DataObject", format="text/csv", file=sampleData)
sampleEML <- system.file("extdata/sample-eml.xml", package="datapack")
dataObj <- updateMetadata(dataObj, xpath="", replacement=)
} # }
library(datapack)
# Create the metadata object with a sample EML file
sampleMeta <- system.file("./extdata/sample-eml.xml", package="datapack")
metaObj <- new("DataObject", format="eml://ecoinformatics.org/eml-2.1.1", file=sampleMeta)
# In the metadata object, replace "sample-data.csv" with 'sample-data.csv.zip'
xp <- sprintf("//dataTable/physical/objectName[text()=\"%s\"]", "sample-data.csv")
metaObj <- updateXML(metaObj, xpath=xp, replacement="sample-data.csv.zip")
```

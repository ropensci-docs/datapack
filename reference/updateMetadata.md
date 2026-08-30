# Update selected elements of the XML content of a DataObject in a DataPackage (aka package member)

A DataObject that contains an XML document can be edited by specifying a
path to the elements to edit (an XPath expression) and a value to
replace the text node.

## Usage

``` r
updateMetadata(x, do, ...)

# S4 method for class 'DataPackage'
updateMetadata(x, do, xpath, replacement, newId = NA_character_, ...)
```

## Arguments

- x:

  a DataPackage instance

- do:

  A DataObject instance object, or DataObject identifier

- ...:

  (Not yet used)

- xpath:

  A `character` value specifying the location in the XML to update.

- replacement:

  A `character` value that will replace the elements found with the
  `xpath`.

- newId:

  A value of type `"character"` which will replace the identifier for
  this DataObject.

## Details

This method requires some knowledge of the structure of the metadata
document as well as facility with the XPath language. If the `newId`
argument is used, the specified new identifier will be assigned to the
object, and the previous identifier will be stored in the `oldId` slot,
for possible use when updating the DataObject to a repository. If
`newId` is not used, a new identifier will be generated for the
DataObject only the first time that updateMetadata is called for a
particular object in a DataPackage.

## See also

[`DataPackage-class`](https://docs.ropensci.org/datapack/reference/DataPackage-class.md)

## Examples

``` r
# Create a DataObject and add it to the DataPackage
dp <- new("DataPackage")
sampleMeta <- system.file("./extdata/sample-eml.xml", package="datapack")
id <- "1234"
metaObj <- new("DataObject", id="1234", format="eml://ecoinformatics.org/eml-2.1.1", 
                file=sampleMeta)
dp <- addMember(dp, metaObj)

# In the metadata object, insert the newly assigned data 
xp <- sprintf("//dataTable/physical/distribution[../objectName/text()=\"%s\"]/online/url", 
              "sample-data.csv") 
newURL <- sprintf("https://cn.dataone.org/cn/v2/resolve/%s", "1234")
dp <- updateMetadata(dp, id, xpath=xp, replacement=newURL)
```

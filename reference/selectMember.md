# Return identifiers for objects that match search criteria

Return DataObjects or DataObject identifiers that match search terms.

## Usage

``` r
selectMember(x, ...)

# S4 method for class 'DataPackage'
selectMember(x, name, value, as = "character")
```

## Arguments

- x:

  A DataPackage instance

- ...:

  (Not yet used)

- name:

  The name of the DataObject slot to inspect, for example
  "sysmeta@formatId".

- value:

  A character or logical value to match. If specified as a character
  value, PERL style regular expressions can be used (see ?grepl).

- as:

  A character value to specify the return type, either "DataObject" or
  "character" (the default)

## Value

A list of matching DataObjects or DataObject identifiers. The default is
to return a list of DataObject identifiers.

## Details

The `"selectMember"` method inspects the DataObject slot `"name"` for a
match with `"value"` for each DataObject in a DataPackage. Matching
DataObjects are returned as a list containing either package member
identifiers (character) or the DataObjects themselves, depending on the
value of the `as` parameter.

## See also

[`DataPackage-class`](https://docs.ropensci.org/datapack/reference/DataPackage-class.md)

## Examples

``` r
#' library(datapack)
dp <- new("DataPackage")
# Add the script to the DataPackage
progFile <- system.file("./extdata/pkg-example/logit-regression-example.R", package="datapack")
# An 'id' parameter is not specified, so one will be generated automatically.
progObj <- new("DataObject", format="application/R", filename=progFile)
dp <- addMember(dp, progObj)

# Add a script input to the DataPackage
inFile <- system.file("./extdata/pkg-example/binary.csv", package="datapack") 
inObj <- new("DataObject", format="text/csv", filename=inFile)
dp <- addMember(dp, inObj)

# Add a script output to the DataPackage
outFile <- system.file("./extdata/pkg-example/gre-predicted.png", package="datapack")
outObj <- new("DataObject", format="image/png", file=outFile)
dp <- addMember(dp, outObj)

# Now determine the package member identifier for the R script
progIds  <- selectMember(dp, name="sysmeta@formatId", value="application/R", as="character")
inputId <- selectMember(dp, name="sysmeta@fileName", value="binary.csv")
```

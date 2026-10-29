# Get values for selected DataPackage members

Given a slot name and set of package member identifiers, return slot
values.

## Usage

``` r
getValue(x, ...)

# S4 method for class 'DataPackage'
getValue(x, name, identifiers = NA_character_)
```

## Arguments

- x:

  A DataPackage instance

- ...:

  (Not yet used)

- name:

  A name of a DataObject slot.

- identifiers:

  A list of DataPackage member identifiers

## Value

A list of values for matching slot names and included identifiers.

## Details

If the parameter `identifiers` is provided, then only the DataPackage
members that have identifiers in the provided list will have there
values fetched. If this parameter is not provided, then the values for
all DataPackage members are returned.

## See also

[`DataPackage-class`](https://docs.ropensci.org/datapack/reference/DataPackage-class.md)

## Examples

``` r
dp <- new("DataPackage")
data <- charToRaw("1,2,3\n4,5,6")
do <- new("DataObject", id="myNewId", dataobj=data, format="text/csv", user="jsmith")
dp <- addMember(dp, do)
data <- charToRaw("7,8.9\n4,10,11")
do <- new("DataObject", id="myNewId2", dataobj=data, format="text/csv", user="jsmith")
dp <- addMember(dp, do)
formats <- getValue(dp, name="sysmeta@formatId")
```

# Add a Rule to the AccessPolicy to make the object publicly readable

To be called prior to creating the object in DataONE. When called before
creating the object, adds a rule to the access policy that makes this
object publicly readable. If called after creation, it will only change
the system metadata locally, and will not have any effect on remotely
uploaded copies of the DataObject.

## Usage

``` r
setPublicAccess(x, ...)

# S4 method for class 'DataObject'
setPublicAccess(x)

# S4 method for class 'DataPackage'
setPublicAccess(x, identifiers = list())
```

## Arguments

- x:

  DataObject

- ...:

  (not yet used)

- identifiers:

  A list of `character` values containing package member identifiers
  that will be updated (default is all package members).

## Value

A DataObject with modified access rules.

A DataPackage with modified access rules.

## See also

[`DataObject-class`](https://docs.ropensci.org/datapack/reference/DataObject-class.md)

[`DataObject-class`](https://docs.ropensci.org/datapack/reference/DataObject-class.md)

[`DataPackage-class`](https://docs.ropensci.org/datapack/reference/DataPackage-class.md)

## Examples

``` r
data <- charToRaw("1,2,3\n4,5,6\n")
do <- new("DataObject", "id1", dataobj=data, "text/csv", 
  "uid=jones,DC=example,DC=com", "urn:node:KNB")
do <- setPublicAccess(do)
# First create a sample package with two DataObjects
dp <- new("DataPackage")
data <- charToRaw("1,2,3\n4,5,6\n")
obj <- new("DataObject", id="id1", dataobj=data, format="text/csv")
dp <- addMember(dp, obj)
data2 <- charToRaw("7,8,9\n4,10,11\n")
obj2 <- new("DataObject", id="id2", dataobj=data2, format="text/csv")
dp <- addMember(dp, obj2)
# Now add public read to all package members ("id1", "id2")
dp <- setPublicAccess(dp)
```

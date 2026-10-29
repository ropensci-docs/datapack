# Clear the accessPolicy from the specified object

Clears the accessPolicy from the specified object by overwriting all
existing access rules set on the object with an empty set.

## Usage

``` r
clearAccessPolicy(x, ...)

# S4 method for class 'SystemMetadata'
clearAccessPolicy(x, ...)

# S4 method for class 'DataObject'
clearAccessPolicy(x, ...)

# S4 method for class 'DataPackage'
clearAccessPolicy(x, identifiers = list(), ...)
```

## Arguments

- x:

  the instance to clear access rules from.

- ...:

  (Additional parameters)

- identifiers:

  A list of `character` values containing package member identifiers
  that the access rule will be applied to.

## Value

The SystemMetadata object with the cleared access policy.

The DataObject with the cleared access policy.

The SystemMetadata object with the cleared access policy.

## See also

[`SystemMetadata-class`](https://docs.ropensci.org/datapack/reference/SystemMetadata-class.md)

[`DataObject-class`](https://docs.ropensci.org/datapack/reference/DataObject-class.md)

[`DataPackage-class`](https://docs.ropensci.org/datapack/reference/DataPackage-class.md)

## Examples

``` r
# Clear access policy for a SystemMetadata object.
sysmeta <- new("SystemMetadata")
sysmeta <- addAccessRule(sysmeta, "uid=smith,ou=Account,dc=example,dc=com", "write")
sysmeta <- clearAccessPolicy(sysmeta)
# Clear access policy for a DataObject
do <- new("DataObject", format="text/csv", filename=system.file("extdata/sample-data.csv", 
          package="datapack"))
do <- addAccessRule(do, "uid=smith,ou=Account,dc=example,dc=com", "write")
do <- clearAccessPolicy(do)
# Clear access policy for a DataPackage
dp <- new("DataPackage")
data <- charToRaw("1,2,3\n4,5,6\n")
obj <- new("DataObject", dataobj=data, format="text/csv")
dp <- addMember(dp, obj)
data2 <- charToRaw("7,8,9\n4,10,11\n")
obj2 <- new("DataObject", dataobj=data2, format="text/csv")
dp <- addMember(dp, obj2)

# Add the access rule to all package members
dp <- addAccessRule(dp, "uid=smith,ou=Account,dc=example,dc=com", 
    permission="write")
# Now clear the access policy for just the second object 
dp <- clearAccessPolicy(dp, getIdentifier(obj2))
```

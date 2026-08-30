# Add access rules to the specified object

Add one or more access rules to the access policy of the specified
object.

## Usage

``` r
addAccessRule(x, ...)

# S4 method for class 'SystemMetadata'
addAccessRule(x, y, ...)

# S4 method for class 'DataObject'
addAccessRule(x, y, ...)

# S4 method for class 'DataPackage'
addAccessRule(x, y, ...)
```

## Arguments

- x:

  The object instance to which to add the rules

- ...:

  Additional arguments

  - `permission`: The permission to be applied to subject if x is
    character (read, write, changePermission)

- y:

  The subject of the rule to be added, or a data frame of
  subject/permission tuples

## Value

The SystemMetadata object with the updated access policy.

The DataObject with the updated access policy

The DataPackage with updated DataObject access policies

## Details

If the `y` argument is specified as a character string containing a
`subject`, then an optional `permission` parameter must be specified,
that contains a character list specifying the permissions to add for
each `subject`.

Note that when `addAccessRule` is called with a \`DataPackage\`
argument, the additional parameter `identifiers` can be used:

- `identifiers`: A list of `character` values containing package member
  identifiers that the access rule will be applied to (all members is
  the default).

## See also

[`SystemMetadata-class`](https://docs.ropensci.org/datapack/reference/SystemMetadata-class.md)

[`DataObject-class`](https://docs.ropensci.org/datapack/reference/DataObject-class.md)

[`DataPackage-class`](https://docs.ropensci.org/datapack/reference/DataPackage-class.md)

## Examples

``` r
# Add an access rule to a SystemMetadata access policy.
# Parameter "y" can be character string containing the subject of the access rule:
sysmeta <- new("SystemMetadata")
sysmeta <- addAccessRule(sysmeta, "uid=smith,ou=Account,dc=example,dc=com", "write")
accessRules <- data.frame(subject=c("uid=smith,ou=Account,dc=example,dc=com", 
  "uid=slaughter,o=unaffiliated,dc=example,dc=org"), permission=c("write", "changePermission"))
sysmeta <- addAccessRule(sysmeta, accessRules)
# Alternatively, parameter "y" can be a data.frame containing one or more access rules:
sysmeta <- addAccessRule(sysmeta, "uid=smith,ou=Account,dc=example,dc=com", "write")
accessRules <- data.frame(subject=c("uid=smith,ou=Account,dc=example,dc=com", 
  "uid=slaughter,o=unaffiliated,dc=example,dc=org"), permission=c("write", "changePermission"))
sysmeta <- addAccessRule(sysmeta, accessRules)
# Add an access rule to a DataObject
data <- charToRaw("1,2,3\n4,5,6\n")
obj <- new("DataObject", id="1234", dataobj=data, format="text/csv")
obj <- addAccessRule(obj, "uid=smith,ou=Account,dc=example,dc=com", "write")
# Add an access rule to members of a DataPackage
# First create a sample DataPackage
dp <- new("DataPackage")
data <- charToRaw("1,2,3\n4,5,6\n")
obj <- new("DataObject", id="id1", dataobj=data, format="text/csv")
dp <- addMember(dp, obj)
data2 <- charToRaw("7,8,9\n4,10,11\n")
obj2 <- new("DataObject", id="id2", dataobj=data2, format="text/csv")
dp <- addMember(dp, obj2)
# Add access rule to all package members
dp <- addAccessRule(dp, "uid=smith,ou=Account,dc=example,dc=com", "write", getIdentifiers(dp))
```

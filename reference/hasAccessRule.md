# Determine if an access rules exists

Each SystemMetadata document may contain a set of (subject, permission)
tuples that represent the access rules for its associated object. This
method determines whether a particular access rule already exists within
the set.

If called for a DataObject, then the SystemMetadata for the DataObject
is checked.

If called for a DataPackage, then the SystemMetadata for DataObjects in
the DataPackage are checked.

## Usage

``` r
hasAccessRule(x, ...)

# S4 method for class 'SystemMetadata'
hasAccessRule(x, subject, permission)

# S4 method for class 'DataObject'
hasAccessRule(x, subject, permission)

# S4 method for class 'DataPackage'
hasAccessRule(x, subject, permission, identifiers = list(), ...)
```

## Arguments

- x:

  the object to check for presence of the access rule.

- ...:

  Additional arguments

- subject:

  of the rule to be checked

- permission:

  the permission to be checked

- identifiers:

  A list of `character` values containing package member identifiers for
  which the access rule will be checked.

## Value

A logical value: if TRUE the access rule was found, if FALSE it was not
found.

When called for SystemMetadata, boolean TRUE if the access rule exists
already, FALSE otherwise

When called for a DataObject, boolean TRUE if the access rule exists
already, FALSE otherwise

When called for a DataPackage, boolean TRUE if the access rule exists in
all specified package members already, FALSE otherwise

## See also

[`SystemMetadata-class`](https://docs.ropensci.org/datapack/reference/SystemMetadata-class.md)

[`DataObject-class`](https://docs.ropensci.org/datapack/reference/DataObject-class.md)

[`DataPackage-class`](https://docs.ropensci.org/datapack/reference/DataPackage-class.md)

## Examples

``` r
#
# Check access rules for a SystemMetadata object.
sysmeta <- new("SystemMetadata")
sysmeta <- addAccessRule(sysmeta, "uid=smith,ou=Account,dc=example,dc=com", "write")
accessRules <- data.frame(subject=c("uid=smith,ou=Account,dc=example,dc=com", 
  "uid=slaughter,o=unaffiliated,dc=example,dc=org"), permission=c("write", "changePermission"))
sysmeta <- addAccessRule(sysmeta, accessRules)
ruleExists <- hasAccessRule(sysmeta, subject="uid=smith,ou=Account,dc=example,dc=com", 
  permission="write")
#
# Check access rules for a DataObject
data <- system.file("extdata/sample-data.csv", package="datapack")
do <- new("DataObject", file=system.file("./extdata/sample-data.csv", package="datapack"), 
                                         format="text/csv")
do <- setPublicAccess(do)
isPublic <- hasAccessRule(do, "public", "read")
accessRules <- data.frame(subject=c("uid=smith,ou=Account,dc=example,dc=com", 
                          "uid=wiggens,o=unaffiliated,dc=example,dc=org"), 
                          permission=c("write", "changePermission"), 
                          stringsAsFactors=FALSE)
do <- addAccessRule(do, accessRules)
SmithHasWrite <- hasAccessRule(do, "uid=smith,ou=Account,dc=example,dc=com", "write")
#
# Check access rules for member DataObjects of a DataPackage.
# First create an example DataPackage
dp <- new("DataPackage")
data <- charToRaw("1,2,3\n4,5,6\n")
obj <- new("DataObject", id="id1", dataobj=data, format="text/csv")
dp <- addMember(dp, obj)
data2 <- charToRaw("7,8,9\n4,10,11\n")
obj2 <- new("DataObject", id="id2", dataobj=data2, format="text/csv")
dp <- addMember(dp, obj2)
# Add access rules to all package members
dp <- addAccessRule(dp, "uid=smith,ou=Account,dc=example,dc=com", "write")
dp <- addAccessRule(dp, "uid=smith,ou=Account,dc=example,dc=com", "changePermission")
hasWrite <- hasAccessRule(dp, "uid=smith,ou=Account,dc=example,dc=com", "write")
hasChange <- hasAccessRule(dp, "uid=smith,ou=Account,dc=example,dc=com", "changePermission")
```

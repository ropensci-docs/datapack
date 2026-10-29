# Remove an access rule from the specified object

Remove access rules from the access policy of the specified object.

## Usage

``` r
removeAccessRule(x, ...)

# S4 method for class 'SystemMetadata'
removeAccessRule(x, y, ...)

# S4 method for class 'DataObject'
removeAccessRule(x, y, ...)

# S4 method for class 'DataPackage'
removeAccessRule(x, y, permission = NA_character_, identifiers = list(), ...)
```

## Arguments

- x:

  The object instance to which to remove the rule

- ...:

  Additional arguments

  - `permission`: The permission to be remove to subject if x is
    character (read, write, changePermission)

- y:

  The subject of the rule to be removed, or a data.frame containing
  access rules.

- permission:

  The permission to remove, if parameter `x` is a character string
  containing a `subject`.

- identifiers:

  A list of `character` values containing package member identifiers
  that the access rule will be applied to (default is all package
  members).

## Value

The SystemMetadata object with the updated access policy.

The DataObject object with the updated access policy.

The Datapackage with members having updated access policies.

## See also

[`SystemMetadata-class`](https://docs.ropensci.org/datapack/reference/SystemMetadata-class.md)

[`DataObject-class`](https://docs.ropensci.org/datapack/reference/DataObject-class.md)

[`DataPackage-class`](https://docs.ropensci.org/datapack/reference/DataPackage-class.md)

## Examples

``` r
#
# Remove access rules from a SystemMetadata object.
# Parameter "y" can be character string containing the subject of the access rule:
sysmeta <- new("SystemMetadata")
sysmeta <- addAccessRule(sysmeta, "uid=smith,ou=Account,dc=example,dc=com", "write")
sysmeta <- addAccessRule(sysmeta, "uid=smith,ou=Account,dc=example,dc=com", "changePermission")
sysmeta <- removeAccessRule(sysmeta, "uid=smith,ou=Account,dc=example,dc=com", "changePermission")

# Alternatively, parameter "y" can be a data.frame containing one or more access rules:
# Add write, changePermission for uid=jones,...
sysmeta <- addAccessRule(sysmeta, "uid=jones,ou=Account,dc=example,dc=com", "write")
sysmeta <- addAccessRule(sysmeta, "uid=jones,ou=Account,dc=example,dc=com", "changePermission")
# Now take privs for uid=jones,... away
accessRules <- data.frame(subject=c("uid=jones,ou=Account,dc=example,dc=com", 
                                     "uid=jones,ou=Account,dc=example,dc=com"), 
                                     permission=c("write", "changePermission"))
sysmeta <- removeAccessRule(sysmeta, accessRules)
#
# Remove access rules form a DataObject.
library(datapack)
do <- new("DataObject", file=system.file("./extdata/sample-data.csv", package="datapack"), 
                        format="text/csv")
do <- setPublicAccess(do)
isPublic <- hasAccessRule(do, "public", "read")
accessRules <- data.frame(subject=c("uid=smith,ou=Account,dc=example,dc=com", 
                          "uid=wiggens,o=unaffiliated,dc=example,dc=org"), 
                          permission=c("write", "changePermission"), 
                          stringsAsFactors=FALSE)
do <- addAccessRule(do, accessRules)
do <- removeAccessRule(do, "uid=smith,ou=Account,dc=example,dc=com", "changePermission")
# hasAccessRule should return FALSE
hasWrite <- hasAccessRule(do, "smith", "write")

# Alternatively, parameter "y" can be a data.frame containing one or more access rules:
do <- addAccessRule(do, "uid=smith,ou=Account,dc=example,dc=com", "write")
accessRules <- data.frame(subject=c("uid=smith,ou=Account,dc=example,dc=com", 
  "uid=slaughter,o=unaffiliated,dc=example,dc=org"), 
  permission=c("write", "changePermission"))
sysmeta <- removeAccessRule(do, accessRules)
# 
# Remove access rules from a DataPackage.
dp <- new("DataPackage")
data <- charToRaw("1,2,3\n4,5,6\n")
obj <- new("DataObject", id="id1", dataobj=data, format="text/csv")
dp <- addMember(dp, obj)
data2 <- charToRaw("7,8,9\n4,10,11\n")
obj2 <- new("DataObject", id="id2", dataobj=data2, format="text/csv")
dp <- addMember(dp, obj2)
# Add access rule to all package members
dp <- addAccessRule(dp, "uid=smith,ou=Account,dc=example,dc=com", "write")
dp <- addAccessRule(dp, "uid=smith,ou=Account,dc=example,dc=com", "changePermission" )
# Now take 'changePermission' away for user 'uid=smith...', specifying parameter 'y' 
# as a character string containing a 'subject'.
dp <- removeAccessRule(dp, "uid=smith,ou=Account,dc=example,dc=com", "write")
dp <- removeAccessRule(dp, "uid=smith,ou=Account,dc=example,dc=com", "changePermission")

# Alternatively, parameter "y" can be a data.frame containing one or more access rules:
# Add write, changePermission for uid=jones,...
dp <- addAccessRule(dp, "uid=jones,ou=Account,dc=example,dc=com", "write")
dp <- addAccessRule(dp, "uid=jones,ou=Account,dc=example,dc=com", "changePermission")
# Now take privs for uid=jones,... away
accessRules <- data.frame(subject=c("uid=jones,ou=Account,dc=example,dc=com", 
                                     "uid=jones,ou=Account,dc=example,dc=com"), 
                                     permission=c("write", "changePermission"))
dp <- removeAccessRule(dp, accessRules)
```

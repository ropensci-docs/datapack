# Test whether the provided subject can read an object

Using the AccessPolicy, tests whether the subject has read permission
for the object. This method is meant work prior to submission to a
repository, and will show the permissions that would be enforced by the
repository on submission. Currently it only uses the AccessPolicy to
determine who can read (and not the rightsHolder field, which always can
read an object). If an object has been granted read access by the
special "public" subject, then all subjects have read access.

## Usage

``` r
canRead(x, ...)

# S4 method for class 'DataObject'
canRead(x, subject)
```

## Arguments

- x:

  DataObject

- ...:

  Additional arguments

- subject:

  : the subject name of the person/system to check for read permissions

## Value

boolean TRUE if the subject has read permission, or FALSE otherwise

## Details

The subject name used in both the AccessPolicy and in the `'subject'`
argument to this method is a string value, but is generally formatted as
an X.509 name formatted according to RFC 2253.

## See also

[`DataObject-class`](https://docs.ropensci.org/datapack/reference/DataObject-class.md)

## Examples

``` r
data <- charToRaw("1,2,3\n4,5,6\n")
obj <- new("DataObject", id="1234", dataobj=data, format="text/csv")
obj <- addAccessRule(obj, "smith", "read")
access <- canRead(obj, "smith")
```

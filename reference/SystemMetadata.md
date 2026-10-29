# Create DataONE SystemMetadata object

A class representing DataONE SystemMetadata, which is core information
about objects stored in a repository and needed to manage those objects
across systems. SystemMetadata contains basic identification, ownership,
access policy, replication policy, and related metadata.

If the \*sysmeta\* parameter is specified, then construct a new
SystemMetadata instance by using the fields from an XML representation
of the SystemMetadata.

## Usage

``` r
SystemMetadata(...)

# S4 method for class 'XMLInternalElementNode'
SystemMetadata(x, ...)
```

## Arguments

- ...:

  Additional arguments

- x:

  A value of type `"XMLInternalElementNode"`, containing the parsed XML
  element with SystemMetadata fields.

## See also

[`SystemMetadata-class`](https://docs.ropensci.org/datapack/reference/SystemMetadata-class.md)

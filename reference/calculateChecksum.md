# Calculate a checksum for the DataObject using the specified checksum algorithm

calculates a checksum

## Usage

``` r
calculateChecksum(x, ...)

# S4 method for class 'DataObject'
calculateChecksum(x, checksumAlgorithm = "SHA256", ...)
```

## Arguments

- x:

  A DataObject instance

- ...:

  Additional parameters (not yet used)

- checksumAlgorithm:

  a `character` value specifying the checksum algorithm to use (i.e
  "MD5" or "SHA1" or "SHA256")

## Value

The calculated checksum

## Note

this method is intended for internal package use only.

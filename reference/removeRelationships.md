# Remove relationships of objects in a DataPackage

Use this function to remove all or a subset of the relationships that
have previously been added in a data package.

## Usage

``` r
removeRelationships(x, ...)

# S4 method for class 'DataPackage'
removeRelationships(x, subjectID = NA_character_, predicate = NA_character_)
```

## Arguments

- x:

  A DataPackage object

- ...:

  (Additional parameters)

- subjectID:

  The identifier of the subject of the relationships to be removed

- predicate:

  The identifier of the predicate of the relationships to be removed

## Value

the updated DataPackage object

## Details

Remove a relationship of the form "subject -\> predicate -\> object", as
defined by the Resource Description Framework (RDF), i.e. an RDF triple.
If neither subjectID nor predicate are provided, then all relationships
are removed. If one or both are provided, they are used to select
matching triples to be removed. Note: This method updates the passed-in
DataPackage object.

## See also

[`DataPackage-class`](https://docs.ropensci.org/datapack/reference/DataPackage-class.md)

## Examples

``` r
dp <- new("DataPackage")
# Create a relationship
dp <- insertRelationship(dp, "/Users/smith/scripts/genFields.R",
    "https://knb.org/data_20030812.40.1",
    "http://www.w3.org/ns/prov#used")
# Create a relationshp with the subject as a blank node with an automatically assigned blank 
# node id
dp <- insertRelationship(dp, subjectID=NA_character_, objectIDs="thing6", 
    predicate="http://myns.org/wasThing")
# Create a relationshp with the subject as a blank node with a user assigned blank node id
dp <- insertRelationship(dp, subjectID="urn:uuid:bc9e160e-ca21-47d5-871b-4a4820fe4451", 
      objectIDs="thing7", predicate="http://myns.org/hadThing")
# Create multiple relationships with the same subject, predicate, but different objects
dp <- insertRelationship(dp, subjectID="https://myns.org/subject1", 
      objectIDs=c("thing4", "thing5"), predicate="http://myns.org/hadThing")
# Create multiple relationships with subject and object types specified
dp <- insertRelationship(dp, subjectID="orcid.org/0000-0002-2192-403X", 
    objectIDs="http://www.example.com/home", predicate="http://myns.org/hadHome",
                   subjectType="uri", objectType="literal")
nrow(getRelationships(dp)) 
#> [1] 6
dp <- removeRelationships(dp, predicate='http://myns.org/wasThing')
nrow(getRelationships(dp)) 
#> [1] 5
dp <- removeRelationships(dp, subjectID='orcid.org/0000-0002-2192-403X')
nrow(getRelationships(dp)) 
#> [1] 4
dp <- removeRelationships(dp, subjectID='https://myns.org/subject1', 
    predicate='http://myns.org/hadThing')
nrow(getRelationships(dp)) 
#> [1] 2
dp <- removeRelationships(dp)
nrow(getRelationships(dp)) 
#> [1] 0
```

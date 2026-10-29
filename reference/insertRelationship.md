# Record relationships of objects in a DataPackage

Record a relationship of the form "subject -\> predicate -\> object", as
defined by the Resource Description Framework (RDF), i.e. an RDF triple.

## Usage

``` r
insertRelationship(x, ...)

# S4 method for class 'DataPackage'
insertRelationship(
  x,
  subjectID,
  objectIDs,
  predicate = NA_character_,
  subjectType = NA_character_,
  objectTypes = NA_character_,
  dataTypeURIs = NA_character_
)
```

## Arguments

- x:

  A DataPackage object

- ...:

  (Additional parameters)

- subjectID:

  The identifier of the subject of the relationship

- objectIDs:

  A list of identifiers of the object of the relationships (a
  relationship is recorded for each objectID)

- predicate:

  The IRI of the predicate of the relationship

- subjectType:

  the type to assign the subject, values can be 'uri', 'blank'

- objectTypes:

  the types to assign the objects (cal be single value or list), each
  value can be 'uri', 'blank', or 'literal'

- dataTypeURIs:

  An RDF data type that specifies the type of the object

## Value

the updated DataPackage object

## Details

For use with DataONE, a best practice is to specify the subject and
predicate as DataONE persistent identifiers
(https://mule1.dataone.org/ArchitectureDocs-current/design/PIDs.html).
If the objects are not known to DataONE, then local identifiers can be
used, and these local identifiers may be promoted to DataONE PIDs when
the package is uploaded to a DataONE member node. The predicate is
typically an RDF property (as a IRI) from a schema supported by DataONE,
i.e. "http://www.w3.org/ns/prov#wasGeneratedBy" If multiple values are
specified for argument objectIDS, a relationship is created for each
value in the list "objectIDs". IF a value is not specified for
subjectType or objectType, then NA is assigned. Note that if these
relationships are fetched via the getRelationships() function, and
passed to the createFromTriples() function to initialize a ResourceMap
object, the underlying redland package will assign appropriate values
for subjects and objects. Note: This method updates the passed-in
DataPackage object.

## See also

[`DataPackage-class`](https://docs.ropensci.org/datapack/reference/DataPackage-class.md)

## Examples

``` r
dp <- new("DataPackage")
# Create a relationship
dp <- insertRelationship(dp, "/Users/smith/scripts/genFields.R",
    "https://knb.ecoinformatics.org/knb/d1/mn/v1/object/doi:1234/_030MXTI009R00_20030812.40.1",
    "http://www.w3.org/ns/prov#used")
# Create a relationshp with the subject as a blank node with an automatically assigned blank 
# node id
dp <- insertRelationship(dp, subjectID=NA_character_, objectIDs="thing6", 
    predicate="http://www.myns.org/wasThing")
# Create a relationshp with the subject as a blank node with a user assigned blank node id
dp <- insertRelationship(dp, subjectID="urn:uuid:bc9e160e-ca21-47d5-871b-4a4820fe4451", 
      objectIDs="thing7", predicate="http://www.myns.org/hadThing")
# Create multiple relationships with the same subject, predicate, but different objects
dp <- insertRelationship(dp, subjectID="urn:uuid:95055dc1-b2a0-4a00-bdc2-05c16d048ca2", 
      objectIDs=c("thing4", "thing5"), predicate="http://www.myns.org/hadThing")
# Create multiple relationships with subject and object types specified
dp <- insertRelationship(dp, subjectID="orcid.org/0000-0002-2192-403X", 
    objectIDs="http://www.example.com/home", predicate="http://www.example.com/hadHome",
                   subjectType="uri", objectType="literal")                
```

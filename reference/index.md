# Package index

## All functions

- [`DataObject-class`](https://docs.ropensci.org/datapack/reference/DataObject-class.md)
  : DataObject wraps raw data with system-level metadata
- [`initialize(`*`<DataObject>`*`)`](https://docs.ropensci.org/datapack/reference/DataObject-initialize.md)
  : Initialize a DataObject
- [`DataPackage-class`](https://docs.ropensci.org/datapack/reference/DataPackage-class.md)
  : A class representing a data package
- [`initialize(`*`<DataPackage>`*`)`](https://docs.ropensci.org/datapack/reference/DataPackage-initialize.md)
  : Initialize a DataPackage object
- [`ResourceMap-class`](https://docs.ropensci.org/datapack/reference/ResourceMap-class.md)
  : ResourceMap provides methods to create, serialize and deserialize an
  OAI ORE resource map
- [`initialize(`*`<ResourceMap>`*`)`](https://docs.ropensci.org/datapack/reference/ResourceMap-initialize.md)
  : Initialize a ResourceMap object
- [`SystemMetadata-class`](https://docs.ropensci.org/datapack/reference/SystemMetadata-class.md)
  : A DataONE SystemMetadata object containing basic identification,
  ownership, access policy, replication policy, and related metadata
- [`initialize(`*`<SystemMetadata>`*`)`](https://docs.ropensci.org/datapack/reference/SystemMetadata-initialize.md)
  : Initialize a DataONE SystemMetadata object with default values or
  values passed in to the constructor
- [`SystemMetadata()`](https://docs.ropensci.org/datapack/reference/SystemMetadata.md)
  : Create DataONE SystemMetadata object
- [`addAccessRule()`](https://docs.ropensci.org/datapack/reference/addAccessRule.md)
  : Add access rules to the specified object
- [`addData()`](https://docs.ropensci.org/datapack/reference/addData.md)
  : Add a DataObject to the DataPackage
- [`addMember()`](https://docs.ropensci.org/datapack/reference/addMember.md)
  : Add a DataObject to the DataPackage
- [`calculateChecksum()`](https://docs.ropensci.org/datapack/reference/calculateChecksum.md)
  : Calculate a checksum for the DataObject using the specified checksum
  algorithm
- [`canRead()`](https://docs.ropensci.org/datapack/reference/canRead.md)
  : Test whether the provided subject can read an object
- [`clearAccessPolicy()`](https://docs.ropensci.org/datapack/reference/clearAccessPolicy.md)
  : Clear the accessPolicy from the specified object
- [`containsId()`](https://docs.ropensci.org/datapack/reference/containsId.md)
  : Returns true if the specified object is a member of the package
- [`createFromTriples()`](https://docs.ropensci.org/datapack/reference/createFromTriples.md)
  : Populate a ResourceMap with RDF relationships from data.frame
- [`describeWorkflow()`](https://docs.ropensci.org/datapack/reference/describeWorkflow.md)
  : Add data derivation information to a DataPackage
- [`dmsg()`](https://docs.ropensci.org/datapack/reference/dmsg.md) :
  Print a debugging message to stderr
- [`freeResourceMap()`](https://docs.ropensci.org/datapack/reference/freeResourceMap.md)
  : Free memory used by a ResouceMap
- [`getData()`](https://docs.ropensci.org/datapack/reference/getData.md)
  : Get the data content of a specified data object
- [`getFormatId()`](https://docs.ropensci.org/datapack/reference/getFormatId.md)
  : Get the FormatId of the DataObject
- [`getIdentifier()`](https://docs.ropensci.org/datapack/reference/getIdentifier.md)
  : Get the Identifier of the DataObject
- [`getIdentifiers()`](https://docs.ropensci.org/datapack/reference/getIdentifiers.md)
  : Get the Identifiers of Package Members
- [`getMember()`](https://docs.ropensci.org/datapack/reference/getMember.md)
  : Return the Package Member by Identifier
- [`getRelationships()`](https://docs.ropensci.org/datapack/reference/getRelationships.md)
  : Retrieve relationships of package objects
- [`getSize()`](https://docs.ropensci.org/datapack/reference/getSize.md)
  : Get the Count of Objects in the Package
- [`getTriples()`](https://docs.ropensci.org/datapack/reference/getTriples.md)
  : Get the RDF relationships stored in the ResourceMap
- [`getValue()`](https://docs.ropensci.org/datapack/reference/getValue.md)
  : Get values for selected DataPackage members
- [`hasAccessRule()`](https://docs.ropensci.org/datapack/reference/hasAccessRule.md)
  : Determine if an access rules exists
- [`insertRelationship()`](https://docs.ropensci.org/datapack/reference/insertRelationship.md)
  : Record relationships of objects in a DataPackage
- [`parseRDF()`](https://docs.ropensci.org/datapack/reference/parseRDF.md)
  : Parse an RDF/XML resource map from a file
- [`parseSystemMetadata()`](https://docs.ropensci.org/datapack/reference/parseSystemMetadata.md)
  : Parse an external XML document and populate a SystemMetadata object
  with the parsed data
- [`plotRelationships()`](https://docs.ropensci.org/datapack/reference/plotRelationships.md)
  : Plot derivation relationships obtained from getRelationships
- [`recordDerivation()`](https://docs.ropensci.org/datapack/reference/recordDerivation.md)
  : Record derivation relationships between objects in a DataPackage
- [`removeAccessRule()`](https://docs.ropensci.org/datapack/reference/removeAccessRule.md)
  : Remove an access rule from the specified object
- [`removeMember()`](https://docs.ropensci.org/datapack/reference/removeMember.md)
  : Remove the Specified Member from the Package
- [`removeRelationships()`](https://docs.ropensci.org/datapack/reference/removeRelationships.md)
  : Remove relationships of objects in a DataPackage
- [`replaceMember()`](https://docs.ropensci.org/datapack/reference/replaceMember.md)
  : Replace the raw data or file associated with a DataObject
- [`selectMember()`](https://docs.ropensci.org/datapack/reference/selectMember.md)
  : Return identifiers for objects that match search criteria
- [`serializePackage()`](https://docs.ropensci.org/datapack/reference/serializePackage.md)
  : Create an OAI-ORE resource map from the package
- [`serializeRDF()`](https://docs.ropensci.org/datapack/reference/serializeRDF.md)
  : Serialize a ResouceMap
- [`serializeSystemMetadata()`](https://docs.ropensci.org/datapack/reference/serializeSystemMetadata.md)
  : Serialize a SystemMetadata object to an XML representation
- [`serializeToBagIt()`](https://docs.ropensci.org/datapack/reference/serializeToBagIt.md)
  : Serialize A DataPackage into a BagIt Archive File
- [`setPublicAccess()`](https://docs.ropensci.org/datapack/reference/setPublicAccess.md)
  : Add a Rule to the AccessPolicy to make the object publicly readable
- [`setValue()`](https://docs.ropensci.org/datapack/reference/setValue.md)
  : Set values for selected DataPackage members
- [`updateMetadata()`](https://docs.ropensci.org/datapack/reference/updateMetadata.md)
  : Update selected elements of the XML content of a DataObject in a
  DataPackage (aka package member)
- [`updateRelationships()`](https://docs.ropensci.org/datapack/reference/updateRelationships.md)
  : Update package relationships by replacing an old identifier with a
  new one
- [`updateXML()`](https://docs.ropensci.org/datapack/reference/updateXML.md)
  : Update selected elements of the XML content of a DataObject
- [`validate()`](https://docs.ropensci.org/datapack/reference/validate.md)
  : Validate a SystemMetadata object

# A class representing a data package

The DataPackage class provides methods for adding and extracting data
objects from a data package. The contents of a data package can include
arbitrary types of objects, including data files, program code,
visualizations and images, animations, and any other type of file. The
DataPackage class stores the individual members of the data package
along with key system-level metadata about each object, including its
size, checksum, identifier, and other key information needed to
effectively archive the members of the package. In addition, the
DataPackage class can include key provenance metadata about the
relationships among the objects in the data package. For example, the
data package can document that one object provides documentation for
another (`cito:documents`), and that one object was derived from another
(`prov:wasDerivedFrom`) by executing a program that used source data
(`prov:used`) to create a derived data object `{prov:wasGeneratedBy}`.
These relationships are integral to the data package, and can be
visualized by programs that understand the ProvONE provenance model (see
<https://purl.dataone.org/provone-v1-dev>).

The DataPackage class is an R representation of an underlying Open
Archives Initiative ORE model (Object Reuse and Exchange; see
<https://www.openarchives.org/ore/>), and follows the DataONE Data
Packaging model (see
<https://releases.dataone.org/online/api-documentation-v2.0.1/design/DataPackage.html>).

## Slots

- `relations`:

  A list containing provenance relationships of package objects

- `objects`:

  A list containing identifiers for objects in the DataPackage

- `sysmeta`:

  A SystemMetadata class instance describing the package

- `externalIds`:

  A list containing identifiers for objects associated with the
  DataPackage

- `resmapId`:

  A character string specifying the identifier for the package resource
  map. This is assigned after a package is uploaded or downloaded from a
  repository.

## Methods

- [`initialize`](https://docs.ropensci.org/datapack/reference/DataPackage-initialize.md):

  : Initialize a DataPackage object.

- [`addAccessRule`](https://docs.ropensci.org/datapack/reference/addAccessRule.md):

  : Add access rules to DataObjects in a DataPackage.

- [`addMember`](https://docs.ropensci.org/datapack/reference/addMember.md):

  : Add a DataObject to a DataPackage.

- [`clearAccessPolicy`](https://docs.ropensci.org/datapack/reference/clearAccessPolicy.md):

  : Clear access policies for DataObjects in a DataPackage.

- [`containsId`](https://docs.ropensci.org/datapack/reference/containsId.md):

  : Returns true if the specified object is a member of the data
  package.

- [`describeWorkflow`](https://docs.ropensci.org/datapack/reference/describeWorkflow.md):

  : Add data derivation information to a DataPackage.

- [`getData`](https://docs.ropensci.org/datapack/reference/getData.md):

  : Get the data content of a specified data object.

- [`getSize`](https://docs.ropensci.org/datapack/reference/getSize.md):

  : Get the Count of Objects in the DataPackage.

- [`getIdentifiers`](https://docs.ropensci.org/datapack/reference/getIdentifiers.md):

  : Get the Identifiers of DataPackage members.

- [`getMember`](https://docs.ropensci.org/datapack/reference/getMember.md):

  : Return the DataPackage Member by Identifier.

- [`getRelationships`](https://docs.ropensci.org/datapack/reference/getRelationships.md):

  : Retrieve relationships of data package objects.

- [`getValue`](https://docs.ropensci.org/datapack/reference/getValue.md):

  : Get values for selected DataPackage members.

- [`hasAccessRule`](https://docs.ropensci.org/datapack/reference/hasAccessRule.md):

  : Determine if access rules exists for DataObjects in a DataPackage.

- [`insertRelationship`](https://docs.ropensci.org/datapack/reference/insertRelationship.md):

  : Insert relationships between objects in a DataPackage.

- [`removeAccessRule`](https://docs.ropensci.org/datapack/reference/removeAccessRule.md):

  : Remove an access rule from DataObject in a DataPackage.

- [`removeMember`](https://docs.ropensci.org/datapack/reference/removeMember.md):

  : Remove the specified DataObject from a DataPackage.

- [`removeRelationships`](https://docs.ropensci.org/datapack/reference/removeRelationships.md):

  : Remove relationships of objects in a DataPackage.

- [`replaceMember`](https://docs.ropensci.org/datapack/reference/replaceMember.md):

  : Replace the raw data or file associated with a DataObject.

- [`selectMember`](https://docs.ropensci.org/datapack/reference/selectMember.md):

  : Select package members based on slot values.

- [`serializePackage`](https://docs.ropensci.org/datapack/reference/serializePackage.md):

  : Create an OAI-ORE resource map from the DataPackage.

- [`serializeToBagIt`](https://docs.ropensci.org/datapack/reference/serializeToBagIt.md):

  : Serialize A DataPackage into a BagIt Archive File.

- [`setPublicAccess`](https://docs.ropensci.org/datapack/reference/setPublicAccess.md):

  : Set the access policy to readable by anyone for DataObject in a
  DataPackage.

- [`setValue`](https://docs.ropensci.org/datapack/reference/setValue.md):

  : Set values for selected DataPackage members

- `show`:

  : Print DataPackage information in a formatted view.

- [`updateMetadata`](https://docs.ropensci.org/datapack/reference/updateMetadata.md):

  : Update selected elements of the XML content of a DataObject in a
  DataPackage

- [`updateRelationships`](https://docs.ropensci.org/datapack/reference/updateRelationships.md):

  : Update package relationships by replacing an old identifier with a
  new one.

## See also

[`datapack`](https://docs.ropensci.org/datapack/reference/datapack.md)

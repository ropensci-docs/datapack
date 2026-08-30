# A DataONE SystemMetadata object containing basic identification, ownership, access policy, replication policy, and related metadata

A class representing DataONE SystemMetadata, which is core information
about objects stored in a repository and needed to manage those objects
across systems. SystemMetadata contains basic identification, ownership,
access policy, replication policy, and related metadata.

## Slots

- `serialVersion`:

  value of type `"numeric"`, the current version of this system
  metadata; only update the current version

- `identifier`:

  value of type `"character"`, the identifier of the object that this
  system metadata describes.

- `replicationAllowed`:

  value of type `"logical"`, replication policy allows replicas.

- `numberReplicas`:

  value of type `"numeric"`, for number of supported replicas.

- `preferredNodes`:

  value of type `"list"`, of preferred member nodes.

- `blockedNodes`:

  value of type `"list"`, of blocked member nodes.

- `formatId`:

  value of type `"character"`, the DataONE object format for the object.

- `size`:

  value of type `"numeric"`, the size of the object in bytes.

- `checksum`:

  value of type `"character"`, the checksum for the object using the
  designated checksum algorithm.

- `checksumAlgorithm`:

  value of type `"character"`, the name of the hash function used to
  generate a checksum, from the DataONE controlled list.

- `submitter`:

  value of type `"character"`, the Distinguished Name or identifier of
  the person submitting the object.

- `rightsHolder`:

  value of type `"character"`, the Distinguished Name or identifier of
  the person who holds access rights to the object.

- `accessPolicy`:

  value of type `"data.frame"`, a list of access rules as (subject,
  permission) tuples to be applied to the object.

- `obsoletes`:

  value of type `"character"`, the identifier of an object which this
  object replaces.

- `obsoletedBy`:

  value of type `"character"`, the identifier of an object that replaces
  this object.

- `archived`:

  value of type `"logical"`, a boolean flag indicating whether the
  object has been archived and thus hidden.

- `dateUploaded`:

  value of type `"character"`, the date on which the object was uploaded
  to a member node.

- `dateSysMetadataModified`:

  value of type `"character"`, the last date on which this system
  metadata was modified.

- `originMemberNode`:

  value of type `"character"`, the node identifier of the node on which
  the object was originally registered.

- `authoritativeMemberNode`:

  value of type `"character"`, the node identifier of the node which
  currently is authoritative for the object.

- `seriesId`:

  value of type `"character"`, a unique Unicode string that identifies
  an object revision chain. A seriesId will resolve to the latest
  version of an object.

- `mediaType`:

  value of type `"character"`, the IANA Media Type (aka MIME-Type) of
  the object, e.g. "text/csv".

- `fileName`:

  value of type `"character"`, the name of the file to create when this
  object is downloaded from DataONE.

- `mediaTypeProperty`:

  value of type a `"list"` of `"character"`, IANA Media Type properties
  for the `"mediaType"` argument

## Methods

- [`initialize`](https://docs.ropensci.org/datapack/reference/SystemMetadata-initialize.md):

  : Initialize a DataONE SystemMetadata object with default values or
  values passed in to the constructor object

- [`SystemMetadata`](https://docs.ropensci.org/datapack/reference/SystemMetadata.md):

  : Create a SystemMetadata object, with all fields set to the value
  found in an XML document

- [`parseSystemMetadata`](https://docs.ropensci.org/datapack/reference/parseSystemMetadata.md):

  : Parse an external XML document and populate a SystemMetadata object
  with the parsed data

- [`serializeSystemMetadata`](https://docs.ropensci.org/datapack/reference/serializeSystemMetadata.md):

  : Get the Count of Objects in the Package

- [`validate`](https://docs.ropensci.org/datapack/reference/validate.md):

  : Validate a SystemMetadata object

- [`addAccessRule`](https://docs.ropensci.org/datapack/reference/addAccessRule.md):

  : Add access rules to an object such as system metadata

- [`hasAccessRule`](https://docs.ropensci.org/datapack/reference/hasAccessRule.md):

  : Determine if a particular access rules exists within SystemMetadata.

- [`clearAccessPolicy`](https://docs.ropensci.org/datapack/reference/clearAccessPolicy.md):

  : Clear the accessPolicy from the specified object.

## See also

[`datapack`](https://docs.ropensci.org/datapack/reference/datapack.md)

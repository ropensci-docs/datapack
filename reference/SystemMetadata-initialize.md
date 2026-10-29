# Initialize a DataONE SystemMetadata object with default values or values passed in to the constructor

Initialize a SystemMetadata object by providing default values for core
information needed to manage objects across repository systems.
SystemMetadata contains basic identification, ownership, access policy,
replication policy, and related metadata.

## Usage

``` r
# S4 method for class 'SystemMetadata'
initialize(
  .Object,
  identifier = NA_character_,
  formatId = NA_character_,
  size = NA_real_,
  checksum = NA_character_,
  checksumAlgorithm = "SHA-256",
  submitter = NA_character_,
  rightsHolder = NA_character_,
  accessPolicy = data.frame(subject = character(), permission = character()),
  replicationAllowed = TRUE,
  numberReplicas = 3,
  obsoletes = NA_character_,
  obsoletedBy = NA_character_,
  archived = FALSE,
  dateUploaded = NA_character_,
  dateSysMetadataModified = NA_character_,
  originMemberNode = NA_character_,
  authoritativeMemberNode = NA_character_,
  preferredNodes = list(),
  blockedNodes = list(),
  seriesId = NA_character_,
  mediaType = NA_character_,
  fileName = NA_character_,
  mediaTypeProperty = list()
)
```

## Arguments

- .Object:

  The object being initialized

- identifier:

  value of type `"character"`, the identifier of the object that this
  system metadata describes.

- formatId:

  value of type `"character"`, the DataONE object format for the object.

- size:

  value of type `"numeric"`, the size of the object in bytes.

- checksum:

  value of type `"character"`, the checksum for the object using the
  designated checksum algorithm.

- checksumAlgorithm:

  value of type `"character"`, the name of the hash function used to
  generate a checksum, from the DataONE controlled list.

- submitter:

  value of type `"character"`, the Distinguished Name or identifier of
  the person submitting the object.

- rightsHolder:

  value of type `"character"`, the Distinguished Name or identifier of
  the person who holds access rights to the object.

- accessPolicy:

  value of type `"data.frame"` containing (subject, permission) tuples
  to constitute the access authorization rules.

- replicationAllowed:

  value of type `"logical"`, for replication policy allows replicas.

- numberReplicas:

  value of type `"numeric"`, for number of supported replicas.

- obsoletes:

  value of type `"character"`, the identifier of an object which this
  object replaces.

- obsoletedBy:

  value of type `"character"`, the identifier of an object that replaces
  this object.

- archived:

  value of type `"logical"`, a boolean flag indicating whether the
  object has been archived and thus hidden.

- dateUploaded:

  value of type `"character"`, the date on which the object was uploaded
  to a member node.

- dateSysMetadataModified:

  value of type `"character"`, the last date on which this system
  metadata was modified.

- originMemberNode:

  value of type `"character"`, the node identifier of the node on which
  the object was originally registered.

- authoritativeMemberNode:

  value of type `"character"`, the node identifier of the node which
  currently is authoritative for the object.

- preferredNodes:

  list of `"character"`, each of which is the node identifier for a node
  to which a replica should be sent.

- blockedNodes:

  list of `"character"`, each of which is the node identifier for a node
  blocked from housing replicas.

- seriesId:

  value of type `"character"`, a unique Unicode string that identifies
  an object revision chain. A seriesId will resolve to the latest
  version of an object.

- mediaType:

  value of type `"character"`, the IANA Media Type (aka MIME-Type) of
  the object, e.g. "text/csv".

- fileName:

  value of type `"character"`, the name of the file to create when this
  object is downloaded from DataONE.

- mediaTypeProperty:

  value of type a `"list"` of `"character"`, IANA Media Type properties
  for the `"mediaType"` argument

## Value

the SystemMetadata instance representing an object

## See also

<https://releases.dataone.org/online/api-documentation-v2.0/apis/Types.html>

[`SystemMetadata-class`](https://docs.ropensci.org/datapack/reference/SystemMetadata-class.md)

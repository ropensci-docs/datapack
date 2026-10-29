# Changelog

## datapack 1.4.2

CRAN release: 2025-10-10

BUGS

- Fix documentation errors due to API changes
  ([\#139](https://github.com/ropensci/datapack/issues/139))

## datapack 1.4.1

CRAN release: 2022-06-10

BUGS

- Remove LazyData from DESCRIPTION
  ([\#132](https://github.com/ropensci/datapack/issues/132))
- Remove dependency on hash package
  ([\#133](https://github.com/ropensci/datapack/issues/133))
- Replace instances of `if (class(...))` with `inherits(...)`
  ([\#136](https://github.com/ropensci/datapack/issues/136))

NEW FEATURES

- Refactor BagIt serialization to match new specification
  ([\#109](https://github.com/ropensci/datapack/issues/109))

## datapack 1.4.0

CRAN release: 2020-11-04

BUGS

- Handle dc:creator in resource map properly
  ([\#116](https://github.com/ropensci/datapack/issues/116))

NEW FEATURES

- Use SHA-256 as the default hash algorithm
  ([\#117](https://github.com/ropensci/datapack/issues/117))
- Added ‘checksumAlgorithm’ argument to DataObject initialization method
  ([\#117](https://github.com/ropensci/datapack/issues/117))
- Update tests for compatibility with testthat 3e
  ([\#125](https://github.com/ropensci/datapack/issues/125))
- Added ‘targetPath’ argument to DataObject to set ‘prov:atLocation’ for
  an object ([\#109](https://github.com/ropensci/datapack/issues/109))

## datapack 1.3.2

CRAN release: 2019-10-15

BUGS

- Ensure that a ‘dc:creator’ element is always present
  ([\#93](https://github.com/ropensci/datapack/issues/93))
- Ensure that the resource map dcterms:modified time is always
  present/updated.
  ([\#93](https://github.com/ropensci/datapack/issues/93))
- Ensure that a DataPackage is marked as updated after addAccessRule,
  setPublicAccess, clearAccessPolicy methods called
  ([\#92](https://github.com/ropensci/datapack/issues/92)).
- Remove dependency on redland::getNextResult
  ([\#110](https://github.com/ropensci/datapack/issues/110))

NEW FEATURES \* Added function removeRelationships() which can remove
all or specified relationships from a DataPackage
([\#99](https://github.com/ropensci/datapack/issues/99))

## datapack 1.3.1

CRAN release: 2017-08-29

BUGS

- fixed bug in updateMetadata() that would cause package relationships
  for the metadata object to be lost.

## datapack 1.3.0

CRAN release: 2017-08-03

NEW FEATURES

- Added support for DataPackage download, edit, upload workflow.
  ([\#85](https://github.com/ropensci/datapack/issues/85))

- Added new method parseRDF() to parses an RDF/XML resource map from a
  file. ([\#85](https://github.com/ropensci/datapack/issues/85))

- Added new method removeMember() which removes a member from a Package.
  ([\#85](https://github.com/ropensci/datapack/issues/85))

- Added new method replaceMember() which replaces the raw data or file
  associated with a DataObject.
  ([\#85](https://github.com/ropensci/datapack/issues/85))

- Added new method selectMember(0) which selects package members based
  on slot values.
  ([\#85](https://github.com/ropensci/datapack/issues/85))

- Added new method updateRelationships() which updates package
  relationships by replacing an old identifier with a new one.
  ([\#85](https://github.com/ropensci/datapack/issues/85))

- Added new method updateMetadata() to update XML content of a
  DataOBject in a DataPackage.
  ([\#85](https://github.com/ropensci/datapack/issues/85))

- Added new method getValue() which gets values for selected DataPackage
  member slots. ([\#85](https://github.com/ropensci/datapack/issues/85))

- Added new method setValue(0) which sets values for selected
  DataPackage member slots.
  ([\#85](https://github.com/ropensci/datapack/issues/85))

- Added new method removeAccessRule() to SystemMetadata, DataObject,
  DataPackage classes.
  ([\#78](https://github.com/ropensci/datapack/issues/78))

- Added new method hasAccessRule() to DataObject, DataPackage classes.
  ([\#78](https://github.com/ropensci/datapack/issues/78))

- Added new method clearAccessPolicy() DataObject, DataPackage classes.
  ([\#78](https://github.com/ropensci/datapack/issues/78))

- Added new method addAccessRule() to DataPackage. class
  ([\#85](https://github.com/ropensci/datapack/issues/85))

- Added new method setPublicAccess() to DataPackage. class
  ([\#85](https://github.com/ropensci/datapack/issues/85))

- Access policies can now be modified for DataPackage, DataObject.
  ([\#78](https://github.com/ropensci/datapack/issues/78))

- Resource map identifiers now include metadata object identifier.
  ([\#82](https://github.com/ropensci/datapack/issues/82))

BUGS

- fixed bug where resource maps had invalid XML names for blank node
  identifiers. ([\#79](https://github.com/ropensci/datapack/issues/79))

- fixed bug where resource maps did not include creator or modification
  time. ([\#80](https://github.com/ropensci/datapack/issues/80))

DEPRECATED

- deprecated function addData(), renamed to addMember().

## datapack 1.2.0

CRAN release: 2017-04-07

BUGS

- Fixed bug where replicationAllowed was not set correctly when parsing
  if it is false
  ([\#61](https://github.com/ropensci/datapack/issues/61))

- Fixed bug where numberReplicas was not set correctly when parsing
  ([\#63](https://github.com/ropensci/datapack/issues/63))

- Fixed bug where the `mediaType` argument to DataObject
  [`initialize()`](https://rdrr.io/r/methods/new.html) was not being
  handled correctly and resulted in an invalid system metadata object to
  be serialized from the DataObject.
  ([\#67](https://github.com/ropensci/datapack/issues/67))

- Added argument ‘mediaTypeProperty’ to DataObject
  [`initialize()`](https://rdrr.io/r/methods/new.html) which was needed
  to fully support ‘mediaType’.
  ([\#67](https://github.com/ropensci/datapack/issues/67))

NEW FEATURES

- Added new function to reset access policies
  [`clearAccessPolicy()`](https://docs.ropensci.org/datapack/reference/clearAccessPolicy.md)
  ([\#56](https://github.com/ropensci/datapack/issues/56))

- Added new function
  [`describeWorkflow()`](https://docs.ropensci.org/datapack/reference/describeWorkflow.md)
  to add run provenance relationships to a DataPackage
  ([\#64](https://github.com/ropensci/datapack/issues/64))

- Added ‘Show’ methods for DataObject and DataPackage classes.
  ([\#71](https://github.com/ropensci/datapack/issues/71),
  [\#73](https://github.com/ropensci/datapack/issues/73))

DEPRECATED

- The method `recordDerivation` is deprecated in this release and may be
  marked as Defunct and removed in a future release
  ([\#68](https://github.com/ropensci/datapack/issues/68))

## datapack 1.1.0

This \# datapack was not released publicly.

## datapack 1.0.1

CRAN release: 2016-05-20

BUGS

- Fixed bug where Roxygen example for serializePackage() was writing to
  the “/tmp” directory

- Serializing system metadata to XML with serializeSystemMetadata() now
  gathers all elements together for a so that the subject does not
  appear under multiple elements.

## datapack 1.0.0

CRAN release: 2016-03-25

NEW FEATURES

- Initial \# datapack (see help topic for ‘datapack’, e.g. “?datapack”)

- Provides an API for building and serializing packages of data and
  associated metadata.

- The package name has been changed from ‘datapackage’ to ‘datapack’

NEW S4 CLASSES

- Class DataPackage for building and serializing data packages.

- Class SystemMetadata and DataObject for representing a member of a
  data package.

- Class ResourceMap for building and serializing a Resource Description
  Framework representation of a data package.

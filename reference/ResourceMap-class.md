# ResourceMap provides methods to create, serialize and deserialize an OAI ORE resource map

The Open Archives Initiative Object Reuse and Exchange (OAI-ORE) defines
standards for the description and exchange of aggregations of web
resources, such as a DataPackage. A Resource Map describes the objects
in a DataPackage and the relationships between these objects.

## Slots

- `relations`:

  value of type `"data.frame"`, containing RDF triples representing the
  relationship between package objects

- `world`:

  a Redland RDF World object

- `storage`:

  a Redland RDF Storage object

- `model`:

  a Redland RDF Model object

- `id`:

  a unique identifier for a ResourceMap instance

## Methods

- [`initialize`](https://docs.ropensci.org/datapack/reference/ResourceMap-initialize.md):

  : Initialize a ResourceMap object.

- [`createFromTriples`](https://docs.ropensci.org/datapack/reference/createFromTriples.md):

  : Populate a ResourceMap with RDF relationships from data.frame.

- [`getTriples`](https://docs.ropensci.org/datapack/reference/getTriples.md):

  : Get the RDF relationships stored in the ResourceMap.

- [`parseRDF`](https://docs.ropensci.org/datapack/reference/parseRDF.md):

  : Parse an RDF/XML resource map from a file.

- [`serializeRDF`](https://docs.ropensci.org/datapack/reference/serializeRDF.md):

  : Write the ResourceMap relationships to a file.

## See also

[`datapack`](https://docs.ropensci.org/datapack/reference/datapack.md)

## Examples

``` r
dp <- new("DataPackage")
dp <- insertRelationship(dp, "/Users/smith/scripts/genFields.R",
    "http://www.w3.org/ns/prov#used",
    "https://knb.ecoinformatics.org/knb/d1/mn/v1/object/doi:1234/_030MXTI009R00_20030812.40.1")
relations <- getRelationships(dp)
resMap <- new("ResourceMap")
resMap <- createFromTriples(resMap, relations, getIdentifiers(dp))
if (FALSE) { # \dontrun{
tf <- tempfile(fileext=".rdf")
serializeRDF(resMap, file=tf)
} # }
```

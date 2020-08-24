# OGC API - Tiles

This GitHub repository contains the new revision of the [OGC](http://opengeospatial.org)'s Web Map Tile Service standards for requesting tiles (both vector tiles and maps tiles; and eventually coverage tiles) of geospatial information on the web. It is a complete rewrite of previous versions, focusing on a simple RESTful core specified as reusable [OpenAPI](http://openapis.org) components.

This is the CURRENT working version of this initiative (Old version work was one of the  engineering reports in Testbed-15 see the public version in http://docs.opengeospatial.org/per/19-069.html; or the GitHub version:  https://github.com/opengeospatial/T-15-D014-WMTS_draft_specification; if you are not a member or observer in Testbed15 you will get a 404)

IMPORTANT: Many examples of OpenAPI documents that are used as inspiration and test of this work is here:
https://app.swaggerhub.com/apis/UAB-CREAF

The OGC API - Maps and the OGC API - Tiles are related and should be considered complementary. Visit the [Quick guide](QuickGuide/README.md)

## Standards

[OGC API standards](https://ogcapi.ogc.org) define modular API building blocks to spatially enable Web APIs
in a consistent way. [OpenAPI](http://openapis.org) is used to define the reusable
API building blocks.

After a while getting familiar and playing with the OpenAPI definition files (explained just below in the "Examples section"), we have finally started to write the standard. We have decided an aggressive path to modularization having two separate core standards, one for tiles and another for maps that can be combined as needed. Several extension for tiles and maps will emerge in the process.

While under development, the standards are written using AsciiDoc using many files that might be difficult to trace. Please see the compiled standard document as it is easier to read here: https://htmlpreview.github.io/?https://github.com/opengeospatial/OGC-API-Tiles/blob/master/core/standard/OAPI_Tiles.html

### OGC API - Tiles - Part 1: Core
The definition of OGC API - Tiles - Part 1: Core is the immediate next step. The Standards Working Group (SWG) agreed on the structure shown below.

-  _TileSet_ - Defines how to specify a `tileset` resource, which contains information on how to formulate a tile request.
  - Included information indicates the associated TileMatrixSet, optional TileMatrixSet limits (TileMatrix, Row, and Column)
- _TileSets_ - Defines how to specify a `tilesets` resource describing multiple `tileset` resources
- _DatasetTileSets_ - Defines how to get a tile resource from the dataset (or datasets) represented by the services. It will tell the path to get a tile resource.
  - OGC API Common - Part 1 (dataset, /map resource at the root): 
- _GeoDataResourceSelection_ - together with 3, geodata= query parameter: This is identical to the GeoDataResourceSelection conformance class of OGC API - Common and if done adequately.
- _GeoDataResourceMap_ - Specifies how to define the a link to a tile resource containing a representation of this geospatial data resource (path).
  - OGC API Common - Part 2 / OGC Feature - Part 1 (collection connection, /maps resource after {collectionID}): 
- _TileMap_ - Defines how to specify a link to a tile resource containing a representation of a map.

### Extensions
The following exensions may be considered for future development either as additional requirements or separate OGC standards:
* _Custom TileMatrixSets_  - Definitions of custom TileMatrixSets ([Requirements Class .adoc](extensions/tmxs/standard/clause_7_tile_tms.adoc), [HTML Preview](https://htmlpreview.github.io/?https://github.com/opengeospatial/OGC-API-Tiles/blob/master/extensions/tmxs/standard/OAPI_Tiles.html))
* _Info_ - Feature information ([Requirements Class .adoc](extensions/info/standard/clause_7_tile_info.adoc), [HTML Preview](https://htmlpreview.github.io/?https://github.com/opengeospatial/OGC-API-Tiles/blob/master/extensions/info/standard/OAPI_Tiles.html))
* _Multi-tile_ - Retrieve a ZIP with many tiles ([Requirements Class .adoc](extensions/multitile/standard/clause_7_tile_collections.adoc), [HTML Preview](https://htmlpreview.github.io/?https://github.com/opengeospatial/OGC-API-Tiles/blob/master/extensions/multitile/standard/OAPI_Tiles.html))

## Using the standard

Those who want to just see the endpoints and responses can explore generic
OpenAPI definitions in this folder (please paste one of them in the Swagger Editor):

- _API Definition Explorer_ - Generic OpenAPI definitions that may be explored within [SwaggerHub](https://app.swaggerhub.com/) may be found [here](./openapi)
- _Reference Implementations_ - Several reference server and client implementations of the draft specification may be found [here](./implementations.adoc)
- _Quick Start Guide_ - A quick start guide demonstrating several basic interaction patterns with an API Tiles endpoint may be found [here](./QuickGuide)


**WARNING: This section needs to be updated.**


## Examples
An example OpenAPI definition, that describes hypothetical WebAPI conformant to this standard to expose vector tiles is available here: https://app.swaggerhub.com/apis/UAB-CREAF/ogc-api-tiles-opf-xmp-vt-more-1-collection/1.0.0
A resolved (almost without dependencies with other files) YAML file, synchronized with the previous working document, is available in this github repository at: https://github.com/opengeospatial/OGC-API-tiles/tree/master/openapi/swaggerhub/tiles.yaml

An example OpenAPI definition, that describes hypothetical WebAPI conformant to this standard to expose map tiles is available here: https://app.swaggerhub.com/apis/UAB-CREAF/ogc-api-map-tiles-opf-xmp-mt-more-1-collection/1.0.0
A resolved (almost without dependencies with other files) YAML file, synchronized with the previous working document, is available in this github repository at: https://github.com/opengeospatial/OGC-API-tiles/tree/master/openapi/swaggerhub/map-tiles.yaml

Until mid July 2019, the work was focused on providing OpenAPI services description examples and domains (libraries). Now we believe this work is finalized, but each time that we take a look we still find gaps, mistakes and things that can be improved.
We expect that during the effort of extracting the knowledge accumulated (hopefully) in these files to create the standard, we will keep fixing, perfecting and evolving things.

IMPORTANT NOTE: We are now using the Swagger HUB again and should be considered the "gold copy". The Swagger account is:
* [Domain documents](https://app.swaggerhub.com/search?owner=UAB-CREAF&type=DOMAIN)
* [API example documents](https://app.swaggerhub.com/search?owner=UAB-CREAF&type=API)

The material in the [standards folder](standard/openapi) takes precedence to the text of the standard and the Swagger HUB takes precedence to the material in GitHub. The [standards folder](standard/openapi) examples are intended to be identical to the Swagger HUB ones except for the path names. To go from  Swagger HUB to GitHub do the following substitutions:
* Replace "https://api.swaggerhub.com/domains/UAB-CREAF/ogc-api-" by "https://raw.githubusercontent.com/opengeospatial/OGC-API-Map-Tiles/master/standard/openapi/ogc-api-"
* Replace "/1.0.0#/" by ".yaml#/"

The files in the [standards folder](standard/openapi) are structured in several parts that can be combined together.

![Diagram of the examples and domains](standard/images/diagram-xmp.png)

A [OGC API maps and tiles OPF FULL example in Swagger](https://api.swaggerhub.com/domains/UAB-CREAF/ogc-api-map-tiles-opf-xmp-full/1.0.0) or in [GitHub](standard/openapi/ogc-api-map-tiles-opf-xmp-full.yaml) that contains full example of server with some features and coverages that are served as maps and/or tiles.

The latter is normally too long to be analyzed. The following are easier to understand.

Examples:
* A [OGC API OPF example for vector tiles in Swagger](https://api.swaggerhub.com/domains/UAB-CREAF/ogc-api-tiles-opf-xmp-vt-more-1-collection/1.0.0) or in [GitHub](standard/openapi/ogc-api-tiles-opf-xmp-vt-more-1-collection.yaml) that describes a service that can serve only tiled features (vector tiles) of one or more collections.
* A [OGC API OPF example for tiled map in Swagger](https://api.swaggerhub.com/domains/UAB-CREAF/ogc-api-map-tiles-opf-xmp-mt-more-1-collection/1.0.0) or in [GitHub](standard/openapi/ogc-api-map-tiles-opf-xmp-mt-more-1-collection.yaml) that describes a service that can serve only map (raster) tiles of one or more collections.
* A [OGC API OPF example for maps in Swagger](standard/openapi/ogc-api-maps-opf-xmp-ore-1-collection.yaml) that describes a service that can serve only maps of one or more collections.
* A [OGC API OPF example for tiled coverages in Swagger](https://api.swaggerhub.com/domains/UAB-CREAF/ogc-api-tiles-opf-xmp-vt-more-1-collection/1.0.0) or in [GitHub](standard/openapi/ogc-api-tiles-opf-xmp-vt-more-1-collection.yaml) that describes a service that can serve tiled coverages of one or more collections. This example was not initially needed by the sponsors but is motivated by the elevation map in a GeoPackage example.

Libraries:
* A [OGC API common DOMAIN document in Swagger](https://api.swaggerhub.com/domains/UAB-CREAF/ogc-api-common/1.0.0) or in [GitHub](standard/openapi/ogc-api-common.yaml). It contains fragments that can be reference in api document instances or other domain document. It could become part of a future OGC API common standard additional material.
* A [OGC API maps DOMAIN document in Swagger](https://api.swaggerhub.com/domains/UAB-CREAF/ogc-api-maps/1.0.0) or in [GitHub](standard/openapi/ogc-api-maps.yaml). It contains fragments that can be reference in api document instances or other domain document. It could become part of a future OGC API maps standard additional material.
* A [OGC API maps and tiles DOMAIN document in Swagger](https://api.swaggerhub.com/domains/UAB-CREAF/ogc-api-map-tiles/1.0.0) or in [GitHub](standard/openapi/ogc-api-map-tiles.yaml). It contains fragments that can be reference in api document instances or other domain document. It will be included by OGC API maps standard and tiles standard.
* A [OGC API tiles DOMAIN document in Swagger](https://api.swaggerhub.com/domains/UAB-CREAF/ogc-api-tiles/1.0.0) or in [GitHub](standard/openapi/ogc-api-tiles.yaml). It contains fragments that can be reference in api document instances or other domain document. It could become part of a future OGC API tiles standard additional material.

## Communication

Join the WMS mailing list

Most work on the specification takes place in [GitHub issues](https://github.com/opengeospatial/OGC-API-Map-Tiles/issues),
so browse there to get a good idea of what is happening, as well as past decisions.

## Contributing

The contributor understands that any contributions, if accepted by the OGC Membership (and eventually the ISO/TC 211), shall be incorporated into OGC and ISO/TC 211 Web Map Service and Web Map Tile Service standards documents and that all copyright and intellectual property shall be vested to the OGC.

The WMS Standards Working Group (SWG) is the group at OGC responsible for the stewardship of the standard, but is working to do as much work in public as possible.

* [Open issues](https://github.com/opengeospatial/OGC-API-Map-Tiles/issues)
* [Copy of License Language](https://raw.githubusercontent.com/opengeospatial/OGC-API-Map-Tiles/master/LICENSE)

Pull Requests from contributors are welcomed. However, please note that by sending a Pull Request or Commit to this GitHub repository, you are agreeing to the terms in the Observer Agreement https://portal.ogc.org/files/?artifact_id=92169

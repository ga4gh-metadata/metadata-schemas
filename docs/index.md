---
title: GA4GH Metadata Standards
---

## Welcome to the GA4GH Metadata Repository

The *GA4GH-Metadata* repository contains definitions for structures, relations and attributes of biological (individuals, biosamples ...) and procedural (experiments, analyses ...) data objects, to facilitate the exchange of data and federation of analyses in the context of the Global Alliance for Genommics and Health ([GA4GH](http://ga4gh.org)).

The metadata specifications presented here were developed by the GA4GH's Metadata Task Team, as part of the (now frozen) general [GA4GH data schema](https://github.com/ga4gh/ga4gh-schemas/).

* [Metadata Specifications on Github](https://github.com/ga4gh-metadata/ga4gh-metadata/)
* [Metadata Wiki](https://github.com/ga4gh-metadata/metadata-schemas/wiki)
    * provides additional documentation, to facilitate understanding how the current schema emerged
    * links to archival docs, e.g. GA4GH Metadata Task Team discussions


## Metadata API

### Goals and Scope

* standardized use of common attributes/values
* a schema of how objects relate to each other

The metadata API provides information on the primary data objects
available via the GA4GH API, and facilities to organize primary data
objects.

#### General Data Formats & Standards
* [Documentation](formats.html)

#### Shared Objects
* [Documentation](shared.html)
* [download *shared metadata elements* specification](https://raw.githubusercontent.com/ga4gh-metadata/ga4gh-metadata/master/schemas/shared.proto)

#### Assay-Metadata
* [Documentation](assaymetadata.html)
* [download *assay metadata* specification](https://raw.githubusercontent.com/ga4gh-metadata/ga4gh-metadata/master/schemas/assaymetadata.proto)

#### Bio-Metadata
* [Documentation](biometadata.html)
* [download *bio metadata* specification](https://raw.githubusercontent.com/ga4gh-metadata/ga4gh-metadata/master/schemas/biometadata.proto)



---

<!--

{% include_relative formats.md %}


[Bio-Metadata (full path)](https://github.com/ga4gh-metadata/ga4gh-metadata/blob/master/schema/bio_metadata.proto)
-->

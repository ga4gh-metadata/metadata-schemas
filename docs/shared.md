---
title: Common - Dataset and Low Level Objects
---

### OntologyTerm

Examples:

```json
{
  "term_id" : "ncit:C3059",
  "term_label" : "Glioma"
},

```
```json
{
  "identifier" : "pubmed:18506748",
  "relation" : "denotes"
},

```

### ExternalIdentifier

Example:

```json

```

### Dataset

All GA4GH data objects are part of a *dataset*. A dataset is a
data-provider-specified collection of related data of multiple types.
Logically, it's akin to a folder, where it's up to the provider what
goes into the folder. Individual data objects are linked by
`datasetId` fields to [Dataset objects](../schemas/shared.proto).

Since the grouping of content in a dataset is determined by the data
provider, users should not make semantic assumptions about that data.
Subsets of the data in a dataset can be selected for analysis using
other metadata or attributes.

#### Dataset Use Cases

For server implementors, datasets are a useful level of granularity
for implementing administrative features such as access control
(e.g. Data set X is public; data set Y is only available to lab Z's
collaborators) and billing (e.g. the costs of hosting Dataset Y should
be charged to lab Z).

For data curators, datasets are 'the simplest thing that could
possibly work' for grouping data (e.g. Dataset X has all the reads,
variants, and expression levels for a particular research project;
Dataset Y has all the work product from a particular grant).

For data accessors, datasets are a simple way to scope exploration and
analysis (e.g. "Are there any supporting examples in 1000genomes?";
"What is the distribution of that result in the data from our project?").


### GeoLocation

A GeoLocation object provides information about a geographic position related to a record. Examples could be:
- an address, e.g. of a lab performing an analysis
- provenance of an individual, obfuscated to a larger order administrative entity (Suffolk, U.K.)
- a lat/long/alt position where an environmental sample was collected

The geographic point object uses the default units from the [DCMI point scheme](http://dublincore.org/documents/dcmi-point/) and avoids optional representation in non-standard units.

```json
"geo_data" : {
  "geo_json" : {
    "type" : "Point",
    "coordinates" : [
      8.55,
      47.37
    ]
  },
  "geo_label" : "Zurich, Switzerland, Europe",
  "info" : {
    "city" : "Zurich",
    "continent" : "Europe",
    "country" : "Switzerland"
  },
  "geo_precision" : "city"
},
```

---
title: Common - Dataset and Low Level Objects
---

### OntologyTerm

... tbd. ...

### ExternalIdentifier

... tbd. ...

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

**Dataset Use Cases**

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

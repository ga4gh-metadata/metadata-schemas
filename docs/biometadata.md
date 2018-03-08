---
title: BioMetadata: Biosample & Individual
---

## BioMetadata: *Biosample* Object

### Biosample in the GA4GH Schema

The majority of use cases of GA4GH
schema compatible resources will serve to facilitate the retrieval of *molecular
features* (DNA sequence variations, gene expression, protein variants) measured
by performing *experimental* (whole genome sequencing, expression arrays, mass
spectroscopy) in conjunction with *bioinformatics* procedures, applied to a
preparation of target molecules (e.g. DNA, RNA) which has been extracted from a
*biological sample* (e.g. tissue biopsy, single cell from FACS,
environmental sample).

In the GA4GH schema, a *Biosample* represents the main "biological
item" against which molecular variants are referenced.

### Biosample attributes

Attribute | Notes
--- | ---
*id* | <ul><li>the Biosample's id</li><li>unique in the context of the server</li><li>used for referencing this Biosample</li></ul>
*name* | <ul><li>a human readable object label/identifier</li><li>not to be used for referencing</li></ul>
*description* | additional, unstructured information about this Biosample
*bio_characteristics* | contains lists of phenotypes, diseases and other information associated with this Biosample, in the form of BioCharacteristic objects
*individualId* | the *id* of the *Individual* this Biosample was derived from
*created* | the time the record was created, in ISO8601
*updated* | the time the record was updated, in ISO8601
*attributes* | additional, structured information


## BioMetadata: *Individual* Object

### Individual in the GA4GH Schema

An *Individual* is a GA4GH data object representing a biological instance
(most commonly a human being or other individual organism) on whose *Biosamples*
experimental analyses are performed.

In the case of metagenome analyses (i.e. when the biosample consists of
material like patient derived sputum, analyzed for its microbial content), the
"species" context would still be the host; identified guest species would
be described in analysis results.

### Individual attributes

Attribute | Notes
--- | ---
*id* | <ul><li>the Individual's id</li><li>unique in the context of the server</li><li>used for referencing this Individual</li></ul>
*name* | <ul><li>a human readable object label/identifier</li><li>not to be used for referencing</li></ul>
*description* | additional, unstructured information about this Individual
*bio_characteristics* | contains lists of phenotypes, diseases and other information associated with this Individual, in the form of BioCharacteristic objects
*species*  | OntologyTerm representing the species (NCBITaxon:9606)
*sex*  | OntologyTerm for the genetic sex of this individual.
*created* | the time the record was created, in ISO8601
*updated* | the time the record was updated, in ISO8601
*attributes* | additional, structured information


## BioMetadata: *BioCharacteristic* Object

### BioCharacteristic in the GA4GH Schema

A BioCharacteristic is an object, defining a single phenotype or diagnosis
through the use of a free text description and a representation by one or
more "ontologyTerms" objects as well as zero or more "negatedOntologyTerms".
An additional "scope" attribute allows to limit queries e.g. to "disease" type
objects.

Example use:

```json
"bio_characteristics" : [
  {
    "description" : "Diffuse Intrinsic Pontine Glioma",
    "ontology_terms" : [
      {
        "term_label" : "Glioma",
        "term_id" : "ncit:C3059"
      },
      {
        "term_label" : "Glioma NOS",
        "term_id" : "pgx:icdom:9380_3"
      },
      {
        "term_label" : "Brain NOS",
        "term_id" : "pgx:icdot:C71.9"
      }
    ],
    "negated_ontology_terms" : [ ]
  }
],
```

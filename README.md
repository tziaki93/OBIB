# Ontology for Biobanking (OBIB)

> **Version:** v3 (under review)

OBIB is the OWL ontology that formalizes the concepts defined in the [MIABIS](https://github.com/BBMRI-ERIC/miabis) (Minimum Information About Biobank data Sharing) standard, using BFO (Basic Formal Ontology) and standard OBO Foundry design patterns.

Version 2.4 is actively in development to support the implementation requirements of MIABIS v3. Updates to core classes, supporting classes, and object properties are currently underway.

* **Sample type**
* **Aggregated Sample Type**

| Ontology       | MIABIS Version | Classes | Properties | Individuals | Axioms |
|----------------|-----------------|---------|------------|--------------|--------|
| OMIABIS (2013) | MIABIS v1       | 249     | 64         | 34           | —      |
| OBIB (2016)    | MIABIS v2       | 516     | 83         | —            | 1172   |
| OBIB (2023)    | MIABIS v2       | 1804    | 93         | 226          | 17807  |
| OBIB (2026)    | MIABIS v2.1     | 1844    | 108        | 226          | 18117  |
| OBIB (2026)    | MIABIS v2.2     | 1868    | 206        | 226          | 18346  |
| OBIB (2026)    | MIABIS v2.3     | 1926    | 203        | 267          | 18893  |
| OBIB (2026)    | MIABIS v3       |     |         |           |   |

---

**Note on documentation:** the accompanying documentation still describes the previous version (v2.3). It will be updated once the v3 corrections below are complete. Until then, this README and the changelog are the authoritative reference for what has changed.

## Changelog from v2.3

### Donor biological sex
Replaced a set of restrictions that forced "donor biological sex" into an incorrect AND relationship (requiring every instance to be both male and female at once) with a proper OR restriction over PATO male/female, and separated biological sex from gender identity, which had previously been conflated.

### Event modelling
Corrected the "age at event" property chain to use the same age-unit pattern already established elsewhere in the ontology, and fixed the direction of the "is about" relation (the age datum is about the donor, not about the event itself). Event remains modeled as a BFO process, consistent with MIABIS's own definition of Event as "a generic template that represents something that happens in a given place and time."

### Biobank
Reused the existing "biobank organization" class as the correct OWL counterpart to the MIABIS v3 Biobank concept, rather than altering the identity of the persistent "biobank" class. Extended it to also cover biobanks that are part of a legal entity without separate legal personhood, using BFO "part of".

### Collection and Research Resource
Removed restrictions that forced these classes into a single BFO category (object aggregate for Collection, information content entity for Research Resource) and removed metadata restrictions that were incorrectly attached directly to them. Replaced both with a "has member" relation to either "collection of specimens" or "dataset", so that a Collection or Research Resource can correctly hold material specimens, informational datasets, or both.

### Sample-type mapping corrections
Several individual sample-type classes had OWL errors where multiple SubClassOf assertions were combined as AND instead of OR, or where the class was attached to the wrong parent:

- **Stem cell / iPS cell**: split into two separate classes, "stem cell specimen" (derives from a general stem cell) and "iPS cell specimen" (an induced pluripotent stem cell line, narrowed under Immortalised cell line specimen).
- **Liquid Biopsy**: reparented from blood specimen to bodily fluid specimen, reflecting that a liquid biopsy can be drawn from blood or other bodily fluids.
- **Urine Sediment**: reparented from urine specimen to processed specimen, with an explicit "derives from" relation to urine specimen, reflecting that sediment is the material obtained after processing urine, not urine itself.
- **Embryo or fetal tissue**: replaced a single SubClassOf restriction to "embryo" with a proper union of the two existing classes, "embryo" or "fetal tissue".
- **Tissue (fresh frozen or fixed)** and **Tissue (frozen or FFPE)**: added the missing "specimen" and "tissue" parent classes. These classes previously had only an anonymous union restriction and no named parent, so they appeared disconnected from the rest of the hierarchy.

## Repository

This repository exists to provide clear traceability and tracked changes for the ontology's development. Commits should include descriptive messages, and this changelog will be updated to reflect the differences between versions as work progresses.

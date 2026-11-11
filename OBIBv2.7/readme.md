# Ontology for Biobanking (OBIB)

**Version:** 2.7
**Status:** Competency Question Verification (FORTH)

OBIB is an OWL ontology that formalizes the concepts defined in the [MIABIS](https://github.com/BBMRI-ERIC/miabis) (Minimum Information About Biobank data Sharing) standard, using BFO (Basic Formal Ontology) and standard OBO Foundry design patterns.

The verification with the queries provided by the project collaborators has been completed. Each query was run as a SPARQL query on example data, and the results showed which queries the ontology answers fully, which partially and which cannot be answered with the current MIABIS v3 scope.

This version adds a set of competency questions that cover the entities and attributes introduced or changed in MIABIS v3, such as Network, Research Resource, sample source, Use & Access conditions, biobank capabilities and quality management standards. New example instances were added to the ontology to support these questions, and each competency question is answered by a SPARQL query on these instances.

This version is intended for testing and verification purposes and remains under review. The example instances will be removed before the final release.

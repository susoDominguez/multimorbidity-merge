# CG-RDF

## Forked Use Case 

The following files have been modified from their original source, which was applied as an use case for the published paper

```
V. Zamborlini, R. Hoekstra, M. Silveira, C. Pruski, A. Teije, Generalizing the Detection of Internal and External Interactions in Clinical Guidelines, in: Proceedings of the 9th International Conference on Health Informatics (HEALTHINF2016), Rome, Italy.

```

## Schema Folder

This folder contains the extended TMR schema to define subguidelines, that is, sets of recommendations from the same CIG which must be suggested as a whole for a particular case.

## Instance Folder

This folder contains the three machine-interpretable clinical guidelines from the original use case, along with a CIG merging them three, and data sets for care actions, causation beliefs and transitions/situations/properties. They have been reintroduced using the CIG interaction service embedded with the extended TMR ontology

```
https://github.kcl.ac.uk/k1214757/TMRWebX

```

## FHIR response folder
This folder has been added to the original source to contain a JSON version of each CIG as returned by the CIG interaction service.
Additionally, it provides a pair of JSON files conforming to FHIR standards. One as a dummy CDS hook file for a patient diagnosed with Diabetes (CIG DB), Hypertension (CIG HT) and Osteoarthritis (CIG OA)

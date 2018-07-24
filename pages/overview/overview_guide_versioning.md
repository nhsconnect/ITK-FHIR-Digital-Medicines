---
title: Guide Versioning
keywords: development, versioning
tags: [development]
sidebar: overview_sidebar
permalink: overview_guide_versioning.html
summary: An overview of this implementation guide is versioned.
---

## 1. Product Versioning ##

### 1.1.0 Semantic Versioning ###

Versioning of each technical “Product” or asset (i.e. API, Design Principle(s), Data Library) is managed using [Semantic Versioning 2.0.0](http://semver.org/).

Given a version number MAJOR.MINOR.PATCH, increment the:

- MAJOR version when you make incompatible API changes,
- MINOR version when you add functionality in a backwards-compatible manner, and
- PATCH version when you make backwards-compatible bug fixes.

Additional labels for pre-release and build metadata are available as extensions to the MAJOR.MINOR.PATCH format.

A pre-release version MAY be denoted by appending a hyphen (refer to [Semantic Versioning - Item 9](http://semver.org/#spec-item-9){:target="_blank"})

For examples: 1.0.0-alpha.1 is a valid pre-release version.

### 1.2.0 Pre-release Labels ###

When FHIR API implementation guides are published, they MUST have an associated maturity label. These labels are based on the GDS development process stages and MUST conform to one of the labels defined in the [FHIR-PUB-04: FHIR API Maturity](https://nhsconnect.github.io/fhir-policy/publication.html) ‘Publication Requirements’ section of the [NHS FHIR Policy](https://nhsconnect.github.io/fhir-policy/index.html).

The labels documented in the GDS development process stages are: 

 - **Experimental**: Early development/POC version of an API for early sight during discovery
 - **Alpha**: Initial test APIs, likely to change substantially, or be discontinued as the project develops
 - **Beta**: APIs that are still under active development and subject to change, but that are likely to progress into a live API
 - **Release Candidate**: APIs that are largely complete, unlikely to change substantially, but still need further testing before becoming live
 - **Live**: Release live APIs
 - **Discontinued**: APIs which have been discontinued and should not be used for new development.

### 1.3.0  GDS Stage - Experimental ###

This implementation guide is in currently in the "Experimental" stage. This means it is undergoing significant changes and will have regular releases. 



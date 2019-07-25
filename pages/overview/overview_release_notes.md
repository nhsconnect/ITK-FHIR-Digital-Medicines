---
title: Release Notes
keywords: development, versioning
tags: [development]
sidebar: overview_sidebar
permalink: overview_release_notes.html
summary: Summary release notes of the versions released in Digital Medicines Implementation Guide
---

{% include warning.html content="This **temporary** site is provided to assist with the development of the Digital Medicines Specification and is being updated regularly. It is advised not to develop against these specifications until a formal announcement has been made." %}

## Alpha 1.1.2 ##
A patch release to correct SNOMED codes for Consent and Eligibility Criteria from temp codes to actual provided values:

New codes added:
61871000000107 | Eligibility for treatment
61861000000100 | Consent

Profiles changed: 
Consent and Eligibility Criteria Section
https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-DM-Immunization-Composition-1

Consent Section
https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-DM-EmergencySupply-Composition-1

## Alpha 1.1.1 ##
- All gist linked examples have now been embedded into the spec as inline coding
- All gist linked Message Definition examples embedded into the spec as inline coding
- "Assure" menu section has been removed
- "Deploy" menu section has been removed
- New section "Distribution list" added to the specification
- Immunizations references renamed to Vaccinations to match PRSB headings
- Referrer details renamed to Referral Details in all sections to match PRSB headings
- Following sections updated and checked to match the PRSB headings following review (Click on the links to see a change comparison)
	- [Allergies and Adverse Reactions Section](images/overview/releasenotes/Digital Medicines Allergies and Adverse Reactions Section Example.html)
	- [Appliances](images/overview/releasenotes/Digital Medicines Attendance Details Section Example.html)
	- Distribution list (NEW SECTION)
	- [GP Practice](images/overview/releasenotes/Digital Medicines GP Practice Section Example.html)
	- [Medications](images/overview/releasenotes/Digital Medicines Emergency Supply Medications Section Example.html)
	- [Patient demographics](images/overview/releasenotes/Digital Medicines Patient Demographics Section Example.html)
	- [Plan and requested actions](images/overview/releasenotes/Digital Medicines Emergency Supply Plan and Requested Actions Section Example.html)
	- [Referral details](images/overview/releasenotes/Digital Medicines Referrer Details Section Example.html)
	- [Vaccinations](images/overview/releasenotes/Digital Medicines Immunization Section Example.html)

## Alpha 1.0.0 ##
Alpha release supporting the following for Immunizations and Emergency Medication Supply:

- FHIR profiles developed using the [FHIR Release STU3](https://www.hl7.org/fhir/STU3/index.html) specification
- [SNOMED CT](https://digital.nhs.uk/snomed-ct) coding support where applicable

  
## Experimental 1.0.0 ##
This draft version includes implementation guidance to support the development of the Digital Medicines specification in preparation for an Alpha release, supporting the following for Immunizations and Emergency Medication Supply:

- FHIR profiles developed using the [FHIR Release STU3](https://www.hl7.org/fhir/STU3/index.html) specification
- [SNOMED CT](https://digital.nhs.uk/snomed-ct) coding support where applicable

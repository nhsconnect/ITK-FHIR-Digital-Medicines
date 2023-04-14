---
title: Release Notes
keywords: development, versioning
tags: [development]
sidebar: overview_sidebar
permalink: overview_release_notes.html
summary: Summary release notes of the versions released in Digital Medicines Implementation Guide
---

## 1.2.9-Private-Beta ##
- MedicationDispense.daysSupply mandated for MinorIllness (if medication is provided)
- Remove batch number from medication
- Updated [Digital Medicines Headings](explore_headings.html) page to align with [PRSB headings](https://prsb2.vercel.app/page/cpcs-minor-illness?hsCtaTracking=1d5866f8-00cc-4380-b593-f012a7c4fffc%7C316e3499-8b4c-4868-a7d9-abddbf63ba3b) for Minor Illness
- Dose directions description (dosage instruction) mandated
- Contact with professionals heading page updated to include reference to CareConnect-ITK-Encounter-1
- Minor Illness Consultation Composition.type changed to 1577041000000109, Community Pharmacist Consultation Service for minor illness
- Further details given for [Medication Dispense List](build_medication_dispense_list.html) and [Medications and Medical Devices Section](explore_medication_mirc.html)
- New MIRC MESH Id added
- Corrections for section heading names and associated codes

- Attendance details (1077881000000105) -> Contacts with professionals (https://fhir.nhs.uk/CodeSystem/SectionCode\|contacts-with-professionals)
- Clinical narrative (1077901000000108) -> Clinical Summary (887181000000106)
- Consent (61861000000100) -> Legal information (886961000000102)

- Medications - guidance amended that only AMP / AMPP dm+d codes shall be sent
- AllergyIntolerance - guidance amended to correct ECL statements for causative agent.  
- AllergyIntolerance - Remove Evidence data item (not required).
- AllergyIntolerance - clarification on reaction.severity
- Condition - remove Evidence data item (not required)
- Procedure - remove Category data item (not required)
- Procedure - remove anesthetic Issues data item (not required)
- Added page "Build Minor Illness Referral Consultation Document Coded Data" from Design and Constructing Clinical Coded Structures Overview

## 1.2.7-Private-Beta ## 

- Minor illness specification: added Safeguarding; Examination findings and Signpost details sections
- Updated Minor illness example
- Change Minor Illness medication and medical devices section to be same as Emergency Supply
- Minor Illness presenting complaint or issues section, changed to use a SNOMED code & removed Symptom Duration
- Minor Illness - remove Referrer details section

## 1.2.6-Private-Beta ## 

- [Referral details](explore_referral_details.html) - Clarification that Referral Details are details on onward referral(s). Change to intro text; change to "Referral to" sub heading description; change to example from self-referral to a GP referral.
- [Attendance details](explore_contacts_professionals.html) - Change to example to include a Service example for  Emergancy Supply. Removal of prefixes (e.g. "Name:") from example. Tidy up example - for example changed some &lt;p&gt; tags for &lt;br/&gt;. Added Emergecy Supply to "Consultation method". Added Consultation method to example. Change Location to Community pharmacy.
- [GP Practice](explore_gp_practice.html) - Removed label ("ODS Organization Code:") from Practice identifier in example. Added GP Practice name and address in example
- [Patient demographics](explore_patient_demographics.html) - removed prefixes (Name: etc.) from the example. Improved formatting of Address by changing &lt;p&gt; to &lt;br/&gt;. Name now appears in one line.
- Change to menu structure - Moved [Observations](explore-observations.html) from Common Headings to Minor Illness Referral Consultation 

## 1.2.5-Private-Beta ## 

- The Pharmacy Digital Minor Illness Referral Service care communication has been renamed to **Minor Illness Referral Consultation (MIRC)**.
- New heading [Referrer Details](explore_referrer_details_mirc.html) has been added to the Minor Illness Referral Consultation section.
- Existing headings for Minor Illness Referral Consultation have been updated - these are [Clinical Summary](explore_clinical_narrative_mirc.html), [Medications and medical devices](explore_medication_mirc.html) and [Presenting complaint or issues](explore_presenting_complaint_mirc.html).  
- Minor Illness Referral Consultation (MIRC) guidance has been added to Common Headings pages for [Attendance details](explore_contacts_professionals.html), [Consent](explore_legal_information.html) and [Patient demographics](explore_patient_demographics.html).
- New Common Heading page added for [Observations](explore_observations.html), which includes details on how to form coded entry data for the Minor Illness Referral Consultation document.
- New Example Scenario added [Jack Smith Minor Illness Referral Consultation (MIRC)](engage_jack_smith_mirc.html). 

<b>Note:</b> At the time of publication, FHIR profile development to support the Minor Illness Referral Consultation (MIRC) care communication has not been completed. This development is planned for the future and will include:

* A new MessageDefinition FHIR profile for the Minor Illness Referral Consultation (MIRC) care communication, with StructureDefinition URL 'https://fhir.nhs.uk/STU3/MessageDefinition/ITK-DM-MIRC-MessageDefinition-1'.
* A new code and display 'ITK013D - ITK Digital Medicine Minor Illness Referral Consultation' to be added to the [CodeSystem ITK-MessageEvent-2](https://fhir.nhs.uk/STU3/CodeSystem/ITK-MessageEvent-2).
* Changes to [CareConnect-ITK-DM-DMIRS-Composition](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-DM-DMIRS-Composition-1):
	* Add new Composition.section for 'Referrer Details' with SNOMED CT representation '1052891000000108 - Referrer details'
	* Add new Composition.section for 'Observations' with SNOMED CT representation '11102421000000108 - Observations'  
	* Correction to Composition.section.title for 'presentingComplaintOrIssues', from 'Presentin complaint or issues' to 'Presenting complaint or issues'. 

Corrections to existing example scenarios - SNOMED CT representations in the following examples have been updated:

- [Jack Dawkins Vaccinations COVID Vaccination Given](engage_jack_dawkins_imms.html)
- [Hettie Winters Vaccinations COVID Vaccination Not Given](engage_hettie_winters_imms.html)

## 1.2.4-Private-Beta ##
- [Vaccinations](explore_vaccinations.html): ‘Vaccine procedure’ updated to align with the Version 1.2 update to the ValueSet [CareConnect-VaccinationProcedure-1](https://fhir.hl7.org.uk/STU3/ValueSet/CareConnect-VaccinationProcedure-1)
- New example scenarios:  The example scenarios are:
	- [for a COVID vaccination that is given](engage_jack_dawkins_imms.html)
	- [for a COVID vaccination that is not given](engage_hettie_winters_imms.html)

<b>Note:</b> These examples are for demonstrating FHIR representation only. They do not imply business requirements in terms of the ITK Wrapper population, or clinical requirements for SNOMED CT representations.

## 1.2.3-Private-Beta ##
- Added DaysSupply as required and changed Indication to optional within [Medications and Medical devices](explore_medication_ES.html) headings
- Added DaysSupply as required to [Medication Dispense List](build_medication_dispense_list.html#medicationdispense)
- Updated [examples](build_medication_dispense_list.html#medication-dispense-list-examples) on Medication Dispense List
- Added [MedicationDispense.quantity](build_medication_dispense_list.html#quantity) coded data requirements
- Clarification on use of [Medication.form](build_medication_dispense_list.html#medicationform)
- Amendments to the [Emergency Supply example scenario](engage_william_smith_meds.html), including supply of both insulin and needles, and amendements to the ITK Header example
- Added requirement to reference an CareConnect-ITK-Header-Organization-1 resource within the `<sender>` element of the [ITK Header](explore.html#itk3-messaging-requirements)
- Added relevant [MESH WorkflowIDs](explore_transport.html#mesh-workflowids)

## 1.2.2-Private-Beta ##
Examples - Banners added clarifying that examples are illustrative, and have not been formally clinically assured
Examples aligned with specification to correctly show Composition.section.text content:
- Location of event - FHIR Target changed to additional freetext added to Composition.section.text
- Serialisation code - optional field. Removed from examples.
- Vaccine procedure - examples changed to 955691000000108 \| Seasonal influenza vaccination given by pharmacist
-  Vaccine product - examples changed to 35727111000001109 \| Influvac sub-unit Tetra vaccine suspension for injection 0.5ml pre-filled syringes (Mylan)

[diff vs. 1.2.1-Private-Beta](https://github.com/nhsconnect/ITK-FHIR-Digital-Medicines/compare/b2809dcc8c433e28c7a36bcdc99164d5dca5085c..4fca9e8deda21053e033429b18b97843105e8df8)

## 1.2.1-Private-Beta ##
Replaced SNOMED code:<br/>
SNOMED CT Concept ID : 820261000000101<br/>
Synonym: Controlled drug dispensing record<br/><br/>
With new SNOMED code:<br/>
SNOMED CT Concept ID :1218611000000102<br/>
Synonym : Urgent supply of prescription items by community pharmacy

## 1.2.0-Private-Beta ##
Added four new areas to the Specification:
- New Medicine Service
- Medication Review
- Digital Minor Illness Refferal Service (DMIRS)
- Appliance Use Review

This produces four new compositions profiles, Messaging Architecture and Message Headings
* Message Definitions section has been removed<br/>
* All examples have the ```<xml>``` tag which was shown at the beginning and the end, now put into a comments wrapper
```
<!--<xml>-->
Text
<!--</xml>-->
```

* Added new section Design & Build > Document Replacement<br/>
* Added new section Messaging Architecture>Document Profiles>Digital Medicines Document Profiles has been created and now encapsulates all information
* Added new section Message Headings > Overview of Headings has been created and now encapsulates all information
* A "FHIR Target" column has been added to every Message Heading page showing the FHIR mapping
* An in-correct SNOMED code was used in the previous release.<br/>
886721000000107 Referral details<br/>
replaces<br/>
1052891000000108 Referrer details
* All <font color="red">Optional</font> elements have been highlighted in red within the Message Headings to avoid confusion when implementing

## 1.1.3-Alpha ##
The two scenario examples contained errors which have now been fixed and run against the Test Harness. They should now correctly validate and help suppliers with more guidance.

## 1.1.2-Alpha ##
A patch release to correct SNOMED codes for Consent and Eligibility Criteria from temp codes to actual provided values:

New codes added:
61871000000107 | Eligibility for treatment
886961000000102 | Consent

Profiles changed: 
Consent and Eligibility Criteria Section
https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-DM-Immunization-Composition-1

Consent Section
https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-DM-EmergencySupply-Composition-1

## 1.1.1-Alpha ##
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

## 1.1.0-Alpha ##
Alpha release supporting the following for Immunizations and Emergency Medication Supply:

- FHIR profiles developed using the [FHIR Release STU3](https://www.hl7.org/fhir/STU3/index.html) specification
- [SNOMED CT](https://digital.nhs.uk/snomed-ct) coding support where applicable

  
## 1.0.0-Experimental ##
This draft version includes implementation guidance to support the development of the Digital Medicines specification in preparation for an Alpha release, supporting the following for Immunizations and Emergency Medication Supply:

- FHIR profiles developed using the [FHIR Release STU3](https://www.hl7.org/fhir/STU3/index.html) specification
- [SNOMED CT](https://digital.nhs.uk/snomed-ct) coding support where applicable

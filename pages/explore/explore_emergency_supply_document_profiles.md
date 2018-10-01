---
title: Emergency Supply Document Profiles 
keywords:  documents
tags: [fhir,messaging,documents]
sidebar: foundations_sidebar
permalink: explore_emergency_supply_document_profiles.html
summary: "ITK3 Digital Medicine Emergency Medication Supply FHIR Document profile"
---


## ITK3 Digital Medicine Emergency Medication Supply FHIR Document Bundle ##

The document bundle is a collection of FHIR Resource Profiles combined to support the Digital Medicine Emergency Medication Supply FHIR Document.

The Bundle consists of the following FHIR Resource Profiles.

- **[ITK-Document-Bundle-1](https://fhir.nhs.uk/STU3/StructureDefinition/ITK-Document-Bundle-1)** - An NHS Digital Bundle Profile to represent a container to collect a combination of the ITK3 FHIR Document resources.
- **[CareConnect-ITK-DM-EmergencySupply-Composition-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-DM-EmergencySupply-Composition-1)** - An NHS Digital Profile derived from the CareConnect Profile for Digital Medicine Emergency Medication Supply FHIR Documents. This Profile is aligned to the PRSB standard for headings and subheadings for clinical documents.
- **[CareConnect-ITK-Encounter-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Encounter-1)** - A NHS Digital Profile derived from the CareConnect Encounter Profile. The Encounter Resource represents an Encounter between a care professional and the patient (or patient's record).
- **[CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)** - 	A CareConnect Profile for Organization. The Organization Resource represents the organisation that employs the healthcare professional.
- **[CareConnect-ITK-Condition-List-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Condition-List-1)** - An NHS Digital Profile derived from the CareConnect List Profile for recording a snapshot of the list of Conditions for the patient.
- **[CareConnect-ITK-Condition-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Condition-1)** -	An NHS Digital Profile derived from the CareConnect Condition Profile for conditions. The Condition Resource records detailed information about conditions or diagnoses recognised by a clinician.
- **[CareConnect-ITK-Procedure-List-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Procedure-List-1)** - An NHS Digital Profile derived from the CareConnect List Profile for recording a snapshot of the list of procedures for that the patient has had.
- **[CareConnect-ITK-Procedure-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Procedure)** - An NHS Digital Profile derived from the CareConnect Procedure Profile. The Procedure Resource is used to record an action that is or was performed on a patient.
-  **[CareConnect-ITK-MedicationDispense-List-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-MedicationDispense-List-1)** - An NHS Digital profile derived from the CareConnect List for recording a snapshot of the Medication(s) dispensed to the patient.
- **[CareConnect-ITK-MedicationDispense-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-MedicationDispense-1)** - An NHS Digital profile derived from the CareConnect MedicationDispense that indicates that a medication product is to be or has been dispensed for a named person/patient.
- **[CareConnect-ITK-Medication-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Medication-1)** - An NHS Digital Profile derived from the CareConnect Medication profile. The Medication Resource is primarily used for the identification and definition of a medication.
- **[CareConnect-Patient-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1)** - A CareConnect Profile for patient. The Patient Resource represents the patient involved in the provision of healthcare related services.
- **[CareConnect-Practitioner-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1)** - A CareConnect Profile for a practitioner. The Practitioner Resource represents the healthcare professional directly or indirectly involved in the provision of healthcare related services.
- **[CareConnect-PractitionerRole-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-PractitionerRole-1)** - A CareConnect Profile for a practitioner role.The PractitionerRole Resource represents a specific set of Roles/Locations/specialties/services that a practitioner may perform at an organization for a period of time.
- **[ITK-RelatedPerson-1](https://fhir.nhs.uk/STU3/StructureDefinition/ITK-RelatedPerson-1)** - An NHS Digital Profile which carries information for a person with a relationship to the patient.
- **[CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)** - A CareConnect Profile for Location. The Location Resource provides information and details on the physical location and the services provided.
- **[ITK-Device-1](https://fhir.nhs.uk/STU3/StructureDefinition/ITK-Device-1)** - An NHS Digital Profile which identifies an instance of a manufactured item that is used in the provision of healthcare without being substantially changed through that activity. The device may be a medical or non-medical device.

For a complete definition of the Digital Medicine Emergency Medication Supply FHIR Document see the section on [message definitions.](explore_emergency_meds_def.html)

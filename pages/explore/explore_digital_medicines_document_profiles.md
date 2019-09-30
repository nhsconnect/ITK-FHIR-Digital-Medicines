---
title: Digital Medicines Document Profiles 
keywords:  documents
sidebar: foundations_sidebar
permalink: explore_digital_medicines_document_profiles.html
summary: "ITK3 Digital Medicines FHIR Document profile"
---


## ITK3 Digital Medicines FHIR Document Bundle ##

The document bundle is a collection of FHIR Resource Profiles combined to support the Digital Medicines FHIR Document.

The Bundle consists of the following FHIR Resource Profiles.

- **[ITK-Document-Bundle-1](https://fhir.nhs.uk/STU3/StructureDefinition/ITK-Document-Bundle-1)** - An NHS Digital Bundle Profile to represent a container to collect a combination of the ITK3 FHIR Document resources.

## Compositions ##

- **[CareConnect-ITK-DM-Immunization-Composition-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-DM-Immunization-Composition-1)** - An NHS Digital Profile derived from the CareConnect Profile for FHIR Documents. This Profile is aligned to the PRSB standard for headings and subheadings for clinical documents and contains the data for recording Immunizations.

- **[CareConnect-ITK-DM-EmergencySupply-Composition-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-DM-EmergencySupply-Composition-1)** - An NHS Digital Profile derived from the CareConnect Profile for FHIR Documents. This Profile is aligned to the PRSB standard for headings and subheadings for clinical documents and contains the data for recording Emergency Supply.

- **[CareConnect-ITK-DM-MedicationReview-Composition-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-DM-MedicationReview-Composition-1)** - An NHS Digital Profile derived from the CareConnect Profile for FHIR Documents. This Profile is aligned to the PRSB standard for headings and subheadings for clinical documents and contains the data for recording Medication Review.

- **[CareConnect-ITK-DM-NewMedicineService-Composition-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-DM-NewMedicineService-Composition-1)** - An NHS Digital Profile derived from the CareConnect Profile for FHIR Documents. This Profile is aligned to the PRSB standard for headings and subheadings for clinical documents and contains the data for recording New Medicines.

- **[CareConnect-ITK-DM-ApplianceUseReview-Composition-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-DM-ApplianceUseReview-Composition-1)** - An NHS Digital Profile derived from the CareConnect Profile for FHIR Documents. This Profile is aligned to the PRSB standard for headings and subheadings for clinical documents and contains the data for recording Appliance Use Reviews.

- **[CareConnect-ITK-DM-DMIRS-Composition-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-DM-DMIRS-Composition-1)** - An NHS Digital Profile derived from the CareConnect Profile for FHIR Documents. This Profile is aligned to the PRSB standard for headings and subheadings for clinical documents and contains the data for recording Digital Minor Illness Referral Service.

## ITK Profiles ##

- **[CareConnect-ITK-AllergyIntolerance-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-AllergyIntolerance-1)** - An NHS Digital Profile derived from the CareConnect AllergyIntolerance Profile. The AllergyIntolerance Resource records risk of harmful or undesirable, physiological response which is unique to an individual and associated with exposure to a substance.
- **[CareConnect-ITK-Allergy-List-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Allergy-List-1)** - An NHS Digital Profile derived from the CareConnect List Profile for recording a snapshot of the list of Allergies for the patient.

- **[CareConnect-ITK-Condition-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Condition-1)** -	An NHS Digital Profile derived from the CareConnect List Profile for conditions. The Condition Resource records detailed information about conditions or diagnoses recognised by a clinician.
- **[CareConnect-ITK-Condition-List-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Condition-List-1)** - An NHS Digital Profile derived from the CareConnect List Profile for recording a snapshot of the list of Conditions for the patient.
- **[CareConnect-ITK-Encounter-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Encounter-1)** - A NHS Digital Profile derived from the CareConnect Encounter Profile. The Encounter Resource represents an Encounter between a care professional and the patient (or patient's record).
- **[CareConnect-ITK-DM-Immunization-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-DM-Immunization-1)** - An NHS Digital Profile derived from the CareConnect Immunization Profile.  The Immunization Resource describes the event of a patient being administered a vaccination or a record of a vaccination as reported by a patient, a clinician or another party and may include vaccine reaction information and what vaccination protocol was followed.
- **[CareConnect-ITK-Procedure-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Procedure-1)** - An NHS Digital Profile derived from the CareConnect Procedure Profile. The Procedure Resource is used to record an action that is or was performed on a patient.
- **[CareConnect-ITK-Procedure-List-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Procedure-List-1)** - An NHS Digital Profile derived from the CareConnect List Profile for recording a snapshot of the list of procedures that the patient has had.
- **[ITK-Attachment-Binary-1](https://fhir.nhs.uk/STU3/StructureDefinition/ITK-Attachment-Binary-1)** - An NHS Digital Profile which may be used to carry attachments to be included in the document. **See Note 1 below**:
- **[ITK-Device-1](https://fhir.nhs.uk/STU3/StructureDefinition/ITK-Device-1)** - An NHS Digital Profile which identifies an instance of a manufactured item that is used in the provision of healthcare without being substantially changed through that activity. The device may be a medical or non-medical device.
- **[ITK-RelatedPerson-1](https://fhir.nhs.uk/STU3/StructureDefinition/ITK-RelatedPerson-1)** - An NHS Digital Profile which carries information for a person with a relationship to the patient.

**Note 1**: This attachment Profile must not be used to send an unstructured Digital Medicines document, its purpose is to allow an attachment to be included within a structured Digital Medicines document.

## CareConnect Profiles ##

- **[CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)** - A CareConnect Profile for Location. The Location Resource provides information and details on the physical location and the services provided.
- **[CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)** - 	A CareConnect Profile for Organization. The Organization Resource represents the organisation that employs the healthcare professional.
- **[CareConnect-Medication-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Medication-1)** - A CareConnect Profile for MedicationRequest. This Medication Resource is primarily used for the identification and definition of a medication.
- **[CareConnect-MedicationDispense-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-MedicationDispense-1)** - A CareConnect Profile for MedicationDispense. Indicates that a medication product is to be or has been dispensed for a named person/patient.
- **[CareConnect-MedicationRequest-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-MedicationRequest-1)** - A CareConnect Profile for MedicationRequest. This MedicationRequest Resource represents an order for both supply of the medication and the instructions for administration of the medication to a patient.
- **[CareConnect-MedicationStatement-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-MedicationStatement-1)** - A CareConnect Profile for MedicationStatement. This MedicationStatement Resource is a record of a medication that is being consumed by a patient.
- **[CareConnect-Patient-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1)** - A CareConnect Profile for patient. The Patient Resource represents the patient involved in the provision of healthcare related services.
- **[CareConnect-Practitioner-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1)** - A CareConnect Profile for a practitioner. The Practitioner Resource represents the healthcare professional directly or indirectly involved in the provision of healthcare related services.
- **[CareConnect-PractitionerRole-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-PractitionerRole-1)** - A CareConnect Profile for a practitioner role. The PractitionerRole Resource represents a specific set of Roles/Locations/specialties/services that a practitioner may perform at an organization for a period of time.
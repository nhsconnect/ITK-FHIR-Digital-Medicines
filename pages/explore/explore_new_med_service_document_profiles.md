---
title: New Medicine Service Document Profiles 
keywords:  documents
tags: [fhir,messaging,documents]
sidebar: foundations_sidebar
permalink: explore_new_med_service_document_profiles.html
summary: "ITK3 Digital Medicines New Medicine Service FHIR Document profile"
---


## ITK3 Digital Medicines New Medicine Service FHIR Document Bundle ##

The document bundle is a collection of FHIR Resource Profiles combined to support the Digital Medicines New Medicine Service FHIR Document.

The Bundle consists of the following FHIR Resource Profiles.

- **[ITK-Document-Bundle-1](https://fhir.nhs.uk/STU3/StructureDefinition/ITK-Document-Bundle-1)** - An NHS Digital Bundle Profile to represent a container to collect a combination of the ITK3 FHIR Document resources.
- **[CareConnect-ITK-DM-NewMedicineService-Composition-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-DM-NewMedicineService-Composition-1)** - An NHS Digital Profile derived from the CareConnect Profile for Digital Medicine Immunization FHIR Documents. This Profile is aligned to the PRSB standard for headings and subheadings for clinical documents.
- **[CareConnect-ITK-Encounter-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Encounter-1)** - A NHS Digital Profile derived from the CareConnect Encounter Profile. The Encounter Resource represents an Encounter between a care professional and the patient (or patient's record).
- **[CareConnect-ITK-Allergy-List-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Allergy-List-1)** - An NHS Digital Profile derived from the CareConnect List Profile for recording a snapshot of the list of Allergies for the patient.
- **[CareConnect-ITK-AllergyIntolerance-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-AllergyIntolerance-1)** - An NHS Digital Profile derived from the CareConnect AllergyIntolerance Profile. The AllergyIntolerance Resource records risk of harmful or undesirable, physiological response which is unique to an individual and associated with exposure to a substance.
- **[CareConnect-ITK-Condition-List-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Condition-List-1)** - An NHS Digital Profile derived from the CareConnect List Profile for recording a snapshot of the list of Conditions for the patient.
- **[CareConnect-ITK-Condition-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Condition-1)** -	An NHS Digital Profile derived from the CareConnect List Profile for conditions. The Condition Resource records detailed information about conditions or diagnoses recognised by a clinician.
- **[CareConnect-ITK-Procedure-List-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Procedure-List-1)** - An NHS Digital Profile derived from the CareConnect List Profile for recording a snapshot of the list of procedures that the patient has had.
- **[CareConnect-ITK-Procedure-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Procedure-1)** - An NHS Digital Profile derived from the CareConnect Procedure Profile. The Procedure Resource is used to record an action that is or was performed on a patient.
- **[CareConnect-Patient-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1)** - A CareConnect Profile for patient. The Patient Resource represents the patient involved in the provision of healthcare related services.
- **[CareConnect-Practitioner-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1)** - A CareConnect Profile for a practitioner. The Practitioner Resource represents the healthcare professional directly or indirectly involved in the provision of healthcare related services.
- **[CareConnect-PractitionerRole-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-PractitionerRole-1)** - A CareConnect Profile for a practitioner role. The PractitionerRole Resource represents a specific set of Roles/Locations/specialties/services that a practitioner may perform at an organization for a period of time.
- **[ITK-RelatedPerson-1](https://fhir.nhs.uk/STU3/StructureDefinition/ITK-RelatedPerson-1)** - An NHS Digital Profile which carries information for a person with a relationship to the patient.
- **[CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)** - 	A CareConnect Profile for Organization. The Organization Resource represents the organisation that employs the healthcare professional.
- **[CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)** - A CareConnect Profile for Location. The Location Resource provides information and details on the physical location and the services provided.
- **[ITK-Device-1](https://fhir.nhs.uk/STU3/StructureDefinition/ITK-Device-1)** - An NHS Digital Profile which identifies an instance of a manufactured item that is used in the provision of healthcare without being substantially changed through that activity. The device may be a medical or non-medical device.
- **[ITK-Attachment-Binary-1](https://fhir.nhs.uk/STU3/StructureDefinition/ITK-Attachment-Binary-1)** - An NHS Digital Profile which may be used to carry attachments to be included in the document. **See Note 1 below**:

**Note 1**: This attachment Profile must not be used to send an unstructured Digital Medicines document, its purpose is to allow an attachment to be included within a structured Digital Medicines document.

For a complete definition of the Digital Medicines New Medicine Service document see the section on [message definitions.](explore_immunization_def.html)


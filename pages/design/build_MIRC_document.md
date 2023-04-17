---
title: Build Minor Illness Referral Consultation Document Coded Data
keywords: design, build,
tags: [design]
sidebar: foundations_sidebar
permalink: build_MIRC_document.html
summary: "Constructing a Minor Illness Consultation Document"
---


## Overview ##
This section details the coded data (FHIR resources) that should be included in a Minor Illness Referral Consultation Document.

## Resources Used for Headings within a Minor Illness Referral Consultation Document ##
Note: Only the headings that have coded data are listed here


<table>
<tr><th>Heading</th><th>FHIR Resources</th><th>Notes</th></tr>
<tr>
	<td><b>Allergies and adverse reactions</b></td>
	<td><a href="https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Allergies-List-1">CareConnect-ITK-Allergies-List-1</a>,<a href="https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-AllergyIntolerance-1">CareConnect-ITK-AllergyIntolerance-1</a></td>
	<td>See <a href="build_allergy_lists.html">Allery List</a> page on how to construct AllergyIntolerance resources in a List</td>
</tr>
<tr>
	<td><b>Distribution list Section</b></td>
	<td><a href="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1">CareConnect-Patient-1</a>, <a href="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1">CareConnect-Practitioner-1</a>, <a href="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1">CareConnect-Organization-1</a>, <a href="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-RelatedPerson-1">CareConnect-RelatedPerson-1</a>, <a href="http://hl7.org/fhir/stu3/binary.html">Attachment-Binary</a>, <a href="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-PractitionerRole-1">CareConnect-PractitionerRole-1</a></td>
	<td>See <a href="explore_distribution_list.html">Distribution list Section</a> for details. Resources may be used depending who (or what organisations) are on the distribution list.</td>
</tr>
<tr>
	<td><b>History</b></td>
		<td><a href="https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Condition-1">CareConnect-ITK-Condition-1</a>, <a href="https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Procedure-1">CareConnect-ITK-Procedure-1</a></td>
		<td>See <a href="explore_history.html">History Section</a> for details. The history section may contain details of a person’s significant medical, surgical and mental health history. Including relevant previous diagnoses, problems and issues, procedures, investigations, specific anesthesia issues, etc. These may be coded as either Condition or Procedure.</td>
</tr>
<tr>
	<td><b>Patient demographics</b></td>
	<td><a href="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1">CareConnect-Patient-1</a></td>
	<td>See <a href="explore_patient_demographics.html">Patient Demographics Section</a></td>
</tr>
<tr>
	<td><b>GP practice</b></td>
	<td><a href="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1">CareConnect-Organization-1</a></td>
	<td>See <a href="explore_gp_practice.html">GP Practice Section</a></td>
</tr>
<tr>
	<td><b>Contacts with professionals</b></td>
	<td><a href="https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Encounter-1">CareConnect-ITK-Encounter-1</a></td>
	<td>See <a href="explore_contacts_professionals.html">Contacts with professionals Section</a>. Encounter represents an Encounter between a care professional and the patient (or patient’s record)</td>
</tr>
<tr>
	<td><b>Medications and medical devices</b></td>
	<td><a href="https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-MedicationDispense-List-1">CareConnect-ITK-MedicationDispense-List-1</a>, <a href="https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-MedicationDispense-1">CareConnect-ITK-MedicationDispense-1</a>, <a href="https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Medication-1">CareConnect-ITK-Medication-1</a></td>
	<td>See <a href="explore_medication_mirc.html">Medications and Medical Devices Section</a>. For further details of constructing a medication dispense list see <a href="build_medication_dispense_list.html">Medication Dispense List</a></td>
</tr>
<tr>
	<td><b>Observations</b></td>
	<td>Observations (the list of Observations can be found <a href="https://fhir.hl7.org.uk/StructureDefinition">here</a></td>
	<td>See <a href="explore_observations.html">Observation Section</a> please check all the careconnect relevant to each observation</td>
</tr>
<tr>
	<td><b>Examination findings</b></td>
	<td>Observations (the list of Observations can be found <a href="https://fhir.hl7.org.uk/StructureDefinition">here</a></td>
	<td>See <a href="explore_examination_findings.html">Examination findings</a> please check all the careconnect relevant to each observation</td>
</tr>
<tr>
	<td><b>Signpost details</b></td>
	<td><a href="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-ReferralRequest-1">CareConnect-ReferralRequest-1</a>, <a href="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-HealthcareService-1">CareConnect-HealthcareService-1</a></td>
	<td>See <a href="explore_signpost_details.html">Signpost Details</a>. Referral requests are the requests made (signpostings), and the HealthcareService is the servive signposted to.</td>
</tr>
<tr>
	<td><b>Safeguarding</b></td>
	<td><a href="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Flag-1">CareConnect-Flag-1</a></td>
	<td>See <a href="explore_safeguarding.html">Safeguarding</a>. Flag is used to hold any safeguarding concerns.</td>
</tr>
</table>


---
title: Medications and Medical Devices Section
keywords:  messaging, sections
tags: [fhir,messaging,section]
sidebar: foundations_sidebar
permalink: explore_medication_ES.html
summary: "Gives information about the Medications and Medical Devices section"
---

{% include custom/section.warnbanner.html %}

## Medications and Medical Devices Section Content ##
The Medications and medical devices section carries information about the patient's medication. PRSB Elements should be formatted as subheadings in any HTML sent. For more information on constructing medication lists see [constructing clinical coded structures](build_medication_dispense_list.html).

<table style="width:100%;max-width: 100%;">
	<thead>
		<tr>
			<th width="15%">Section</th>
			<th width="35%">Description</th>
			<th width="5%">Card.</th>
			<th width="5%">MRO*</th>
			<th width="40%">FHIR Target and Guidance</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>Medications and Medical Devices </td>
			<td>The details of and instructions for medications and medical equipment the patient is using.</td>
			<td>0 to 1</td>
			<td>O</td>
			<td>Carried in the CodeableConcept of <b>Composition.section.code</b> FHIR element.</td>
		</tr>
		<tr>
			<th>PRSB Element</th>
			<th>Description</th>
			<th>Card.</th>
			<th>MRO*</th>
			<th>FHIR Target and Guidance</th>		
		</tr>
		<tr>
			<td>Supply type</td>
			<td>A description of the type of medication being supplied (e.g. emergency supply, over the counter medication, patient group direction etc.).</td>
			<td>0 to 1</td>
			<td>R</td>
			<td>Carried in the CodeableConcept of <b>MedicationDispense.type</b> FHIR element. See <a href="build_medication_dispense_list.html#type">medicationDispense.type</a> for further guidance.</td> 
		</tr>
		<tr>
			<td>Medication name</td>
			<td>May be generic name or brand name (as appropriate). Mandatory medication name coded using a SNOMED CT/dm+d term where possible, allowing plain text for historical/patient reported items , extemporaneous preparations or those not registered in dm+d. Comment: e.g. "Citalopram tab 20mg", "Trimethoprim".</td>
			<td>1 only</td>
			<td>M</td>
			<td>Text and a SNOMED CT concept carried in the CodeableConcept of the FHIR element <b>MedicationDispense.medication[x].<br/>medicationReference.Medication.Name</b>. See <a href="build_medication_dispense_list.html#medicationcode">medication.code</a> for further guidance.</td>
		</tr>
		<tr>
			<td>Form</td>
			<td>Form of the medicinal substance e.g. capsules, tablets, liquid. Not normally required unless a specific form has been requested by the prescriber.  Comment: e.g. "Modified Release Capsules".</td>
			<td>0 to 1</td>
			<td>O</td>
			<td>Text and a SNOMED CT concept carried in the CodeableConcept of the FHIR element <b>MedicationDispense.medication[x].<br/>medicationReference.Medication.form</b>. See <a href="build_medication_dispense_list.html#medicationform">medication.form</a> for further guidance.</td>
		</tr>
		<tr>
			<td>Batch number</td>
			<td>The batch number of the medicine.</td>
			<td>0 to 1</td>
			<td></td>
			<td>Not required in Pharmacy to GP communication.</td>
		</tr>
		<tr>
			<td>Site</td>
			<td>The anatomical site at which the medication is to be administered.  Comment: e.g. "Left eye".</td>
			<td>0 to 1</td>
			<td>O</td>
			<td>Text and a SNOMED CT concept carried in the CodeableConcept of the FHIR element <b>MedicationDispense.dosageInstruction.site</b>.</td>
		</tr>
		<tr>
			<td>Route</td>
			<td>Medication administration description (oral, IM, IV, etc.): may include method of administration, (e.g., by infusion, via nebuliser, via NG tube).</td>
			<td>0 to many</td>
			<td>O</td>
			<td>Text and a SNOMED CT concept carried in the CodeableConcept of the FHIR element <b>MedicationDispense.dosageInstruction.route</b>.</td>
		</tr>
		<tr>
			<td>Indication</td>
			<td>Reason for medication being prescribed, where known.</td>
			<td>0 to 1</td>
			<td>R</td>
			<td>A free text or code derived text term giving the clinical indication or reason for ordering the medication.</td>
		</tr>
		<tr>
			<td>Reason for supply</td>
			<td>The reason why the patient is being supplied the medication as an 'emergency supply of medication' e.g patient is on holiday and has left medication at home.</td>
			<td>1 only</td>
			<td>M</td>
			<td>Free text. Carried in the <b>MedicationDispense.type</b> FHIR element. See <a href="build_medication_dispense_list.html#type">medicationDispense.type</a> for further guidance.</td>
		</tr>
		<tr>
			<td>Reason for non supply</td>
			<td>The reason why the patient is refused an 'emergency supply of medication'. </td>
			<td>0 to 1</td>
			<td>R</td>
			<td>Guidance to be confirmed</td>
		</tr>
		<tr>
			<td>Total amount of medication supplied</td>
			<td>A description of the total amount of medication supplied e.g 30 tablets, 100ml etc.</td>
			<td>1 only</td>
			<td>M</td>
			<td>Recorded in a structured format i.e. a unit (eg ml, tablet, etc.) and a value (eg 100, 1, 0.5 etc.). Carried in the <b>MedicationDispense.quantity</b> FHIR element. See <a href="build_medication_dispense_list.html#quantity">medicationDispense.quantity</a> for further guidance.</td>
		</tr>
		<tr>
			<td>Dose directions description</td>
			<td>A single plain text phrase describing the entire medication dosage and administration directions, including dose quantity and medication frequency.  Comment: e.g. "I tablet at night" or "20mg at 10pm" This is the form of dosage direction text normally available from UK GP systems.</td>
			<td>0 to 1</td>
			<td>O</td>
			<td>Text within the <b>section.narrative.text</b> and text repeated in the FHIR element <b>MedicationDispense.dosageInstruction.text</b>.</td>
		</tr>
		<tr>
			<td>Additional instructions</td>
			<td>Allows for: <br> - requirements for adherence support, e.g., compliance aids, prompts and packaging requirements <br> - additional information about specific person requirements, e.g., unable to swallow tablets.medicines, e.g., where specific brand required</td>
			<td>0 to many</td>
			<td>O</td>
			<td>Free text. Carried in the <b>MedicationDispense.dosageInstruction.additionalInstruction.text</b> FHIR element.</td>
		</tr>
		<tr>
			<td>Supplied by</td>
			<td>The name of the person who supplied the medication, preferably in a structured format.</td>
			<td>1 only</td>
			<td>M</td>
			<td>Free text. Carried in the <b>MedicationDispense.performer.actor</b> FHIR element.</td>
		</tr>
		<tr>
			<td>Role</td>
			<td>The role of the person who supplied the medication.</td>
			<td>0 to 1</td>
			<td>R</td>
			<td>The role may be held on the source system, be from an authoritative source such as SDS, or use an existing vocabulary such as the job role title (from the national workforce dataset). Carried in the <b>TBC</b> FHIR element.</td>
		</tr>
		<tr>
			<td>Professional identifier</td>
			<td>Professional identifier and regulatory body of the person who supplied the medication.</td>
			<td>0 to 1</td>
			<td>R</td>
			<td>The role may be held on the source system, be from an authoritative source such as SDS, or use an existing vocabulary such as the job role title (from the national workforce dataset). Carried in the <b>TBC</b> FHIR element.</td>
		</tr>
		<tr>
			<td>Date/time</td>
			<td>The date/time on which the medication was supplied to the patient.</td>
			<td>0 to 1</td>
			<td>R</td>
			<td>The date/time as recorded by the pharmacy system. Carried in the <b>MedicationDispense.whenHandedOver</b> FHIR element.</td>
		</tr>
		<tr>
		<td colspan="5"><b>* M=Mandatory R=Required O=Optional</b></td>
		</tr>
	</tbody>
</table>


## Example Medications and Medical Devices Section ##

<script src="https://gist.github.com/IOPS-DEV/8c976ad43f09cf155ad9af55093eb29c.js"></script>

## Coded Resources ##

This text section should be linked to the following FHIR Resources to provide the textual information in a coded format.

- List
- MedicationDispense
- Medication
 
See constructing clinical coded structures - [Medication Dispense List](build_medication_dispense_list.html)












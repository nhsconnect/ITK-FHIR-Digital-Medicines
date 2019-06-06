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
			<td colspan="5"><b>Medications</b></td>
		</tr>
		<tr>
			<td>Supply type</td>
			<td>A description of the type of medication being supplied (e.g. emergency supply, over the counter medication, patient group direction etc.).</td>
			<td>0 to 1</td>
			<td>R</td>
			<td>Emergency supply <br/>
​Minor ailments scheme  <br/>
​Over the counter  <br/>
​Patient group direction <br/> 
​Prescription dispensing  <br/>
​Private prescription dispensing  <br/>
​Self declared <br/>
 <br/>
			Carried in the CodeableConcept of <b>MedicationDispense.type</b> FHIR element. See <a href="build_medication_dispense_list.html#type">medicationDispense.type</a> for further guidance.</td> 
		</tr>
		<tr>
			<td>Medication name</td>
			<td>May be generic name or brand name (as appropriate).</td>
			<td>1 only</td>
			<td>M</td>
			<td>Choice of<br/>
 • Text<br/>
• Coded text (needs to be GS1 code mapped to DM+D)– constraint: MedicationName. Any AMP/VMP/VTM/AMPP/VMPP subsets from the dm+d terminology. NHS dm+d AMP ::352201000001139 NHS dm+d AMPP ::352401000001135 NHS dm+d VMP ::352701000001133 NHS dm+d VMPP  ::352601000001138. Constraint binding: [dm+d]subset=NHS_dm+d
			<br/><br/>
			Text and a SNOMED CT concept carried in the CodeableConcept of the FHIR element <b>MedicationDispense.medication[x].<br/>medicationReference.Medication.Name</b>. See <a href="build_medication_dispense_list.html#medicationcode">medication.code</a> for further guidance.</td>
		</tr>
		<tr>
			<td>Form</td>
			<td>Eg capsule, drops, tablet, lotion etc.</td>
			<td>0 to 1</td>
			<td>O</td>
			<td>Choice of<br/>
 • Text<br/>
 • Coded text – constraint: DrugDoseForm. SNOMED CT CfH DoseForm termset. Any descendant of 421967003 | drug dose form. Constraint binding: [SNOMED CT]subset=CfH DoseForm
			<br/><br/>
			Text and a SNOMED CT concept carried in the CodeableConcept of the FHIR element <b>MedicationDispense.medication[x].<br/>medicationReference.Medication.form</b>. See <a href="build_medication_dispense_list.html#medicationform">medication.form</a> for further guidance.</td>
		</tr>
		<tr>
			<td>Site</td>
			<td>The anatomical site at which the medication is to be administered.  Comment: e.g. "Left eye".</td>
			<td>0 to 1</td>
			<td>O</td>
			<td>Choice of<br/>
 • Text<br/>
 • Coded text – constraint: SiteOfMedicationAdministration. Any valid site for the administration of a medication. Constraint binding: [SNOMED-CT]subset= SiteOfMedicationAdministration
			<br/><br/>
			Text and a SNOMED CT concept carried in the CodeableConcept of the FHIR element <b>MedicationDispense.dosageInstruction.site</b>.</td>
		</tr>
		<tr>
			<td>Indication</td>
			<td>Reason for medication being prescribed, where known.</td>
			<td>0 to 1</td>
			<td>R</td>
			<td>This will be free text or SNOMED CT subset</td>
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
			<td>This will be free text. Text within the <b>section.narrative.text</b> and text repeated in the FHIR element <b>MedicationDispense.dosageInstruction.text</b>.</td>
		</tr>
		<tr>
			<td>Additional instructions</td>
			<td>Allows for: <br> - requirements for adherence support, e.g., compliance aids, prompts and packaging requirements <br> - additional information about specific person requirements, e.g., unable to swallow tablets.medicines, e.g., where specific brand required</td>
			<td>0 to many</td>
			<td>O</td>
			<td>Free text. Carried in the <b>MedicationDispense.dosageInstruction.additionalInstruction.text</b> FHIR element.</td>
		</tr>
		<tr>
			<td>Date/time</td>
			<td>The date/time on which the medication was supplied to the patient.</td>
			<td>0 to 1</td>
			<td>R</td>
			<td>The date/time as recorded by the pharmacy system. Carried in the <b>MedicationDispense.whenHandedOver</b> FHIR element.</td>
		</tr>
		<tr>
			<td colspan="5"><b>Appliances</b></td>
		</tr>
		<tr>
			<td>Appliance name</td>
			<td>May be generic name or brand name (as appropriate).</td>
			<td>1 only</td>
			<td>M</td>
			<td>As per dm+d (AMP)</td>
		</tr>
		<tr>
			<td>Size</td>
			<td>The size of the appliance.</td>
			<td>0 to 1</td>
			<td>R</td>
			<td>As per dm+d (AMP) appliance product information (where applicable)</td>
		</tr>
		<tr>
			<td>Weight</td>
			<td>The weight of the appliance.</td>
			<td>0 to 1</td>
			<td>R</td>
			<td>As per dm+d (AMP) appliance product information (where applicable)</td>
		</tr>
		<tr>
			<td>Colour</td>
			<td>The colour of the appliance.</td>
			<td>0 to 1</td>
			<td>R</td>
			<td>As per dm+d (AMP) appliance product information (where applicable)</td>
		</tr>
		<tr>
			<td>Route</td>
			<td>Appliance administration description (IM, IV, etc.): may include method of administration, (e.g., by infusion).</td>
			<td>0 to 1</td>
			<td>R</td>
			<td>E.g. catheter may have been introduced suprapubically or urethrally. <br/>
<br/>
The following value set may be applicable, but would need validating for appliances:<br/>
<br/>
• Coded text – constraint: NHS e-prescribing route of administration subset ID: 413001000001136 Original Id : 30201000001137 This is an extract from the SUBSET -BiAnnual-Drug-15.0.1-20130401: SnomedCT_GB1000001_20130401/Subsets/EPrescribing/NHS e-Prescribing route of administration subset. Constraint binding: [SNOMED-CT]subset=NHS e-Prescribing route of administration subset
</td>
		</tr>
		<tr>
			<td>Site</td>
			<td>The anatomical site at which the appliance is to be used, including laterality.</td>
			<td>0 to 1</td>
			<td>R</td>
			<td>The following value set may be applicable, but would need validating for appliances:<br/>
 • Coded text – constraint: SiteOfMedicationAdministration. Any valid site for the administration of a medication. Constraint binding: [SNOMED-CT]subset= SiteOfMedicationAdministration</td>
		</tr>
		<tr>
			<td>Quantity</td>
			<td>The quantity of the appliance (including the units).</td>
			<td>0 to 1</td>
			<td>R</td>
			<td>Recorded in a structured format i.e. a unit and a value.</td>
		</tr>
		<tr>
			<td>Indication</td>
			<td>Reason for appliance being prescribed, where known.</td>
			<td>0 to 1</td>
			<td>R</td>
			<td>Free text</td>
		</tr>
		<tr>
			<td>Date/time</td>
			<td>The date/time on which the appliance was supplied to the patient.</td>
			<td>0 to 1</td>
			<td>R</td>
			<td>The date/time as recorded by the pharmacy system.</td>
		</tr>
		<tr>
			<td colspan="5"><b>* M=Mandatory R=Required O=Optional</b></td>
		</tr>
	</tbody>
</table>


## Example Medications and Medical Devices Section ##

```
<xml>
	<section>
		<title value="Medications and medical devices"/>
		<code>
			<coding>
				<system value="http://snomed.info/sct"/>
				<code value="933361000000108"/>
				<display value="Medications and medical devices"/>
			</coding>
		</code>
		<text>
		<status value="additional"/>
		<div xmlns="http://www.w3.org/1999/xhtml">
		<table width="100%">
			<tbody>
			<tr>
				<th>Medication name</th>
				<td>BD Viva hypodermic insulin needles for pre-filled / reusable pen injectors screw on 5mm/31gauge (Becton, Dickinson UK Ltd)</td>
			</tr>
			<tr>
				<th>Dose directions description</th>
				<td>As needed.</td>
			</tr>
			</tbody>
		</table>
		</div>
		</text>
		<!--reference to further information carried in the medication dispense list resource-->
		<entry>
			<reference value="urn:uuid:4bc7faea-5974-407a-b658-d6ed1d4c9187"/>
		</entry>
	</section>
</xml>
```

## Coded Resources ##

This text section should be linked to the following FHIR Resources to provide the textual information in a coded format.

- List
- MedicationDispense
- Medication
 
See constructing clinical coded structures - [Medication Dispense List](build_medication_dispense_list.html)












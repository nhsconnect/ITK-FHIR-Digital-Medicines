---
title: Medications and Medical Devices Section
keywords:  messaging, sections
tags: [fhir,messaging,section]
sidebar: foundations_sidebar
permalink: explore_medication_dmirs.html
summary: "Gives information about the Medications and Medical Devices section"
---

{% include custom/section.warnbanner.html %}

## Medications and Medical Devices Section Content ##
The Medications and medical devices section carries information about the patient's medication. PRSB Elements should be formatted as subheadings in any HTML sent. For more information on constructing medication lists see [constructing clinical coded structures](build_medication_dispense_list.html).

| MEDICATIONS   AND MEDICAL DEVICES   | |             | |                                  |                                                                            |                                                                                |
|-----------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------|---------------------------------------------|------------------------------------|-----------------------------------------------------------------------------------------------------|
|     Supply Appropriate             |     Confirmation   that in the opinion of the pharmacist, it is appropriate to sell a medicine   to the patient under the NHS CPCS                   |                    |     Options   - "Yes", "No"                 |     Mandatory                      |     Composition.section.text                                                                        |
|     Med1 Supplied                  |     The name of any   "over the counter" (OTC) medication supplied to support the patient   with treatment of their minor illness                    |                    |     Free text data   entry                  |     Mandatory                      |     Composition.section.text and     MedicationDispense.   medicationReference. Medication. code    |
|     Med1 Supplied_cost             |     The cost of any   OTC medication  provided to the patient                                                                                        |                    |     Free text data   entry                  |     Mandatory                      |     Composition.section.text                                                                        |
|     Med1 Supplied_Quantity         |     The quantity of   any OTC medication provided to the patient                                                                                     |                    |     Free text data   entry                  |     Mandatory                      |     Composition.section.text and     MedicationDispense.   quantity                                 |
|     Med1 Dose                      |     The dosage   instructions for the OTC medication provided to the patient                                                                         |                    |     Free text data   entry                  |     Mandatory                      |     Composition.section.text and     MedicationDispense.   dosageInstruction. text                  |
|     Med2 Supplied                  |     The name of any   "over the counter" (OTC) medication supplied to support the patient   with treatment of their minor illness                    |                    |     Free text data   entry                  |     Mandatory                      |     Composition.section.text and     MedicationDispense.   medicationReference. Medication. code    |
|     Med2 Supplied_cost             |     The cost of any   OTC medication  provided to the patient                                                                                        |                    |     Free text data   entry                  |     Mandatory                      |     Composition.section.text                                                                        |
|     Med2 Supplied_Quantity         |     The quantity of   any OTC medication provided to the patient                                                                                     |                    |     Free text data   entry                  |     Mandatory                      |     Composition.section.text and     MedicationDispense.   quantity                                 |
|     Med2 Dose                      |     The dosage   instructions for the OTC medication provided to the patient                                                                         |                    |     Free text data   entry                  |     Mandatory                      |     Composition.section.text and     MedicationDispense.   dosageInstruction. text                  |
|     Advice Provided With Medicine    |     Details of any   additional advice given to the patient                                                                                          |                    |     Free text data   entry                  |     Mandatory                      |     Composition.section.text and     MedicationDispense.note                                        |
|     Advice Provided Only            |     Confirmation   that only advice was given to the patient                                                                                         |                    |     Options - "Yes",   "No"                 |     Mandatory                      |     Composition.section.text                                                                        |
|     Additional Instructions        |     Any additional   information or instructions provided to the patient as part of the   consultation                                               |                    |     Free text data   entry                  |     Mandatory                      |     Composition.section.text                                                                        |
|     Person Advised                 |     Recording of the   person who was given the advice and their relationship to the patient if they   were representing them in the consultation    |                    |     Options drop   down menu (see notes)    |     Mandatory                      |     Composition.section.text                                                                        |
|     Symptom Advice Given            |     Any specific   symptom advice provided to the patient                                                                                            |                    |     Free text data   entry                  |     Mandatory                      |     Composition.section.text                                                                        |



## Example Medications and Medical Devices Section ##

{% include note.html content="These examples have not been clinically assured against Digital Medicines use cases.<br/>Examples are illustrative only." %}

```
<!--<xml>-->
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
					<th>Supply type</th>
					<td>A description of the type of medication being supplied (e.g. emergency supply, over the counter medication, patient group direction etc.).</td>
				</tr>
				<tr>
					<th>Medication name</th>
					<td>BD Viva hypodermic insulin needles for pre-filled / reusable pen injectors screw on 5mm/31gauge (Becton, Dickinson UK Ltd)</td>
				</tr>
				<tr>
					<th>Form</th>
					<td>capsule</td>
				</tr>
				<tr>
					<th>Site</th>
					<td>"Mouth"</td>
				</tr>
				<tr>
					<th>Indication</th>
					<td>Reason for medication being prescribed, where known.</td>
				</tr>
				<tr>
					<th>Total amount of medication supplied</th>
					<td>30 tablets</td>
				</tr>
				<tr>
					<th>Dose directions description</th>
					<td>I tablet at night" or "20mg at 10pm"</td>
				</tr>
				<tr>
					<th>Additional instructions</th>
					<td>Allows for: <br> - requirements for adherence support, e.g., compliance aids, prompts and packaging requirements <br> - additional information about specific person requirements, e.g., unable to swallow tablets.medicines, e.g., where specific brand required</td>
				</tr>
				<tr>
					<th>Date/time</th>
					<td>The date/time on which the medication was supplied to the patient.</td>
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
<!--</xml>-->
```

## Coded Resources ##

This text section should be linked to the following FHIR Resources to provide the textual information in a coded format.

- List
- MedicationDispense
- Medication
 
See constructing clinical coded structures - [Medication Dispense List](build_medication_dispense_list.html)
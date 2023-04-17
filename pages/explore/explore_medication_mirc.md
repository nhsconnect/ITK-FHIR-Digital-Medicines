---
title: Medications and Medical Devices Section
keywords:  messaging, sections
tags: [fhir,messaging,section]
sidebar: foundations_sidebar
permalink: explore_medication_mirc.html
summary: "Gives information about the Medications and Medical Devices section"
---

{% include custom/section.warnbanner.html %}

## Medications and Medical Devices Section Content ##
The Medications and medical devices section carries information about the patient's medication. PRSB Elements should be formatted as subheadings in any HTML sent. For more information on constructing medication lists see [constructing clinical coded structures](build_medication_dispense_list.html).

| MEDICATIONS   AND MEDICAL DEVICES   |                                                                                                                                                                                                                                                                                                            |             |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |                                  |                                                                 |
|-------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------|-----------------------------------------------------------------|
| Data Item                           | Description                                                                                                                                                                                                                                                                                                | Cardinality | Values                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | Mandatory / Required / Optional | FHIR Target                                                     |
| Supply type                         | A description of the type of supply (e.g. emergency supply, over the counter medication, patient group direction etc)                                                                                                                                                                                  | 0 TO 1    | Emergency supply, Minor ailments scheme, Over the counter, Patient group direction, Prescription dispensing, Private prescription dispensing, Self declared                                                                                                                                                                                                                                                                                                                                                                                                       | Required                         | MedicationDispense.type        |
| MEDICATIONS                         |                                                                                                                                                                                                                                                                                                            |           |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |    |                          |
| Medication name                     | May be generic name or brand name (as appropriate).                                                                                                                                                                                                                                                      | 1 ONLY    | Choice of • Text • Coded text (needs to be GS1 code mapped to dm+d)– constraint:  MedicationName. An AMP or AMPP from the dm+d terminology.   NHS dm+d AMP ::352201000001139 NHS dm+d AMPP ::352401000001135. Constraint binding: [dm+d]subset= NHS_dm+d | Mandatory  | MedicationDispense. medicationReference. Medication. code |
| Form                                | E.g. capsule, drops, tablet, lotion etc.                                                                                                                                                                                                                                                                   | 0 TO 1    | Choice of • Text • Coded text – constraint: DrugDoseForm. SNOMED CT CfH DoseForm termset. Any descendant of 421967003 - drug dose form. Constraint binding: [SNOMED CT]subset= CfH DoseForm | Required  | MedicationDispense. medicationReference. Medication. form |
| Route | The route by which the medication is administered e.g. oral, IM, IV | 0 TO 1    | Choice of • Text • Coded text – constraint: SNOMED CT: - ^999000051000001100 ePrescribing route of administration simple reference set (foundation metadata concept) | Required  | MedicationDispense. dosageInstruction. route  |
| Site                                | The anatomical site at which the medication is to be administered. Comment: e.g. "Left eye" | 0 TO 1    | Choice of • Text • Coded text – constraint: SiteOfMedicationAdministration. Any valid site for the administration of a medication. Constraint binding: [SNOMED-CT]subset= SiteOfMedicationAdministration | Required  | MedicationDispense. dosageInstruction. site  |
| Indication                          | Reason for medication being supplied, where known. | 0 TO 1  | This will be free text | Required  | Record in Composition.section.text  |
| Total amount of medication supplied | A description of the total amount of medication supplied. | 1 ONLY  | Recorded as a quantity and unit of measure (eg 50 ml, 28 tablet, 5 vial).  | Required  | MedicationDispense. quantity |
| Days Supply                         | Amount of medication supplied expressed as a number of days. | 1 TO 1 | Recorded as a number of days (eg 7 days) | Mandatory | MedicationDispense.daysSupply |
| Structured dose direction cluster - Structured dose amount  | A structural representation of dose amount, e.g. 20mg or 2 tablets. | 0 TO 1 | As per FHIR Dose Syntax Implementation Guidance (see link below) | Required | MedicationDispense. doseQuantity |
| Structured dose direction cluster - Structured dose timing  | A computable representation of dose timing and maximum dose | 0 TO 1 | As per FHIR Dose Syntax Implementation Guidance (see link below) | Required | MedicationDispense. timing |
| Structured dose direction cluster - Dose direction duration  | Recommendation of the time period for which the medication should be continued | 0 TO 1 | As per FHIR Dose Syntax Implementation Guidance (see link below) | Required | MedicationDispense. text |
| Dose directions description         | A single plain text phrase describing the entire medication dosage and administration directions including dose quantity and medication frequency. Comment: e.g. “1 tablet at night or “2mg at 10pm”. This is the form of dosage direction text normally available from UK GP Systems.                | 1 TO 1    | This will be free text | Mandatory  | MedicationDispense. dosageInstruction. text |
| Additional instructions             | Allows for: * requirements for adherence support, e.g. compliance aids, prompts and packaging requirements * additional information about specific person requirements, e.g. unable to swallow tablets.medicines, e.g. where specific brand required | 0 TO MANY | This will be free text. | Required | MedicationDispense. dosageInstruction. additionalInstruction. text |
| Date/time  | The date/time on which the medication was supplied to the patient. | 0 TO 1    | The date/time as recorded by the pharmacy system.| Required | MedicationDispense. whenHandedOver |
| APPLIANCES                          |                                                                                                                                                                                                                                                                                                            |           |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |  |  |
| Appliance   name                    | May be generic name or brand name (as appropriate).                                                                                                                                                                                                                                                      | 1 ONLY    | As per dm+d (AMP)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | Mandatory | MedicationDispense. medicationreference. Medication. code |
| Size                                | The size of the appliance.                                                                                                                                                                                                                                                                                 | 0 TO 1    | As per dm+d (AMP) appliance product information (where applicable)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | Required  | MedicationDispense. medicationreference. Medication. code |
| Weight                              | The weight of the appliance.                                                                                                                                                                                                                                                                               | 0 TO 1    | As per dm+d (AMP) appliance product information (where applicable)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | Required  | MedicationDispense. medicationreference. Medication. code |
| Colour                              | The colour of the appliance.                                                                                                                                                                                                                                                                               | 0 TO 1    | As par dm+d (AMP) appliance product information (where applicable)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | Required  | MedicationDispense. medicationreference. Medication. code |
| Route                               | Appliance administration description (IM, IV, etc.): may include method of administration, (e.g. by infusion).                                                                                                                                                                                        | 0 TO 1    | E.g. catheter may have been introduced suprapubically or urethrally. The following value set may be applicable, but would need validating for appliances: • Coded text – constraint: NHS e-prescribing route of administration subset ID: 413001000001136 Original Id : 30201000001137 This is an extract from the SUBSET -BiAnnual-Drug-15.0.1-20130401: SnomedCT_GB1000001_20130401 / Subsets / EPrescribing / NHS e-Prescribing route of administration subset. Constraint binding: [SNOMED-CT]subset= NHS   e-Prescribing route of administration subset | Required  | MedicationDispense. dosageInstruction. route  |
| Site                                | The anatomical site at which the appliance is to be used, including laterality.                                                                                                                                                                                                                        | 0 TO 1    | The following value set may be applicable, but would need validating for appliances: • Coded text – constraint: SiteOfMedicationAdministration. Any valid site for the administration of a medication. Constraint binding: [SNOMED-CT]subset= SiteOfMedicationAdministration | Required  | MedicationDispense. dosageInstruction. site  |
| Quantity                            | The quantity of the appliance (including the units).                                                                                                                                                                                                                                                     | 0 TO 1    | Recorded in a structured format i.e. a unit and a value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | Required  | MedicationDispense. quantity |
| Indication                          | Reason for appliance being prescribed, where known. | 0 TO 1  | Free text | Required  | N/A as not available within the MedicationDispense resource |
| Date/time                           | The date/time on which the appliance was supplied to the patient.                                                                                                                                                                                                                                        | 0 TO 1    | The date/time as recorded by the pharmacy system.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | Required  | MedicationDispense. whenHandedOver |

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
			<td>Eg capsule, drops, tablet, lotion etc.</td>
		</tr>
		<tr>
			<th>Site</th>
			<td>The anatomical site at which the medication is to be administered.  Comment: e.g. "Left eye".</td>
		</tr>
		<tr>
			<th>Indication</th>
			<td>Reason for medication being prescribed, where known.</td>
		</tr>
		<tr>
			<th>Total amount of medication supplied</th>
			<td>A description of the total amount of medication supplied e.g 30 tablets, 100 ml etc.</td>
		</tr>
		<tr>
			<th>Days Supply</th>
			<td>Amount of medication supplied expressed as a number of days e.g 5 days, 30 days etc.</td>
		</tr>
		<tr>
			<th>Dose directions description</th>
			<td>A single plain text phrase describing the entire medication dosage and administration directions, including dose quantity and medication frequency.  Comment: e.g. "I tablet at night" or "20mg at 10pm" This is the form of dosage direction text normally available from UK GP systems.</td>
		</tr>
		<tr>
			<th>Additional instructions</th>
			<td>Allows for: <br> - requirements for adherence support, e.g., compliance aids, prompts and packaging requirements <br> - additional information about specific person requirements, e.g., unable to swallow tablets.medicines, e.g., where specific brand required</td>
		</tr>
		<tr>
			<th>Date/time</th>
			<td>The date/time on which the medication was supplied to the patient.</td>
		</tr>
		<tr>
			<td colspan="5"><b>Appliances</b></td>
		</tr>
		<tr>
			<th>Appliance name</th>
			<td>May be generic name or brand name (as appropriate).</td>
		</tr>
		<tr>
			<th>Size</th>
			<td>The size of the appliance.</td>
		</tr>
		<tr>
			<th>Weight</th>
			<td>The weight of the appliance.</td>
		</tr>
		<tr>
			<th>Colour</th>
			<td>The colour of the appliance.</td>
		</tr>
		<tr>
			<th>Route</th>
			<td>Appliance administration description (IM, IV, etc.): may include method of administration, (e.g., by infusion).</td>
		</tr>
		<tr>
			<th>Site</th>
			<td>The anatomical site at which the appliance is to be used, including laterality.</td>
		</tr>
		<tr>
			<th>Quantity</th>
			<td>The quantity of the appliance (including the units).</td>
		</tr>
		<tr>
			<th>Indication</th>
			<td>Reason for appliance being prescribed, where known.</td>
		</tr>
		<tr>
			<th>Date/time</th>
			<td>The date/time on which the appliance was supplied to the patient.</td>
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

- [List](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-MedicationDispense-List-1)
- [MedicationDispense](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-MedicationDispense-1)
- [Medication](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Medication-1)
 
See constructing clinical coded structures - [Medication Dispense List](build_medication_dispense_list.html)

## Link to Dose Syntax Guidance ##

[Dose Syntax](https://simplifier.net/guide/ukcoreimplementationguideformedicines/home?version=current)
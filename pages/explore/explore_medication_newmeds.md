---
title: Medications and Medical Devices Section
keywords:  messaging, sections
tags: [fhir,messaging,section]
sidebar: foundations_sidebar
permalink: explore_medication_newmeds.html
summary: "Gives information about the Medications and Medical Devices section"
---

{% include custom/section.warnbanner.html %}

## Medications and Medical Devices Section Content ##
The Medications and medical devices section carries information about the patient's medication. PRSB Elements should be formatted as subheadings in any HTML sent. For more information on constructing medication lists see [constructing clinical coded structures](build_medication_dispense_list.html).

| MEDICATIONS   AND MEDICAL DEVICES        |                                                                                                                                                                                                                                                                                                 |             |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |                             |                                                                            |
|------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------|----------------------------------------------------------------------------|
| Data Item                                | Description                                                                                                                                                                                                                                                                                     | Cardinality | Values                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | Mandatory/required/optional | FHIR Target                                                                |
| Medication name                          | May   be generic name or brand name (as appropriate).                                                                                                                                                                                                                                           | 1 ONLY      | Choice   of      • Text     • Coded text (needs to be GS1 code mapped to DM+D)– constraint:   MedicationName. Any AMP/VMP/VTM/AMPP/VMPP subsets from the dm+d terminology.   NHS dm+d AMP ::352201000001139 NHS dm+d AMPP ::352401000001135 NHS dm+d VMP   ::352701000001133 NHS dm+d VMPP ::352601000001138. Constraint binding:   [dm+d]subset=NHS_dm+d                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | Mandatory                   | MedicationStatement.medication[x].     medicationReference.Medication.Name |
| Form                                     | E.g.   capsule, drops, tablet, lotion etc.                                                                                                                                                                                                                                                      | 0 TO 1      | Choice   of     • Text     • Coded text – constraint: DrugDoseForm. SNOMED CT CfH DoseForm termset.   Any descendant of 421967003 drug dose form. Constraint binding: [SNOMED   CT]subset=CfH DoseForm                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | Required                    | MedicationStatement.medication[x].     medicationReference.Medication.form |
| Route                                    | Medication   administration description (oral, IM, IV, etc.): may include method of   administration, (e.g., by infusion, via nebuliser, via NG tube).                                                                                                                                          | 0 TO MANY   | •   Coded text – constraint: NHS e-prescribing route of administration subset ID:   413001000001136 Original Id : 30201000001137 This is an extract from the   SUBSET -BiAnnual-Drug-15.0.1-20130401:   SnomedCT_GB1000001_20130401/Subsets/EPrescribing/NHS e-Prescribing route of   administration subset. Constraint binding: [SNOMED-CT]subset=NHS   e-Prescribing route of administration subset                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | Required                    | MedicationStatement.dosage.route                                           |
| Indication                               | Reason   for medication being prescribed, where known.                                                                                                                                                                                                                                          | 0 TO 1      | This   will be free text or SNOMED CT subset                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | Required                    | Composition.section.text                                                   |
| Dose   directions description            | A single plain   text phrase describing the entire medication dosage and administration   directions including dose quantity and medication frequency. Comment, e.g.,   “1 tablet at night or “2mg at 10pm”. This is the form of dosage direction   text normally available from UK GP Systems. | 0 TO 1      | Free   text                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | Required                    | Composition.section.text                                                   |
| Matters identified during the discussion | Matters   identified during the service about the patient's experience of using the   medication. To include e.g., patient using/not using the medicine as   prescribed, patient reports side effects, patient reports negative feelings   about the medication etc.                            | 1 TO MANY   | Coded   text using the following descriptors:      a. patient reports using the medicine as prescribed     b. patient reports not using the medicine as prescribed     i. patient has not started using the medicine     ii. prescriber has stopped new medicine     iii. patient is not using the medicine in line with the directions of the   prescriber     iv. patient reports missing a dose in the past 7 days     c. patient reports need for more information about the medicine      d. patient reports side effects     e. patient reports negative feelings about the medicine      f. patient reports uncertainty on whether the medicine is working      g. patient reports concern about remembering to take the medicine      h. patient reports difficulty using the medicine due to its pharmaceutical   form/formulation     i. other - free text option | Mandatory                   | Composition.section.text                                                   |

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
			<td>A description of the total amount of medication supplied e.g 30 tablets, 100ml etc.</td>
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
</xml>
```

## Coded Resources ##

This text section should be linked to the following FHIR Resources to provide the textual information in a coded format.

- List
- MedicationDispense
- Medication
 
See constructing clinical coded structures - [Medication Dispense List](build_medication_dispense_list.html)












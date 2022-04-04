---
title: Medications and Medical Devices Section - NOW RETIRED
keywords:  messaging, sections
tags: [fhir,messaging,section]
sidebar: foundations_sidebar
permalink: explore_medication_medrev.html
summary: "Gives information about the Medications and Medical Devices section"
---

{% include warning.html content="The medication review use case is now retired and you cannot implement it." %}

{% include custom/section.warnbanner.html %}

## Medications and Medical Devices Section Content ##
The Medications and medical devices section carries information about the patient's medication. PRSB Elements should be formatted as subheadings in any HTML sent. For more information on constructing medication lists see [constructing clinical coded structures](build_medication_dispense_list.html).

| MEDICATIONS   AND MEDICAL DEVICES        |                                                                                                                                                                                                                                                                                                 |             |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |                                  |                                                         |
|------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------|---------------------------------------------------------|
| Data Item                                | Description                                                                                                                                                                                                                                                                                     | Cardinality | Values                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | Mandatory/required/     optional | FHIR Target                                             |
| Medication name                          | May   be generic name or brand name (as appropriate).                                                                                                                                                                                                                                           | 1 ONLY      | Choice   of           • Text     • Coded text (needs to be GS1 code mapped to DM+D)– constraint:   MedicationName. Any AMP/VMP/VTM/AMPP/VMPP subsets from the dm+d terminology.   NHS dm+d AMP ::352201000001139 NHS dm+d AMPP ::352401000001135 NHS dm+d VMP   ::352701000001133 NHS dm+d VMPP    ::352601000001138. Constraint binding: [dm+d]subset=NHS_dm+d                                                                                                                                                                                                                                                                                                                                                                                                                                                                  | Mandatory                        | MedicationStatement.medicationReference.Medication.code |
| Form                                     | E.g.   capsule, drops, tablet, lotion etc.                                                                                                                                                                                                                                                      | 0 TO 1      | Choice   of           • Text           • Coded text – constraint:   DrugDoseForm. SNOMED CT CfH DoseForm termset. Any descendant of 421967003 -   drug dose form. Constraint binding: [SNOMED CT]subset=CfH DoseForm                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | Required                         | MedicationStatement.medicationReference.Medication.form |
| Route                                    | Medication   administration description (oral, IM, IV, etc.): may include method of   administration, (e.g., by infusion, via nebuliser, via NG tube).                                                                                                                                          | 0 TO MANY   | •   Coded text – constraint: NHS e-prescribing route of administration subset ID:   413001000001136 Original Id : 30201000001137 This is an extract from the   SUBSET -BiAnnual-Drug-15.0.1-20130401:   SnomedCT_GB1000001_20130401/Subsets/EPrescribing/NHS e-Prescribing route of   administration subset. Constraint binding: [SNOMED-CT]subset=NHS   e-Prescribing route of administration subset                                                                                                                                                                                                                                                                                                                                                                                                                            | Required                         | MedicationStatement.dosage.route                        |
| Indication                               | Reason   for medication being prescribed, where known.                                                                                                                                                                                                                                          | 0   TO 1    | This   will be free text or SNOMED CT subset                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     | Required                         | MedicationStatement.reasonCode                          |
| Dose directions description              | A   single plain text phrase describing the entire medication dosage and   administration directions including dose quantity and medication frequency.   Comment, e.g., “1 tablet at night or “2mg at 10pm”. This is the form of   dosage direction text normally available from UK GP Systems. | 0 TO 1      | Free   text                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | Required                         | MedicationStatement.dosage.text                         |
| Matters identified during the discussion | Matters   identified during the service about the patient's experience of using the   medication. To include e.g., patient using/not using the medicine as   prescribed, patient reports side effects, patient reports negative feelings   about the medication etc.                            | 1 TO MANY   | Coded   text using the following descriptors:      a. patient not using a medicine as prescribed (non-adherence)     b. problem with pharmaceutical form of a medicine or use of a device     c. patient reports need for more information about a medicine or   condition     d. patient reports side effects or other concern about a medicine     e. Potential drug interactions      f. Potential side effects/adverse drug reaction preventing use of the   medicine     g. Patient reports not using the medicine any more      h. Patient reports lack of efficacy      i. Patient reports problem with dosage regimen      j. Patient reports unresolved concern about the medicine     k. other (free text information can be entered in the clinical record)        l. No matters identified during medication review  | Mandatory                        | Composition.section.text                                |

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
					<th>Medication name</th>
					<td>BD Viva hypodermic insulin needles for pre-filled / reusable pen injectors screw on 5mm/31gauge (Becton, Dickinson UK Ltd)</td>
				</tr>
				<tr>
					<th>Form</th>
					<td>injection</td>
				</tr>
				<tr>
					<th>Route</th>
					<td>IM</td>
				</tr>
				<tr>
					<th>Indication</th>
					<td>Reason for medication being prescribed, where known.</td>
				</tr>
				<tr>
					<th>Dose directions description</th>
					<td>I tablet at night" or "20mg at 10pm</td>
				</tr>
				<tr>
					<th>Matters identified during the discussion</th>
					<td>patient reports need for more information about the medicine</td>
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

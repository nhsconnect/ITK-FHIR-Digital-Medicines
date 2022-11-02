---
title: Appliances - NOW RETIRED
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_appliances_appuse.html
summary: "Gives information about the Appliances section"
---

{% include warning.html content="The applicance use review use case is now retired and you cannot implement it." %}

{% include custom/section.warnbanner.html %}

## Appliances Section Content ##
The Appliances section carries information about the appliances used. PRSB Elements should be formatted as subheadings in any HTML sent.

| APPLIANCES                               |                                                                                                                                                                                                                                                                                                                                                           |             |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |                                  |                                                                          |
|------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------|--------------------------------------------------------------------------|
| Data Item                                | Description                                                                                                                                                                                                                                                                                                                                               | Cardinality | Values                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | Mandatory/required/     optional | FHIR Target                                                              |
| Appliance name                           | May   be generic name or brand name (as appropriate).                                                                                                                                                                                                                                                                                                     | 1 ONLY      | As   per dm+d (AMP)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | Mandatory                        | MedicationStatement.medicationReference.Medication.code                  |
| Product order number                     | The   product order number for the appliance.                                                                                                                                                                                                                                                                                                             | 0   TO 1    | As   per dm+d (AMP) appliance product information (where applicable)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | <font color="red">Optional</font>                         | MedicationStatement.medicationReference.Medication.code                  |
| Manufacturer                             | Name   of appliance manufacturer.                                                                                                                                                                                                                                                                                                                         | 0   TO 1    | As   per dm+d (AMP)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | <font color="red">Optional</font>                         | Medication.manufacturer                                                  |
| Batch number                             | The   batch number of the appliance.                                                                                                                                                                                                                                                                                                                      | 0   TO 1    | Free   text                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               | <font color="red">Optional</font>                         | Medication.package.batch.lotNumber                                       |
| Size                                     | The   size of the appliance.                                                                                                                                                                                                                                                                                                                              | 0   TO 1    | As   per dm+d (AMP) appliance product information (where applicable)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | Required                         | MedicationStatement.medicationReference.Medication.code                  |
| Weight                                   | The   weight of the appliance.                                                                                                                                                                                                                                                                                                                            | 0   TO 1    | As   per dm+d (AMP) appliance product information (where applicable)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | Required                         | MedicationStatement.medicationReference.Medication.code                  |
| Colour                                   | The   colour of the appliance.                                                                                                                                                                                                                                                                                                                            | 0   TO 1    | As   par dm+d (AMP) appliance product information (where applicable)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | Required                         | MedicationStatement.medicationReference.Medication.code                  |
| Route                                    | Appliance   administration description (IM, IV, etc.): may include method of   administration, (e.g., by infusion).                                                                                                                                                                                                                                       | 0   TO 1    | E.g.   catheter may have been introduced suprapubically or urethrally.           The following value set may be applicable, but would need validating for   appliances:          • Coded text – constraint: NHS e-prescribing route of administration subset   ID: 413001000001136 Original Id : 30201000001137 This is an extract from the   SUBSET -BiAnnual-Drug-15.0.1-20130401:   SnomedCT_GB1000001_20130401/Subsets/EPrescribing/NHS e-Prescribing route of   administration subset. Constraint binding: [SNOMED-CT]subset=NHS   e-Prescribing route of administration subset      | Required                         | MedicationStatement.dosage.route                                         |
| Site                                     | The   anatomical site at which the appliance is to be used, including   laterality.                                                                                                                                                                                                                                                                       | 0   TO 1    | The   following value set may be applicable, but would need validating for   appliances:      • Coded text – constraint:   SiteOfMedicationAdministration. Any valid site for the administration of a   medication. Constraint binding: [SNOMED-CT]subset=   SiteOfMedicationAdministration                                                                                                                                                                                                                                                                                               | Required                         | MedicationStatement.dosage.site                                          |
| Quantity                                 | The   quantity of the appliance (including the units).                                                                                                                                                                                                                                                                                                    | 0   TO 1    | Recorded   in a structured format i.e. a unit and a value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | Required                         | MedicationStatement.basedon.medicationrequest.dispenserequested.quantity |
| Indication                               | Reason   for appliance being prescribed, where known.                                                                                                                                                                                                                                                                                                     | 0   TO 1    | Free   text                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               | Required                         | MedicationStatement.reasoncode                                           |
| Matters identified during the discussion | Matters   identified during the service about the patient's experience of using the   appliance. To include e.g, patient using/not using the appliance as   prescribed, patient reports negative feelings about the appliance etc. Also   to include whether the information was provided by the patient or somebody   else (e.g. a relative, carer etc). | 1 TO MANY   | Coded.  Reference set needs to be defined e.g.   patient using/not using the appliance as prescribed, patient reports negative   feelings about the appliance etc.                                                                                                                                                                                                                                                                                                                                                                                                                        | Mandatory                        | Composition.section.text                                                 |

## Example Clinical Summary Section ##

```
<!--<xml>-->
<!--Appliances-->
	<section>
		<title value="Appliances"/>
		<code>
			<coding>
				<system value="http://snomed.info/sct"/>
				<code value="334251007"/>
				<display value="Appliance"/>
			</coding>
		</code>
		<text>
			<status value="additional"/>
			<div xmlns="http://www.w3.org/1999/xhtml">
			<table width="100%">
				<tbody>
				<tr>
					<th>Appliance name</th>
					<td>May be generic name or brand name (as appropriate).</td>
				</tr>
				<tr>
					<th>Product order number</th>
					<td>The product order number for the appliance.</td>
				</tr>
				<tr>
					<th>Manufacturer</th>
					<td>Name of appliance manufacturer.</td>
				</tr>
				<tr>
					<th>Batch number</th>
					<td>The batch number of the appliance.</td>
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
					<th>Matters identified during the discussion</th>
					<td>Matters identified during the service about the patient’s experience of using the appliance. To include e.g, patient using/not using the appliance as prescribed, patient reports negative feelings about the appliance etc. Also to include whether the information was provided by the patient or somebody else (e.g. a relative, carer etc).</td>
				</tr>
				</tbody>
			</table>
			</div>
		</text>
	</section>
<!--</xml>-->
```

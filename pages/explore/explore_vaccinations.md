---
title: Vaccinations Section
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_vaccinations.html
summary: "Gives information about the vaccinations section"
---

{% include custom/section.warnbanner.html %}

## Vaccinations Section Content ##
The vaccinations section carries information about the vaccinations administered. PRSB Elements should be formatted as subheadings in any HTML sent.

| VACCINATIONS       |                                                                                               |             |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |                                  |                                              |
|--------------------|-----------------------------------------------------------------------------------------------|-------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------|----------------------------------------------|
| Data Item          | Description                                                                                   | Cardinality | Values                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | Mandatory/required/     optional | FHIR Target                                  |
| Vaccine product    | Vaccine   product administered.                                                               | 1   ONLY    | Choice   of           • Text           • Coded text - constraint:   MedicationName. Any AMP/VMP/VTM/AMPP/VMPP subsets from the dm+d terminology.   NHS dm+d AMP ::352201000001139 NHS dm+d AMPP ::352401000001135 NHS dm+d VMP   ::352701000001133 NHS dm+d VMPP ::352301000001131 NHS dm+d VTM   ::352601000001138. Constraint binding: [dm+d]subset=NHS_dm+d          (In the future needs to be GS1 code mapped to dm+d)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | Mandatory                        | Immunization.vaccineCode                     |
| Vaccine procedure  | The   vaccination that was given e.g. seasonal influenza vaccination.                         | 1   ONLY    | For   seasonal flu vaccinations the following coded text should be used:          955691000000108 - Seasonal influenza vaccination given by pharmacist   (situation) -          Note that 849211000000109 - seasonal influenza vaccination given by pharmacist   (finding) - in the NHSE service specification was made inactive in April 2015   and was replaced by the concept above               For general vaccinations the following coded text should be used:      <<33879002 -Active immunisation-     <<304250009 -Immunisation status-     <<713404003 -Vaccination given-          In addition there are some scattered concepts below in the situations   hieararchy.     <<955641000000103 -Influenza vaccination given by other healthcare   provider-     955701000000108 -Seasonal influenza vaccination given while hospital   inpatient-     <<957581000000102 -Meningitis B vaccination given by other healthcare   provider-     957751000000103 -Meningitis ACW & Y vaccination given by other   healthcare provider-     <<1066171000000108 -Seasonal influenza vaccination given by   midwife-     140611000119104 -Human papilloma virus type 16 and 18 vaccination   given-      | Mandatory                        | Immunization.extension(vaccinationProcedure) |
| Manufacturer       | Name   of vaccine manufacturer                                                                | 0   TO 1    | Derived   from GS1 code/free text                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | Required                         | Immunization.manufacturer                    |
| Serialisation code | A   code that separately identifies two identical vaccines (i.e. same product,   same batch). | 0   TO 1    | Derived   from FMD code/Free text                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | <font color="red">Optional</font>                         | Composition.section.text                     |
| Site               | Body   site vaccine was administered into.                                                    | 0   TO 1    | Choice   of      • Text      • Coded text – constraint:   SiteOfMedicationAdministration. Any valid site for the administration of a   medication. Constraint binding: [SNOMED-CT]subset=   SiteOfMedicationAdministration                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  | Required                         | Immunization.site                            |
| Route              | How   vaccine entered the body.                                                               | 0   TO 1    | •   Coded text – constraint: NHS e-prescribing route of administration subset ID:   413001000001136 Original Id : 30201000001137 This is an extract from the   SUBSET -BiAnnual-Drug-15.0.1-20130401:   SnomedCT_GB1000001_20130401/Subsets/EPrescribing/NHS e-Prescribing route of   administration subset. Constraint binding: [SNOMED-CT]subset=NHS   e-Prescribing route of administration subset.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | Required                         | Immunization.route                           |
| Indication         | The   clinical indication or reason for administering the vaccine.                            | 0   TO 1    | This   will be free text/proposal to use the list from below (as an example   list)     Routine mass immunisation    171279008-Immunization due (finding)-          Travel to endemic area    414448007-Identified as high risk for travel immunization   (finding)-     Planned travel to high risk area 161096004-Going to travel abroad   (finding)-     Recent travel to high risk area 506931000000109-Recent travel to disease   affected area (finding)-          Subpopulation at special or unusual risk    78648007-At risk for infection (finding)-     High risk due to occupation 14679004 Occupation (occupation)     High risk due to lifestyle 134436002-Lifestyle (finding)-     High risk due to existing medical condition 398192003-Co-morbid conditions   (finding)-          Control of known sporadic outbreak    443684005-Disease outbreak (event)-          Patient request  183995001-Patient   requested procedure (situation)-          Post-exposure prophyaxis    444107005-Exposure to communicable disease (event)-          Other  723620004-Requires vaccination   (finding)                                                                                             | <font color="red">Optional</font>                         | Immunization.explanation.reason              |
| Dose amount        | Amount   of vaccine administered.                                                             | 0   TO 1    | This   will be free text. Coded units of measure (from DM+D)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | Required                         | Immuinzation.doseQuantity                    |
| Date/time          | The   date/time on which the vaccine was administered.                                        | 0   TO 1    | The   date/time as recorded by the pharmacy system.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | Required                         | Immunization.date                            |

## Example Vaccinations Section ##

```
<!--<xml>-->
<!--Vaccinations-->
	<section>
		<title value="Vaccinations"/>
		<code>
			<coding>
				<system value="http://snomed.info/sct"/>
				<code value="1102181000000102"/>
				<display value="Immunisations"/>
			</coding>
		</code>
		<text>
		<status value="additional"/>
		<div xmlns="http://www.w3.org/1999/xhtml">
		<table width="100%">
			<tbody>
			<tr>
				<th>Vaccine product</th>
				<td>Seasonal influenza vaccination given by pharmacist.</td>
			</tr>
			<tr>
				<th>Vaccine procedure</th>
				<td>The vaccination that was given e.g. seasonal influenza vaccination.</td>
			</tr>
			<tr>
				<th>Manufacturer</th>
				<td>Name of vaccine manufacturer</td>
			</tr>
			<tr>
				<th>Serialisation code</th>
				<td>xyz991/td>
			</tr>
			<tr>
				<th>Site</th>
				<td>Upper right arm<</td>
			</tr>
			<tr>
				<th>Route</th>
				<td>Subcutaneous route</td>
			</tr>
			<tr>
				<th>Indication</th>
				<td>Patient requested procedure.</td>
			</tr>
			<tr>
				<th>Dose amount</th>
				<td>Amount of vaccine administered.</td>
			</tr>
			<tr>
				<th>DateTime</th>
				<td>9-May-2018 10:00</td>
			</tr>
			</tbody>
		</table>
		</div>
		</text>
		<entry>
			<reference value="urn:uuid:631ec8d3-6341-4c9e-b2a1-131af62718f2"/>
		</entry>
	</section>
<!--</xml>-->
```

## Coded Resources ##

This text section should be linked to the following FHIR Resources to provide the textual information in a coded format.

- Immunization
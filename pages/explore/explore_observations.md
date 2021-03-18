---
title: Observation Section
keywords:  messaging, sections
tags: [fhir,messaging,sections]
sidebar: foundations_sidebar
permalink: explore_observations.html
summary: "Gives information about the Observations section"
---

{% include custom/section.warnbanner.html %}

## Clinical Observations for Minor Illness Referral Consultation (MIRC) ##
The Observations section carries details related to the patient's observations. The list of coded Clinical Observations has been defined as: 

- Blood Pressure 
- Pulse Rate
- Temperature
- Height
- Weight
- Oxygen Saturation
- Pain Score
- Level of Consciousness
- Respiratory Rate
- NEW2 Score

Elements should be rendered as subheadings in any HTML sent.

##  Example Clinical Observations for Minor Illness Referral Consultation (MIRC) Section ##

{% include note.html content="These examples have not been clinically assured against Digital Medicines use cases.<br/>Examples are illustrative only." %}

```
<!--<xml>-->
<!--Observations-->
<section>
	<title value="Observations"/>
	<code>
		<coding>
			<system value="http://snomed.info/sct"/>
			<code value="1102421000000108"/>
			<display value="Observations"/>
		</coding>
	</code>
	<text>
		<status value="additional"/>
		<div xmlns="http://www.w3.org/1999/xhtml">
			<table width="100%">
				<tbody>
					<tr>
						<th>Observation</th>
						<th>Performed</th>
						<th>Reading</th>
					</tr>
					<tr>
						<td>Respiration rate</td>
						<td>2021-02-08T12:34:04</td>
						<td>38 /min</td>
					</tr>
					<tr>
						<td>Pulse rate</td>
						<td>2021-02-08T12:35:15</td>
						<td>92 /min</td>
					</tr>
					<tr>
						<td>Oxygen saturation</td>
						<td>2021-02-08T12:36:45</td>
						<td>98%</td>
					</tr>
					<tr>
						<td>Air or oxygen</td>
						<td>2021-02-08T12:36:55</td>
						<td>Air</td>
					</tr>
					<tr>
						<td>Temperature</td>
						<td>2021-02-08T12:37:30</td>
						<td>37 C</td>
					</tr>
					<tr>
						<td>Systolic pressure</td>
						<td>2021-02-08T12:39:34/td>
						<td>84 mmHg</td>
					</tr>
					<tr>
						<td>Consciousness score</td>
						<td>2021-02-08T12:40:01</td>
						<td>voice</td>
					</tr>
					<tr>
						<td>NEWS2</td>
						<td>2021-02-08T12:40:15</td>
						<td>6</td>
					</tr>
				</tbody>
			</table>
		</div>
	</text>
</section>

<!--</xml>-->
```
<a href="explore_observations.html">Back to top of page</a>

## Coded Resources ##

The text section should be linked to the following FHIR resources to provide the textual information in a coded format.

## Blood Pressure Observation ## 

The coded form of each blood pressure reading follows the codes and structure for [CareConnect-BloodPressure-Observation-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-BloodPressure-Observation-1).

| CareConnect-Observation-1 element | Cardinality | Notes                                                                                                           |
|-------------------------------------|-------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| meta.profile        | 1..1  | Claim conformance to ‘https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-BloodPressure-Observation-1’                                                                       |
| status          | 1..1  | Fixed to final                                                                                                        |
| category          | 1..1  | Fixed as per profile                                                                                                      |
| code            | 1..1  | Loinc slice – fixed as per profile<br>SNOMED slice – fixed as per profile                                                                                   |
| subject           | 1..1  | Link to Patient                                                                                                       |
| effectiveDateTime       | 1..1  | The date and time the blood pressure reading took place                                                                                             |
| performer         | 0..*  | Either <br>- use the identifier part of Reference data type to hold the identifier of the practitioner<br>- use the display part of the Reference data type to hold the name of the practitioner<br>- use the reference to point to a CareConnect-Practitioner-1<br>- use the reference to point to the Organization (pharmacy) |
| dataAbsentReason        | 0..1  | An optional reason why the data is absent                                                                                             |
| comment           | 0..1  | Any additional comments                                                                                                     |
| bodySite          | 0..1  | Optional body site of reading                                                                                                   |
| component systolic      |     |                                                                                                             |
| - code            | 1..1  | Loinc slice – fixed as per profile<br>SNOMED slice – fixed as per profile                                                                                   |
| - valueQuantity         | 0..1  | Recorded as per the profile                                                                                                   |
| - dataAbsentReason        | 0..1  | A reason the data is absent                                                                                                   |
| component diastolic       |     |                                                                                                             |
| - code            | 1..1  | Loinc slice – fixed as per profile<br>SNOMED slice – fixed as per profile                                                                                   |
| - valueQuantity         | 0..1  | Recorded as per the profile                                                                                                   |
| - dataAbsentReason        | 0..1  | A reason the data is absent                                                                                                   |

###  Blood Pressure Observation Example ###
{% include note.html content="These examples have not been clinically assured against Digital Medicines use cases.<br/>Examples are illustrative only." %}

```
<!--<xml>-->
<Observation xmlns="http://hl7.org/fhir">
	<id value="f80fc9e3-a4fe-400e-8fe4-83f7d5616ea2"/>
	<meta>
		<!--claim conformance to CareConnect-BloodPressure-Observation-1-->
		<profile value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-BloodPressure-Observation-1"/>
	</meta>
	<!--a fixed value for status-->
	<status value="final"/>
	<!--fixed value for category-->
	<category>
		<coding>
			<system value="http://hl7.org/fhir/observation-category"/>
			<code value="vital-signs"/>
			<display value="Vital Signs"/>
		</coding>
	</category>
	<!--fixed values for code-->
	<code>
		<coding>
			<system value="http://loinc.org"/>
			<code value="85354-9"/>
			<display value="Blood pressure panel with all children optional"/>
		</coding>
		<coding>
			<system value="http://snomed.info/sct"/>
			<code value="75367002"/>
			<display value="Blood pressure"/>
		</coding>
	</code>
	<!--a link to the Patient-->
	<subject>
		<reference value="Patient/4f78d392-c9e0-4f1f-9ab6-57d387838690"/>
	</subject>
	<!--the date and time of the reading-->
	<effectiveDateTime value="2018-10-04T14:17:59+01:00"/>
	<!--example of a link to a Practitioner-->
	<performer>
		<reference value="Practitioner/2360aba6-8561-4a22-bbbf-afc08e750146"/>
	</performer>
	<!--an example of the name of the practitioner-->
	<performer>
		<display value="DAVIES Gemma"/>
	</performer>
	<!--example of a link to the pharmacy-->
	<performer>
		<reference value="Organization/cd5f7770-6249-4f5d-ad8e-d0bb1446a4d9"/>
	</performer>
	<!--body site of reading-->
	<bodySite>
		<coding>
			<system value="http://snomed.info/sct"/>
			<code value="368209003"/>
			<display value="Right arm"/>
		</coding>
	</bodySite>
	<!--systolic-->
	<component>
		<!--fixed values for code-->
		<code>
			<coding>
				<system value="http://loinc.org"/>
				<code value="8480-6"/>
				<display value="Systolic blood pressure"/>
			</coding>
			<coding>
				<system value="http://snomed.info/sct"/>
				<code value="72313002"/>
				<display value="Systolic blood pressure"/>
			</coding>
		</code>
		<!--the systolic reading-->
		<valueQuantity>
			<value value="120"/>
			<unit value="mmHg"/>
			<system value="http://unitsofmeasure.org"/>
		</valueQuantity>
	</component>
	<!--diastolic-->
	<component>
		<!--fixed values for code-->	
		<code>
			<coding>
				<system value="http://loinc.org"/>
				<code value="8462-4"/>
				<display value="Diastolic blood pressure"/>
			</coding>
			<coding>
				<system value="http://snomed.info/sct"/>
				<code value="1091811000000102"/>
				<display value="Diastolic arterial pressure"/>
			</coding>
		</code>
		<!--the diastolic reading-->
		<valueQuantity>
			<value value="60"/>
			<unit value="mmHg"/>
			<system value="http://unitsofmeasure.org"/>
		</valueQuantity>
	</component>
</Observation>
<!--</xml>-->
```
<a href="explore_observations.html">Back to top of page</a>

## Pulse Rate Observation ## 

The coded form of each pulse rate reading follows the codes and structure for [CareConnect-HeartRate-Observation-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-HeartRate-Observation-1).

| CareConnect-Observation-1 element | Cardinality | Notes                                                                                                          |
|-------------------------------------|-------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| meta.profile        | 1..1    | Claim conformance to ‘https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-HeartRate-Observation-1’                                                                      |
| status          | 1..1    | Fixed to final                                                                                                       |
| category          | 1..1    | Fixed as per profile                                                                                                     |
| code            | 1..1    | Loinc slice – fixed as per profile<br>SNOMED slice – fixed as per profile<br>There could be a further SNOMED coding to narrow heart rate to pulse rate (see example below)                                                 |
| subject           | 1..1    | Link to Patient                                                                                                      |
| effectiveDateTime       | 1..1    | The date and time the reading took place                                                                                             |
| performer         | 0..*    | Either<br>- use the identifier part of Reference data type to hold the identifier of the practitioner<br>- use the display part of the Reference data type to hold the name of the practitioner<br>- use the reference to point to a CareConnect-Practitioner-1<br>- use the reference to point to the Organization (pharmacy) |
| valueQuantity         | 0..1    | The pulse rate recorded in beats per minute (/min)                                                                                           |
| dataAbsentReason        | 0..1    | An optional reason why the data is absent                                                                                              |
| comment           | 0..1    | Any additional comments                                                                                                    |
| bodySite          | 0..1    | Optional body site of reading                                                                                                  |

### Pulse Rate Observation Example ###
{% include note.html content="These examples have not been clinically assured against Digital Medicines use cases.<br/>Examples are illustrative only." %}

```
<!--<xml>--> 
<Observation xmlns="http://hl7.org/fhir">
	<id value="a1f2519e-3cb1-4ba4-820a-57e47334b655"/>
	<meta>
		<!--claims conformance to CareConnect-HeartRate-Observation-1-->
		<profile value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-HeartRate-Observation-1"/>
	</meta>
	<!--fixed value for status-->
	<status value="final"/>
	<!--fixed value for category-->
	<category>
		<coding>
			<system value="http://hl7.org/fhir/observation-category"/>
			<code value="vital-signs"/>
			<display value="Vital Signs"/>
		</coding>
	</category>
	<!--fixed values for code, plus an extra SNOMED code for pulse rate-->
	<code>
		<coding>
			<system value="http://loinc.org"/>
			<code value="8867-4"/>
			<display value="Heart rate"/>
		</coding>
		<coding>
			<system value="http://snomed.info/sct"/>
			<code value="364075005"/>
			<display value="Heart rate"/>
		</coding>
		<coding>
			<system value="http://snomed.info/sct"/>
			<code value="78564009"/>
			<display value="Pulse rate"/>
			<userSelected value="true"/>
		</coding>
	</code>
	<!--link to patient-->
	<subject>
		<reference value="Patient/4f78d392-c9e0-4f1f-9ab6-57d387838690"/>
	</subject>
	<!--the date and time of the reading-->
	<effectiveDateTime value="2018-10-04T14:17:59+01:00"/>
	<!--example of a link to a Practitioner-->
	<performer>
		<reference value="Practitioner/2360aba6-8561-4a22-bbbf-afc08e750146"/>
	</performer>
	<!--an example of the name of the practitioner-->
	<performer>
		<display value="DAVIES Gemma"/>
	</performer>
	<!--example of a link to the pharmacy-->
	<performer>
		<reference value="Organization/cd5f7770-6249-4f5d-ad8e-d0bb1446a4d9"/>
	</performer>
	<!--the pulse rate reading-->
	<valueQuantity>
		<value value="95"/>
		<unit value="/min"/>
		<system value="http://unitsofmeasure.org"/>
	</valueQuantity>
</Observation>
<!--</xml>-->
```
<a href="explore_observations.html">Back to top of page</a>

## Height Observation ##

The coded form of each height reading follows the codes and structure for [CareConnect-Observation-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Observation-1).

| CareConnect-VitalSigns-Observation-1 element | Cardinality | Notes                                                                                                          |
|-------------------------------------|-------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| meta.profile        | 1..1    | Claim conformance to ‘https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-VitalSigns-Observation-1’                                                                          |
| status          | 1..1    | Fixed to final                                                                                                       |
| category          | 1..1    | Fixed as demonstrated in example below                                   |
| code            | 1..1    | Fixed as demonstrated in example below        |
| subject           | 1..1    | Link to Patient                                                                                                      |
| effectiveDateTime       | 1..1    | The date and time the reading took place                                                                                             |
| performer         | 0..*    | Either<br>- use the identifier part of Reference data type to hold the identifier of the practitioner<br>- use the display part of the Reference data type to hold the name of the practitioner<br>- use the reference to point to a CareConnect-Practitioner-1<br>- use the reference to point to the Organization (pharmacy) |
| valueQuantity         | 0..1    | The height recorded in metres or centimetres                                                                                             |
| dataAbsentReason        | 0..1    | An optional reason why the data is absent                                                                                              |
| comment           | 0..1    | Any additional comments                                                                                                    |
| bodySite          | 0..1    | Optional body site of reading                                                                                                  |
   
### Height Observation Example ###
{% include note.html content="These examples have not been clinically assured against Digital Medicines use cases.<br/>Examples are illustrative only." %}

```
<!--<xml>-->  
<Observation xmlns="http://hl7.org/fhir">
	<id value="dbbad20f-e696-405e-8c98-be0cdcc5406c"/>
	<meta>
		<!--claims conformance to CareConnect-Observation-1-->
		<profile value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Observation-1"/>
	</meta>
	<!--fixed value for status-->
	<status value="final"/>
	<!--fixed value for category-->
	<category>
		<coding>
			<system value="http://hl7.org/fhir/observation-category"/>
			<code value="vital-signs"/>
			<display value="Vital Signs"/>
		</coding>
	</category>
	<!--fixed values for code-->
	<code>
		<coding>
			<system value="http://loinc.org"/>
			<code value="8302-2"/>
			<display value="Body height"/>
		</coding>
		<coding>
			<system value="http://snomed.info/sct"/>
			<code value="50373000"/>
			<display value="Body height"/>
		</coding>
	</code>
	<!--link to patient-->
	<subject>
		<reference value="Patient/4f78d392-c9e0-4f1f-9ab6-57d387838690"/>
	</subject>
	<!--date time when reading occurred-->
	<effectiveDateTime value="2018-10-04T14:17:59+01:00"/>
	<!--the performer-->
	<performer>
		<reference value="Performer/2360aba6-8561-4a22-bbbf-afc08e750146"/>
	</performer>
	<performer>
		<reference value="Organization/cd5f7770-6249-4f5d-ad8e-d0bb1446a4d9"/>
	</performer>
	<!--the reading-->
	<valueQuantity>
		<value value="175"/>
		<unit value="cm"/>
		<system value="http://unitsofmeasure.org"/>
	</valueQuantity>
</Observation>
<!--</xml>-->
```
<a href="explore_observations.html">Back to top of page</a>


## Weight Observation ##

The coded form of each weight reading follows the code and structure for [CareConnect-Observation-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Observation-1).

| CareConnect-Observation-1 element |  | Notes                                                                                                            |
|-----------------------------------|------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| meta.profile        | 1..1 | Claim conformance to 'https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Observation-1'                                                                             |
| status          | 1..1 | Fixed to final                                                                                                         |
| category          | 1..1 | Fixed as demonstrated in example below                                                                                                 |
| code          | 1..1 | Fixed as demonstrated in example below                                                                                                 |
| subject         | 1..1 | Link to Patient                                                                                                        |
| effectiveDateTime       | 1..1 | The date and time the reading took place                                                                                                 |
| performer         | 0..* | Either<br>- use the identifier part of Reference data type to hold the identifier of the practitioner<br>- use the display part of the Reference data type to hold the name of the practitioner<br>- use the reference to point to a CareConnect-Practitioner-1<br>- use the reference to point to the Organization (pharmacy) |
| valueQuantity       | 0..1 | The weight recorded in kilogrammes                                                                                                   |
| dataAbsentReason      | 0..1 | An optional reason why the data is absent                                                                                                |
| comment         | 0..1 | Any additional comments                                                                                                      |
| bodySite          | 0..1 | Optional body site of reading                                                                                                    |                                |

### Weight Observation Example ###
{% include note.html content="These examples have not been clinically assured against Digital Medicines use cases.<br/>Examples are illustrative only." %}

```
<!--<xml>--> 
<Observation xmlns="http://hl7.org/fhir">
	<id value="dbbad20f-e696-405e-8c98-be0cdcc5406c"/>
	<meta>
		<!--claims conformance to CareConnect-Observation-1-->
		<profile value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Observation-1"/>
	</meta>
	<!--fixed value for status-->
	<status value="final"/>
	<!--fixed value for category-->
	<category>
		<coding>
			<system value="http://hl7.org/fhir/observation-category"/>
			<code value="vital-signs"/>
			<display value="Vital Signs"/>
		</coding>
	</category>
	<!--fixed values for code-->
	<code>
		<coding>
			<system value="http://loinc.org"/>
			<code value="29463-7"/>
			<display value="Body weight"/>
		</coding>
		<coding>
			<system value="http://snomed.info/sct"/>
			<code value="27113001 "/>
			<display value="Body weight"/>
		</coding>
	</code>
	<!--link to patient-->
	<subject>
		<reference value="Patient/4f78d392-c9e0-4f1f-9ab6-57d387838690"/>
	</subject>
	<!--date time when reading occurred-->
	<effectiveDateTime value="2018-10-04T14:17:59+01:00"/>
	<!--the performer-->
	<performer>
		<reference value="Performer/2360aba6-8561-4a22-bbbf-afc08e750146"/>
	</performer>
	<performer>
		<reference value="Organization/cd5f7770-6249-4f5d-ad8e-d0bb1446a4d9"/>
	</performer>
	<!--the reading-->
	<valueQuantity>
		<value value="82.7"/>
		<unit value="kg"/>
		<system value="http://unitsofmeasure.org"/>
	</valueQuantity>
</Observation>
<!--</xml>-->
```
<a href="explore_observations.html">Back to top of page</a>

## Oxygen Saturation Observation ##

The coded form of each oxygen saturation reading follows the codes and structure for [CareConnect-OxygenSaturation-Observation-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-OxygenSaturation-Observation-1).

| CareConnect-Observation-1 element | Cardinality | Notes                                                                                                            |
|-------------------------------------|-------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| meta.profile        | 1..1    | Claim conformance to ‘https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-OxygenSaturation-Observation-1’                                                                       |
| status          | 1..1    | Fixed to final                                                                                                         |
| category          | 1..1    | Fixed as per profile                                                                                                       |
| code            | 1..1    | Loinc slice – fixed as per profile<br>SNOMED slice – fixed as per profile                                                                                      |
| subject           | 1..1    | Link to Patient                                                                                                          |
| effectiveDateTime       | 1..1    | The date and time the reading took place                                                                                                 |
| performer         | 0..*    | Either <br>- use the identifier part of Reference data type to hold the identifier of the practitioner<br>- use the display part of the Refer4ence data type to hold the name of the practitioner<br>- use the reference to point to a CareConnect-Practitioner-1<br>- use the reference to point to the Organization (pharmacy) |
| valueQuantity         | 0..1    | The temperature recorded in percent                                                                                                  |
| dataAbsentReason        | 0..1    | An optional reason why the data is absent                                                                                                |
| comment           | 0..1    | Any additional comments                                                                                                      |
| bodySite          | 0..1    | Optional body site of reading                                                                                                    |

### Oxygen Saturation Observation Example ###
{% include note.html content="These examples have not been clinically assured against Digital Medicines use cases.<br/>Examples are illustrative only." %}

```
<!--<xml>--> 
<Observation xmlns="http://hl7.org/fhir">
	<id value="35a1483b-4d04-4907-9f4e-c69ae409a1ea"/>
	<meta>
		<!--claims conformance to CareConnect-OxygenSaturation-Observation-1-->
		<profile value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-OxygenSaturation-Observation-1"/>
	</meta>
	<!--fixed to final-->
	<status value="final"/>
	<!--fixed value for category-->
	<category>
		<coding>
			<system value="http://hl7.org/fhir/observation-category"/>
			<code value="vital-signs"/>
			<display value="Vital Signs"/>
		</coding>
	</category>
	<!--fixed values for code-->
	<code>
		<coding>
			<system value="http://loinc.org"/>
			<code value="59408-5"/>
			<display value="Oxygen saturation in Arterial blood by Pulse oximetry"/>
		</coding>
		<coding>
			<system value="http://snomed.info/sct"/>
			<code value="103228002"/>
			<display value="Hemoglobin saturation with oxygen"/>
		</coding>
	</code>
	<!--link to patient-->
	<subject>
		<reference value="Patient/4f78d392-c9e0-4f1f-9ab6-57d387838690"/>
	</subject>
	<effectiveDateTime value="2018-10-04T14:17:59+01:00"/>
	<!--practitioner-->
	<performer>
		<reference value="Performer/2360aba6-8561-4a22-bbbf-afc08e750146"/>
	</performer>
	<performer>
		<reference value="Organization/cd5f7770-6249-4f5d-ad8e-d0bb1446a4d9"/>
	</performer>
	<!--the reading-->
	<valueQuantity>
		<value value="93"/>
		<unit value="%"/>
		<system value="http://unitsofmeasure.org"/>
	</valueQuantity>
</Observation>
<!--</xml>-->
```
<a href="explore_observations.html">Back to top of page</a>

## Pain Score Observation ##

The coded form of each pain score reading follows the codes and structure for [CareConnect-Observation-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Observation-1).

| CareConnect-Observation-1 element | Cardinality | Notes                                                                                                             |
|-------------------------------------|-------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| meta.profile        | 1..1    | Claim conformance to ‘https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Observation-1’                                                                             |
| status          | 1..1    | Fixed to final                                                                                                          |
| code            | 1..1    | Fixed as demonstrated in example below                                                                                                  |
| subject           | 1..1    | Link to Patient                                                                                                         |
| effectiveDateTime       | 1..1    | The date and time the reading took place                                                                                                |
| performer         | 0..*    | Either<br>- use the identifier part of Reference data type to hold the identifier of the practitioner<br>- use the display part of the Reference data type to hold the name of the practitioner<br>- use the reference to point to a CareConnect-Practitioner-1<br>- use the reference to point to the Organization (pharmacy) |
| valueQuantity         | 0..1    | The recorded pain score value                                                                                                     |
| dataAbsentReason        | 0..1    | An optional reason why the data is absent                                                                                                 |
| comment           | 0..1    | Any additional comments                                                                                                       |
| method          | 1..1    | The pain scale used                                                                                                       | 

### Pain Score Observation Example ###
{% include note.html content="These examples have not been clinically assured against Digital Medicines use cases.<br/>Examples are illustrative only." %}

```
<!--<xml>-->
<Observation xmlns="http://hl7.org/fhir">
	<id value="dbbad20f-e696-405e-8c98-be0cdcc5406c"/>
	<meta>
		<!--claims conformance to CareConnect-BodyTemperature-Observation-1-->
		<profile value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Observation-1"/>
	</meta>
	<!--fixed value for status-->
	<status value="final"/>
	<!--fixed values for code-->
	<code>
		<coding>
			<system value="http://snomed.info/sct"/>
			<code value="225908003"/>
			<display value="Pain score"/>
		</coding>
	</code>
	<!--link to patient-->
	<subject>
		<reference value="Patient/4f78d392-c9e0-4f1f-9ab6-57d387838690"/>
	</subject>
	<!--date time when reading occurred-->
	<effectiveDateTime value="2018-10-04T14:17:59+01:00"/>
	<!--the performer-->
	<performer>
		<reference value="Performer/2360aba6-8561-4a22-bbbf-afc08e750146"/>
	</performer>
	<performer>
		<reference value="Organization/cd5f7770-6249-4f5d-ad8e-d0bb1446a4d9"/>
	</performer>
	<!--the reading-->
	<valueQuantity>
		<value value="4"/>
	</valueQuantity>
	<method>
		<text value="Verbal Rating Scale"/>
	</method>
</Observation>
<!--</xml>-->
```
<a href="explore_observations.html">Back to top of page</a>

## Level of Consciousness Observation ##

The coded form of each Level of Consciousness reading follows the codes and structure the codes and structure for [CareConnect-ACVPU-Observation-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-ACVPU-Observation-1).

| CareConnect-Observation-1 element | Cardinality | Notes                                                                                                             |
|-------------------------------------|-------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| meta.profile        | 1..1    | Claim conformance to ‘https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-ACVPU-Observation-1’                                                                           |
| status          | 1..1    | Fixed to final                                                                                                          |
| code            | 1..1    | SNOMED slice – fixed as per profile                                                                                                   |
| subject           | 1..1    | Link to Patient                                                                                                         |
| effectiveDateTime       | 1..1    | The date and time the reading took place                                                                                                |
| performer         | 0..*    | Either<br>- use the identifier part of Reference data type to hold the identifier of the practitioner<br>- use the display part of the Reference data type to hold the name of the practitioner<br>- use the reference to point to a CareConnect-Practitioner-1<br>- use the reference to point to the Organization (pharmacy) |
| valueCodeableConcept      | 0..1    | The Consciousness recorded in percent – one of<br>- alert<br>- confusion<br>- voice<br>- pain<br>- unresponsive                                                                        |
| dataAbsentReason        | 0..1    | An optional reason why the data is absent                                                                                                 |
| comment           | 0..1    | Any additional comments                                                                                                       |
| bodySite          | 0..1    | Optional body site of reading                                                                                                     |

### Level of Consciousness Observation Example ###
{% include note.html content="These examples have not been clinically assured against Digital Medicines use cases.<br/>Examples are illustrative only." %}

```
<!--<xml>-->
<Observation xmlns="http://hl7.org/fhir">
	<id value="dbbad20f-e696-405e-8c98-be0cdcc5406c"/>
	<meta>
		<!--claims conformance to CareConnect-ACVPU-Observation-1-->
		<profile value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-ACVPU-Observation-1"/>
	</meta>
	<!--fixed value for status-->
	<status value="final"/>
	<!--fixed values for code-->
	<code>
		<coding>
			<system value="http://snomed.info/sct"/>
			<code value="1104441000000107"/>
			<display value="ACVPU (Alert Confusion Voice Pain Unresponsive) scale score"/>
		</coding>
	</code>
	<!--link to patient-->
	<subject>
		<reference value="Patient/4f78d392-c9e0-4f1f-9ab6-57d387838690"/>
	</subject>
	<!--date time when reading occurred-->
	<effectiveDateTime value="2018-10-04T14:17:59+01:00"/>
	<!--the performer-->
	<performer>
		<reference value="Performer/2360aba6-8561-4a22-bbbf-afc08e750146"/>
	</performer>
	<performer>
		<reference value="Organization/cd5f7770-6249-4f5d-ad8e-d0bb1446a4d9"/>
	</performer>
	<!--the reading-->
	<valueCodeableConcept>
		<code>
			<coding>
				<code value="voice"/>
			</coding>
		</code>
	</valueCodeableConcept>
</Observation>
<!--</xml>-->
```
<a href="explore_observations.html">Back to top of page</a>

## Respiratory Rate Observation ##

The coded form of each respiratory rate reading follows the codes and structure for [CareConnect-RespiratoryRate-Observation-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-RespiratoryRate-Observation-1).

| CareConnect-Observation-1 element | Cardinality | Notes                                                                                                             |
|-------------------------------------|-------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| meta.profile        | 1..1    | Claim conformance to ‘https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-RespiratoryRate-Observation-1’                                                                       |
| status          | 1..1    | Fixed to final                                                                                                          |
| category          | 1..1    | Fixed as per profile                                                                                                        |
| code            | 1..1    | Loinc slice – fixed as per profile<br>SNOMED slice – fixed as per profile                                                                                     |
| subject           | 1..1    | Link to Patient                                                                                                         |
| effectiveDateTime       | 1..1    | The date and time the reading took place                                                                                                |
| performer         | 0..*    | Either<br>- use the identifier part of Reference data type to hold the identifier of the practitioner<br> - use the display part of the Reference data type to hold the name of the practitioner<br>- use the reference to point to a CareConnect-Practitioner-1<br> - use the reference to point to the Organization (pharmacy) |
| valueQuantity         | 0..1    | The respiratory rate recorded in /min                                                                                                 |
| dataAbsentReason        | 0..1    | An optional reason why the data is absent                                                                                                 |
| comment           | 0..1    | Any additional comments                                                                                                       |
| bodySite          | 0..1    | Optional body site of reading                                                                                                     |

### Respiratory Rate Observation Example ###
{% include note.html content="These examples have not been clinically assured against Digital Medicines use cases.<br/>Examples are illustrative only." %}

```
<!--<xml>-->
<Observation xmlns="http://hl7.org/fhir">
	<id value="3a3fce15-32d6-4911-86f9-6f849066e0c1"/>
	<meta>
		<profile value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-RespiratoryRate-Observation-1"/>
	</meta>
	<status value="final"/>
	<category>
		<coding>
			<system value="http://hl7.org/fhir/observation-category"/>
			<code value="vital-signs"/>
			<display value="Vital Signs"/>
		</coding>
	</category>
	<code>
		<coding>
			<system value="http://loinc.org"/>
			<code value="9279-1"/>
			<display value="Respiratory Rate"/>
		</coding>
		<coding>
			<system value="http://snomed.info/sct"/>
			<code value="86290005"/>
			<display value="Respiratory rate"/>
		</coding>
	</code>
	<subject>
		<reference value="Patient/4f78d392-c9e0-4f1f-9ab6-57d387838690"/>
	</subject>
	<effectiveDateTime value="2018-10-04T14:17:59+01:00"/>
	<performer>
		<reference value="Performer/2360aba6-8561-4a22-bbbf-afc08e750146"/>
	</performer>
	<performer>
		<reference value="Organization/cd5f7770-6249-4f5d-ad8e-d0bb1446a4d9"/>
	</performer>
	<valueQuantity>
		<value value="21"/>
		<unit value="/min"/>
		<system value="http://unitsofmeasure.org"/>
	</valueQuantity>
</Observation>
<!--</xml>-->
```
<a href="explore_observations.html">Back to top of page</a>

## Air or Oxygen Observation ##

| CareConnect-Observation-1 element | Cardinality | Notes                                                                                                            |
|-------------------------------------|-------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| meta.profile        | 1..1    | Claim conformance to ‘https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Observation-1’                                                                            |
| status          | 1..1    | Fixed to final                                                                                                         |
| code            | 1..1    | Use the text element of CodeableConcept to indicate an 'Air or Oxygen Observation'                                                                                 |
| subject           | 1..1    | Link to Patient                                                                                                        |
| effectiveDateTime       | 1..1    | The date and time the reading took place                                                                                                 |
| performer         | 0..*    | Either<br>- use the identifier part of Reference data type to hold the identifier of the practitioner<br>- use the display part of the Reference data type to hold the name of the practitioner<br>- use the reference to point to a CareConnect-Practitioner-1<br>- use the reference to point to the Organization (pharmacy) |
| valueCodeableConcept      | 0..1    | One of<br> - 722742002 ‘Breathing room air’ OR<br> - 371825009 ‘Patient on oxygen’ OR<br> - 315041000 ‘High concentration oxygen therapy (procedure)’ OR <br>- 9999016 ‘High flow oxygen therapy (procedure)’                                        |
| dataAbsentReason        | 0..1    | An optional reason why the data is absent                                                                                                |
| comment           | 0..1    | Any additional comments                                                                                                      |
                                                                                                                                                                                                                                                                                                               
### Air or Oxygen Observation Example ###
{% include note.html content="These examples have not been clinically assured against Digital Medicines use cases.<br/>Examples are illustrative only." %}

```
<!--<xml>-->
<Observation xmlns="http://hl7.org/fhir">
	<id value="3a3fce15-32d6-4911-86f9-6f849066e0c1"/>
	<meta>
		<profile value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Observation-1"/>
	</meta>
	<status value="final"/>
	<code>
		<text value=”Air or Oxygen Observation”>
	</code>
	<subject>
		<reference value="Patient/4f78d392-c9e0-4f1f-9ab6-57d387838690"/>
	</subject>
	<effectiveDateTime value="2018-10-04T14:17:59+01:00"/>
	<performer>
		<reference value="Performer/2360aba6-8561-4a22-bbbf-afc08e750146"/>
	</performer>
	<performer>
		<reference value="Organization/cd5f7770-6249-4f5d-ad8e-d0bb1446a4d9"/>
	</performer>
	<valueCodeableConcept>
		<system value="http://snomed.info/sct"/>
		<code value="722742002"/>
		<display value="Breathing room air"/>
	</valueCodeableConcept >
</Observation>
<!--</xml>-->
```
<a href="explore_observations.html">Back to top of page</a>

## NEWS2 Score Observation ##

The coded form of each NEWS2 observation follows the code and structure for [CareConnect-Observation-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Observation-1).

| CareConnect-Observation-1 element | Cardinality | Notes                                                                                                                                                                                                                                                                                   |
|-------------------------------------|-------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| meta.profile        | 1..1    | Claim conformance to ‘https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Observation-1’                                                                                                                                                                                                                                                   |
| status          | 1..1    | Fixed to final                                                                                                                                                                                                                                                                                |
| category          | 1..1    | Fixed as demonstrated in example below                                                                                                                                                                                                                                                                        |
| code            | 1..1    | Fixed as demonstrated in example below                                                                                                                                                                                                                                                                        |
| subject           | 1..1    | Link to Patient                                                                                                                                                                                                                                                                               |
| effectiveDateTime       | 1..1    | The date and time the reading took place                                                                                                                                                                                                                                                                      |
| performer         | 0..*    | Either<br>- use the identifier part of Reference data type to hold the identifier of the practitioner<br>- use the display part of the Reference data type to hold the name of the practitioner<br>- use the reference to point to a CareConnect-Practitioner-1<br>- use the reference to point to the Organization (pharmacy)                                                                                                                                                                        |
| valueQuantity         | 0..1    | The NEWS2 score recorded                                                                                                                                                                                                                                                                            |
| related         | 0..*    | Links to the Observations that make up the NEWS2 score                                                                                                                                                                                                                                                                  |
| component         | 0..*    | Components detailing the sub-score – as demonstrated in example below.<br>The values for the sub-score codes are:<br>- 1104351000000103 ‘Royal College of Physicians NEWS2 (National Early Warning Score 2) - pulse score’<br>- 1104311000000102 ‘Royal College of Physicians NEWS2 (National Early Warning Score 2) - oxygen saturation scale 1 score’<br>- 1104331000000105 ‘Royal College of Physicians NEWS2 (National Early Warning Score 2) - air or oxygen score’<br>- 1104371000000107 ‘Royal College of Physicians NEWS2 (National Early Warning Score 2) - temperature score’<br>- 1104341000000101 ‘Royal College of Physicians NEWS2 (National Early Warning Score 2) - systolic blood pressure score’<br>- 1104361000000100 ‘Royal College of Physicians NEWS2 (National Early Warning Score 2) - consciousness score’ |

### NEWS2 Score Observation Example ###
{% include note.html content="These examples have not been clinically assured against Digital Medicines use cases.<br/>Examples are illustrative only." %}

```
<!--<xml>-->
<Observation>
	<id value="21344a45-2660-45d1-9fb3-49e54d14b662"/>
	<meta>
		<profile value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Observation-1"/>
	</meta>
	<identifier>
		<system value="https://tools.ietf.org/html/rfc4122"/>
		<value value="7188c7ad-7802-4d43-9775-4d9d684600d5"/>
	</identifier>
	<status value="final"/>
	<category>
		<coding>
			<system value="http://terminology.hl7.org/CodeSystem/observation-category"/>
			<code value="survey"/>
			<display value="Survey"/>
		</coding>
	</category>
	<code>
		<coding>
			<system value="http://snomed.info/sct"/>
			<code value="1104051000000101"/>
			<display value="Royal College of Physicians NEWS2 (National Early Warning Score 2) total score"/>
		</coding>
	</code>
	<subject>
		<reference value="Patient/ad2c58ab-ffab-4366-9c76-b0322e22e881"/>
	</subject>
	<effectiveDateTime value="2018-10-04T14:17:59+01:00"/>
	<performer>
		<reference value="Performer/7096e518-2638-4c00-ab0e-504c20cd50b6"/>
	</performer>
	<performer>
		<reference value="Organization/25d5ad55-5657-4cbe-9b8b-2e993f19286e"/>
	</performer>
	<valueQuantity>
		<value value="6"/>
		<system value="http://unitsofmeasure.org"/>
		<code value="score"/>
	</valueQuantity>
	<related>
		<type value="derived-from"/>
		<target>
			<reference value="Observation/fc6c6fa5-d8e8-4634-a19a-985325077cb2"/>
		</target>
	</related>
	<related>
		<type value="derived-from"/>
		<target>
			<reference value="Observation/638c6821-eb51-4f1b-b8c0-5269d1df9b7c"/>
		</target>
	</related>
	<related>
		<type value="derived-from"/>
		<target>
			<reference value="Observation/5a1625e8-938e-4c19-9d3e-a235bfb4b37d"/>
		</target>
	</related>
	<related>
		<type value="derived-from"/>
		<target>
			<reference value="Observation/c756fd32-f04e-45a9-b02f-2461ed53c736"/>
		</target>
	</related>
	<related>
		<type value="derived-from"/>
		<target>
			<reference value="Observation/1a1273f4-dd78-4bb4-bb98-ed6456caa2a2"/>
		</target>
	</related>
	<related>
		<type value="derived-from"/>
		<target>
			<reference value="Observation/f0d26102-3a50-4993-9203-6089b625fc2f"/>
		</target>
	</related>
	<related>
		<type value="derived-from"/>
		<target>
			<reference value="Observation/dbf6ec86-ebd7-4490-8586-596328519ed2"/>
		</target>
	</related>
	<!-- Respiratory Rate Sub-Score -->
	<component>
		<code>
			<coding>
				<system value="http://snomed.info/sct"/>
				<code value="1104301000000104"/>
				<display value="Royal College of Physicians NEWS2 (National Early Warning Score 2) - respiration rate score"/>
			</coding>
		</code>
		<valueQuantity>
			<value value="2"/>
			<system value="http://unitsofmeasure.org"/>
			<code value="score"/>
		</valueQuantity>
	</component>
	<!-- Pulse Sub-Score -->
	<component>
		<code>
			<coding>
				<system value="http://snomed.info/sct"/>
				<code value="1104351000000103"/>
				<display value="Royal College of Physicians NEWS2 (National Early Warning Score 2) - pulse score"/>
			</coding>
		</code>
		<valueQuantity>
			<value value="1"/>
			<system value="http://unitsofmeasure.org"/>
			<code value="score"/>
		</valueQuantity>
	</component>
	<!-- Oxygen Saturation scale 1 Sub-Score -->
	<component>
		<code>
			<coding>
				<system value="http://snomed.info/sct"/>
				<code value="1104311000000102"/>
				<display value="Royal College of Physicians NEWS2 (National Early Warning Score 2) - oxygen saturation scale 1 score"/>
			</coding>
		</code>
		<valueQuantity>
			<value value="2"/>
			<system value="http://unitsofmeasure.org"/>
			<code value="score"/>
		</valueQuantity>
	</component>
	<!-- Air or Oxygen Sub-Score -->
	<component>
		<code>
			<coding>
				<system value="http://snomed.info/sct"/>
				<code value="1104331000000105"/>
				<display value="Royal College of Physicians NEWS2 (National Early Warning Score 2) - air or oxygen score"/>
			</coding>
		</code>
		<valueQuantity>
			<value value="0"/>
			<system value="http://unitsofmeasure.org"/>
			<code value="score"/>
		</valueQuantity>
	</component>
	<!-- Temperature Sub-Score -->
	<component>
		<code>
			<coding>
				<system value="http://snomed.info/sct"/>
				<code value="1104371000000107"/>
				<display value="Royal College of Physicians NEWS2 (National Early Warning Score 2) - temperature score"/>
			</coding>
		</code>
		<valueQuantity>
			<value value="1"/>
			<system value="http://unitsofmeasure.org"/>
			<code value="score"/>
		</valueQuantity>
	</component>
	<!-- Systolic Blood Pressure Sub-Score -->
	<component>
		<code>
			<coding>
				<system value="http://snomed.info/sct"/>
				<code value="1104341000000101"/>
				<display value="Royal College of Physicians NEWS2 (National Early Warning Score 2) - systolic blood pressure score"/>
			</coding>
		</code>
		<valueQuantity>
			<value value="0"/>
			<system value="http://unitsofmeasure.org"/>
			<code value="score"/>
		</valueQuantity>
	</component>
	<!--  Consciousness Sub-Score -->
	<component>
		<code>
			<coding>
				<system value="http://snomed.info/sct"/>
				<code value="1104361000000100"/>
				<display value="Royal College of Physicians NEWS2 (National Early Warning Score 2) - consciousness score"/>
			</coding>
		</code>
		<valueQuantity>
			<value value="0"/>
			<system value="http://unitsofmeasure.org"/>
			<code value="score"/>
		</valueQuantity>
	</component>
</Observation>
<!--</xml>-->
```
<a href="explore_observations.html">Back to top of page</a>
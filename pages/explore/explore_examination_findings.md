---
title: Examination findings - NOW RETIRED
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_examination_findings.html
summary: "Gives information about examination findings"
---

{% include warning.html content="The Minor Illness use case is now retired and you cannot implement it." %}

{% include custom/section.warnbanner.html %}

## Examination Findings Section Content ##
This is an examination findings record entry. <br/><br/>There may be 0 TO MANY record entry/entries under a section. Each record entry is made up of a number of elements or data items.

- [Height/Length](explore_examination_findings.html#heightlength-observation)
- [Weight](explore_examination_findings.html#weight-observation)
- [BMI](explore_examination_findings.html#bmi-observation)
- [Blood Pressure](explore_examination_findings.html#blood-pressure-observation) 
- [Heart Rate](explore_examination_findings.html#heart-rate-observation)
- [Temperature](explore_examination_findings.html#temperature-observation)
- [Oxygen Saturation](explore_examination_findings.html#oxygen-saturation-observation)
- [Pain Score](explore_examination_findings.html#pain-score-observation)
- [Level of Consciousness](explore_examination_findings.html#level-of-consciousness-observation)
- [Respiratory Rate](explore_examination_findings.html#respiratory-rate-observation)
- [Air or Oxygen](explore_examination_findings.html#air-or-oxygen-observation)
- [National early warning score (NEWS 2)](explore_examination_findings.html#news2-score-observation)


## Example Section ##

{% include note.html content="These examples have not been clinically assured against Digital Medicines use cases.<br/>Examples are illustrative only." %}

```
<!--<xml>-->
<!--Examination findings-->
<section>
	<title value="Examination findings"/>
	<code>
		<coding>
			<system value="http://snomed.info/sct"/>
			<code value="715851000000102"/>
			<display value="Examination findings"/>
		</coding>
	</code>
	<text>
		<status value="additional"/>
		<div xmlns="http://www.w3.org/1999/xhtml">
			<table width="100%">
				Examination Finding Date: 2021-09-04T12:35
				<tbody>
					<tr>
						<th>Observation</th>
						<th>Performed</th>
						<th>Reading</th>
					</tr>
					<tr>
						<td>Height/Length</td>
						<td>1.7 m</td>
					</tr>	
					<tr>
						<td>Weight</td>
						<td>82.5 kg</td>
					</tr>	
					<tr>
						<td>BMI</td>
						<td>22</td>
					</tr>			
					<tr>
						<td>Blood pressure</td>
						<td>84/120 mmHg</td>
					</tr>					
					<tr>
						<td>Heart rate</td>
						<td>92 /min</td>
					</tr>
					<tr>
						<td>Temperature</td>
						<td>37.5 C</td>
					</tr>		
					<tr>
						<td>Oxygen saturation</td>
						<td>98%</td>
					</tr>		
					<tr>
						<td>Pain score</td>
						<td>6</td>
					</tr>
					<tr>
						<td>Level of Consciousness</td>
						<td>voice</td>
					</tr>					
					<tr>
						<td>Respiration rate</td>
						<td>38 /min</td>
					</tr>
					<tr>
						<td>Air or oxygen</td>
						<td>Air</td>
					</tr>
					<tr>
						<td>National early warning score (NEWS 2)</td>
						<td>6</td>
					</tr>
				</tbody>
			</table>
		</div>
	</text>
</section>

<!--</xml>-->
```

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
| bodySite          | 0..1  | <442083009 - Anatomical or acquired body structure                                                                                                   |
| component systolic      |     |                                                                                                             |
| - code            | 1..1  | SNOMED <<271649006 Systolic blood pressure                                                                                   |
| - valueQuantity         | 0..1  | Recorded as per the profile                                                                                                   |
| component diastolic       |     |                                                                                                             |
| - code            | 1..1  | SNOMED <<271650006 Diastolic blood pressure                                                                                   |
| - valueQuantity         | 0..1  | Recorded as per the profile                                                                                                   |


###  Blood Pressure Observation Example ###
{% include note.html content="These examples have not been clinically assured against Digital Medicines use cases.<br/>Examples are illustrative only." %}

```
<!--<xml>-->
<Observation xmlns="http://hl7.org/fhir">
	<id value="e0818279-51da-4e82-ab44-7798cdab8ccc"/>
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
				<system value="http://snomed.info/sct"/>
				<code value="271649006"/>
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
				<system value="http://snomed.info/sct"/>
				<code value="271650006"/>
				<display value="Diastolic blood pressure"/>
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
<a href="explore_examination_findings.html">Back to top of page</a>

## Temperature Observation ##

The coded form of each temperature reading follows follows the codes and structure for [CareConnect-BodyTemperature-Observation-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-BodyTemperature-Observation-1)

| CareConnect-BodyTemperature-Observation-1   element | Cardinality | Notes                                                                                                                                                                                                                                                                                                                                  |
|-----------------------------------------------------|-------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| meta.profile                                        | 1..1        | Claim conformance to   ‘https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-BodyTemperature-Observation-1’                                                                                                                                                                                                                    |
| status                                              | 1..1        | Fixed to final                                                                                                                                                                                                                                                                                                                         |
| category                                            | 1..1        | Fixed as per profile                                                                                                                                                                                                                                                                                                                   |
| code                                                | 1..1        | SNOMED CT <<386725007 - Body temperature                                                                                                                   |
| subject                                             | 1..1        | Link to Patient                                                                                                                                                                                                                                                                                                                        |
| effectiveDateTime                                   | 1..1        | The date and time the reading took place                                                                                                                                                                                                                                                                                               |
| valueQuantity                                       | 0..1        | The temperature recorded in Celsius                                                                                                                                                                                                                                                                                                    |

### Temperature Observation Example ###  
{% include note.html content="These examples have not been clinically assured against Digital Medicines use cases.<br/>Examples are illustrative only." %}

```
<!--<xml>-->
<Observation xmlns="http://hl7.org/fhir">
	<id value="b8287484-53eb-4ae4-b040-c56fcb58df8f"/>
	<meta>
		<!--claims conformance to CareConnect-BodyTemperature-Observation-1-->
		<profile value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-BodyTemperature-Observation-1"/>
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
			<system value="http://snomed.info/sct"/>
			<code value="386725007"/>
			<display value="Body temperature"/>
		</coding>
	</code>
	<!--link to patient-->
	<subject>
		<reference value="Patient/4f78d392-c9e0-4f1f-9ab6-57d387838690"/>
	</subject>
	<!--date time when reading occurred-->
	<effectiveDateTime value="2018-10-04T14:17:59+01:00"/>
	<!--the reading-->
	<valueQuantity>
		<value value="38.5"/>
		<unit value="Cel"/>
		<system value="http://unitsofmeasure.org"/>
	</valueQuantity>
</Observation>
<!--</xml>-->
```
<a href="explore_examination_findings.html">Back to top of page</a>

## Heart Rate Observation ## 

The coded form of each pulse rate reading follows the codes and structure for [CareConnect-HeartRate-Observation-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-HeartRate-Observation-1).

| CareConnect-Observation-1 element | Cardinality | Notes                                                                                                          |
|-------------------------------------|-------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| meta.profile        | 1..1    | Claim conformance to ‘https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-HeartRate-Observation-1’                                                                      |
| status          | 1..1    | Fixed to final                                                                                                       |
| category          | 1..1    | Fixed as per profile                                                                                                     |
| code            | 1..1    | SNOMED slice – fixed as per profile                                                 |
| subject           | 1..1    | Link to Patient                                                                                                      |
| effectiveDateTime       | 1..1    | The date and time the reading took place                                                                                             |
| valueQuantity         | 0..1    | The heart rate recorded in beats per minute (/min)                                                                                           |

### Heart Rate Observation Example ###
{% include note.html content="These examples have not been clinically assured against Digital Medicines use cases.<br/>Examples are illustrative only." %}

```
<!--<xml>--> 
<Observation xmlns="http://hl7.org/fhir">
	<id value="ce6a7522-8285-4e0d-9d93-c928d21f512b"/>
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
			<system value="http://snomed.info/sct"/>
			<code value="364075005"/>
			<display value="Heart rate"/>
		</coding>
	</code>
	<!--link to patient-->
	<subject>
		<reference value="Patient/4f78d392-c9e0-4f1f-9ab6-57d387838690"/>
	</subject>
	<!--the date and time of the reading-->
	<effectiveDateTime value="2018-10-04T14:17:59+01:00"/>
	<!--the pulse rate reading-->
	<valueQuantity>
		<value value="95"/>
		<unit value="/min"/>
		<system value="http://unitsofmeasure.org"/>
	</valueQuantity>
</Observation>
<!--</xml>-->
```
<a href="explore_examination_findings.html">Back to top of page</a>

## Height/Length Observation ##

The coded form of each height reading follows the codes and structure for [CareConnect-Observation-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Observation-1).

| CareConnect-VitalSigns-Observation-1 element | Cardinality | Notes                                                                                                          |
|-------------------------------------|-------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| meta.profile        | 1..1    | Claim conformance to ‘https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-VitalSigns-Observation-1’                                                                          |
| status          | 1..1    | Fixed to final                                                                                                       |
| category          | 1..1    | Fixed as demonstrated in example below                                   |
| code            | 1..1    | SNOMED CT: - 50373000 - Body height measure (observable entity) OR 248334005 - Length of body (observable entity)        |
| subject           | 1..1    | Link to Patient                                                                                                      |
| valueQuantity         | 0..1    | The height recorded in metres or centimetres                                                                                             |
   
### Height/Length Observation Example ###
{% include note.html content="These examples have not been clinically assured against Digital Medicines use cases.<br/>Examples are illustrative only." %}

```
<!--<xml>-->  
<Observation xmlns="http://hl7.org/fhir">
	<id value="bf235b3a-e513-47d0-a76e-b2390aff655b"/>
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
			<system value="http://snomed.info/sct"/>
			<code value="50373000"/>
			<display value="Body height"/>
		</coding>
	</code>
	<!-- for Length the code is
	<code>
		<coding>
			<system value="http://snomed.info/sct"/>
			<code value="248334005"/>
			<display value="Length of body"/>
		</coding>
	</code> -->	
	<!--link to patient-->
	<subject>
		<reference value="Patient/4f78d392-c9e0-4f1f-9ab6-57d387838690"/>
	</subject>
	<!--date time when reading occurred-->
	<effectiveDateTime value="2018-10-04T14:17:59+01:00"/>
	<!--the reading-->
	<valueQuantity>
		<value value="175"/>
		<unit value="cm"/>
		<system value="http://unitsofmeasure.org"/>
	</valueQuantity>
</Observation>
<!--</xml>-->
```
<a href="explore_examination_findings.html">Back to top of page</a>

## BMI Observation ##

The coded form of each BMI reading follows the codes and structure for [CareConnect-Observation-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Observation-1).

| CareConnect-VitalSigns-Observation-1 element | Cardinality | Notes                                                                                                          |
|-------------------------------------|-------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| meta.profile        | 1..1    | Claim conformance to ‘https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-VitalSigns-Observation-1’                                                                          |
| status          | 1..1    | Fixed to final                                                                                                       |
| category          | 1..1    | Fixed as demonstrated in example below                                   |
| code            | 1..1    | Fixed as demonstrated in example below        |
| subject           | 1..1    | Link to Patient                                                                                                      |
| valueQuantity         | 0..1    | The height recorded in metres or centimetres                                                                                             |
   
### BMI Observation Example ###
{% include note.html content="These examples have not been clinically assured against Digital Medicines use cases.<br/>Examples are illustrative only." %}

```
<!--<xml>-->  
<Observation xmlns="http://hl7.org/fhir">
	<id value="f6db2df2-abe3-4e17-80f8-e5bc06c7f92b"/>
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
			<system value="http://snomed.info/sct"/>
			<code value="60621009"/>
			<display value="Body mass index"/>
		</coding>
	</code>
	<!--link to patient-->
	<subject>
		<reference value="Patient/4f78d392-c9e0-4f1f-9ab6-57d387838690"/>
	</subject>
	<!--date time when reading occurred-->
	<effectiveDateTime value="2018-10-04T14:17:59+01:00"/>
	<!--the reading-->
	<valueQuantity>
		<value value="25"/>
		<unit value="kg/m2"/>
		<system value="http://unitsofmeasure.org"/>
	</valueQuantity>
</Observation>
<!--</xml>-->
```
<a href="explore_examination_findings.html">Back to top of page</a>

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
| valueQuantity       | 0..1 | The weight recorded in kilogrammes                                                                                                   |


### Weight Observation Example ###
{% include note.html content="These examples have not been clinically assured against Digital Medicines use cases.<br/>Examples are illustrative only." %}

```
<!--<xml>--> 
<Observation xmlns="http://hl7.org/fhir">
	<id value="2e96ba1e-49a4-4964-9a54-3b055873fb07"/>
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
			<system value="http://snomed.info/sct"/>
			<code value="27113001"/>
			<display value="Body weight"/>
		</coding>
	</code>
	<!--link to patient-->
	<subject>
		<reference value="Patient/4f78d392-c9e0-4f1f-9ab6-57d387838690"/>
	</subject>
	<!--date time when reading occurred-->
	<effectiveDateTime value="2018-10-04T14:17:59+01:00"/>
	<!--the reading-->
	<valueQuantity>
		<value value="82.7"/>
		<unit value="kg"/>
		<system value="http://unitsofmeasure.org"/>
	</valueQuantity>
</Observation>
<!--</xml>-->
```
<a href="explore_examination_findings.html">Back to top of page</a>

## Oxygen Saturation Observation ##

The coded form of each oxygen saturation reading follows the codes and structure for [CareConnect-OxygenSaturation-Observation-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-OxygenSaturation-Observation-1).

| CareConnect-Observation-1 element | Cardinality | Notes                                                                                                            |
|-------------------------------------|-------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| meta.profile        | 1..1    | Claim conformance to ‘https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-OxygenSaturation-Observation-1’                                                                       |
| status          | 1..1    | Fixed to final                                                                                                         |
| category          | 1..1    | Fixed as per profile                                                                                                       |
| code            | 1..1    | SNOMED slice – fixed as per profile                                                                                      |
| subject           | 1..1    | Link to Patient                                                                                                          |
| effectiveDateTime       | 1..1    | The date and time the reading took place                                                                                                 |
| valueQuantity         | 0..1    | The temperature recorded in percent                                                                                                  |

### Oxygen Saturation Observation Example ###
{% include note.html content="These examples have not been clinically assured against Digital Medicines use cases.<br/>Examples are illustrative only." %}

```
<!--<xml>--> 
<Observation xmlns="http://hl7.org/fhir">
	<id value="e3890ae3-db3e-4104-824c-f9636950866e"/>
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
			<system value="http://snomed.info/sct"/>
			<code value="431314004"/>
			<display value="Peripheral oxygen saturation"/>
		</coding>
	</code>
	<!--link to patient-->
	<subject>
		<reference value="Patient/4f78d392-c9e0-4f1f-9ab6-57d387838690"/>
	</subject>
	<effectiveDateTime value="2018-10-04T14:17:59+01:00"/>
	<!--the reading-->
	<valueQuantity>
		<value value="93"/>
		<unit value="%"/>
		<system value="http://unitsofmeasure.org"/>
	</valueQuantity>
</Observation>
<!--</xml>-->
```
<a href="explore_examination_findings.html">Back to top of page</a>

## Pain Score Observation ##

The coded form of each pain score reading follows the codes and structure for [CareConnect-Observation-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Observation-1).

| CareConnect-Observation-1 element | Cardinality | Notes                                                                                                             |
|-------------------------------------|-------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| meta.profile        | 1..1    | Claim conformance to ‘https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Observation-1’                                                                             |
| status          | 1..1    | Fixed to final                                                                                                          |
| code            | 1..1    | Fixed as demonstrated in example below                                                                                                  |
| subject           | 1..1    | Link to Patient                                                                                                         |
| effectiveDateTime       | 1..1    | The date and time the reading took place                                                                                                |
| valueQuantity         | 0..1    | The recorded pain score value                                                                                                     |

### Pain Score Observation Example ###
{% include note.html content="These examples have not been clinically assured against Digital Medicines use cases.<br/>Examples are illustrative only." %}

```
<!--<xml>-->
<Observation xmlns="http://hl7.org/fhir">
	<id value="f3dc3143-0f3a-49f4-9da8-67a5e1492145"/>
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
	<!--the reading-->
	<valueQuantity>
		<value value="4"/>
	</valueQuantity>
</Observation>
<!--</xml>-->
```
<a href="explore_examination_findings.html">Back to top of page</a>

## Level of Consciousness Observation ##

The coded form of each Level of Consciousness reading follows the codes and structure the codes and structure for [CareConnect-ACVPU-Observation-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-ACVPU-Observation-1).

| CareConnect-Observation-1 element | Cardinality | Notes                                                                                                             |
|-------------------------------------|-------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| meta.profile        | 1..1    | Claim conformance to ‘https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-ACVPU-Observation-1’                                                                           |
| status          | 1..1    | Fixed to final                                                                                                          |
| code            | 1..1    | SNOMED slice – fixed as per profile                                                                                                   |
| subject           | 1..1    | Link to Patient                                                                                                         |
| effectiveDateTime       | 1..1    | The date and time the reading took place                                                                                                |
| valueCodeableConcept      | 0..1    | The Consciousness recorded in percent – one of<br>- alert<br>- confusion<br>- voice<br>- pain<br>- unresponsive                                                                        |


### Level of Consciousness Observation Example ###
{% include note.html content="These examples have not been clinically assured against Digital Medicines use cases.<br/>Examples are illustrative only." %}

```
<!--<xml>-->
<Observation xmlns="http://hl7.org/fhir">
	<id value="a4c394ac-b0d8-44e9-8125-38e7d28c8193"/>
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
<a href="explore_examination_findings.html">Back to top of page</a>

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
| valueQuantity         | 0..1    | The respiratory rate recorded in /min                                                                                                 |

### Respiratory Rate Observation Example ###
{% include note.html content="These examples have not been clinically assured against Digital Medicines use cases.<br/>Examples are illustrative only." %}

```
<!--<xml>-->
<Observation xmlns="http://hl7.org/fhir">
	<id value="771d0d98-7988-4e7b-b0eb-021d094c2b33"/>
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
			<system value="http://snomed.info/sct"/>
			<code value="86290005"/>
			<display value="Respiratory rate"/>
		</coding>
	</code>
	<subject>
		<reference value="Patient/4f78d392-c9e0-4f1f-9ab6-57d387838690"/>
	</subject>
	<effectiveDateTime value="2018-10-04T14:17:59+01:00"/>
	<valueQuantity>
		<value value="21"/>
		<unit value="/min"/>
		<system value="http://unitsofmeasure.org"/>
	</valueQuantity>
</Observation>
<!--</xml>-->
```
<a href="explore_examination_findings.html">Back to top of page</a>

## Air or Oxygen Observation ##

| CareConnect-Observation-1 element | Cardinality | Notes                                                                                                            |
|-------------------------------------|-------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| meta.profile        | 1..1    | Claim conformance to ‘https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Observation-1’                                                                            |
| status          | 1..1    | Fixed to final                                                                                                         |
| code            | 1..1    | Use the text element of CodeableConcept to indicate an 'Air or Oxygen Observation'                                                                                 |
| subject           | 1..1    | Link to Patient                                                                                                        |
| effectiveDateTime       | 1..1    | The date and time the reading took place                                                                                                 |
| valueCodeableConcept      | 0..1    | One of<br> - 722742002 ‘Breathing room air’ OR<br> - 371825009 ‘Patient on oxygen’ OR<br> - 315041000 ‘High concentration oxygen therapy (procedure)’ OR <br>- 9999016 ‘High flow oxygen therapy (procedure)’                                        |

                                                                                                                                                                                                                                                                                                               
### Air or Oxygen Observation Example ###
{% include note.html content="These examples have not been clinically assured against Digital Medicines use cases.<br/>Examples are illustrative only." %}

```
<!--<xml>-->
<Observation xmlns="http://hl7.org/fhir">
	<id value="c4211cc4-1bca-4a95-9fc7-dbd64062c01f"/>
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
	<valueCodeableConcept>
		<system value="http://snomed.info/sct"/>
		<code value="722742002"/>
		<display value="Breathing room air"/>
	</valueCodeableConcept >
</Observation>
<!--</xml>-->
```
<a href="explore_examination_findings.html">Back to top of page</a>

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
| valueQuantity         | 0..1    | The NEWS2 score recorded                                                                                                                                                                                                                                                                            |
| related         | 0..*    | Links to the Observations that make up the NEWS2 score                                                                                                                                                                                                                                                                  |
| component         | 0..*    | Components detailing the sub-score – as demonstrated in example below.<br>The values for the sub-score codes are:<br>- 1104351000000103 ‘Royal College of Physicians NEWS2 (National Early Warning Score 2) - pulse score’<br>- 1104311000000102 ‘Royal College of Physicians NEWS2 (National Early Warning Score 2) - oxygen saturation scale 1 score’<br>- 1104331000000105 ‘Royal College of Physicians NEWS2 (National Early Warning Score 2) - air or oxygen score’<br>- 1104371000000107 ‘Royal College of Physicians NEWS2 (National Early Warning Score 2) - temperature score’<br>- 1104341000000101 ‘Royal College of Physicians NEWS2 (National Early Warning Score 2) - systolic blood pressure score’<br>- 1104361000000100 ‘Royal College of Physicians NEWS2 (National Early Warning Score 2) - consciousness score’ |

### NEWS2 Score Observation Example ###
{% include note.html content="These examples have not been clinically assured against Digital Medicines use cases.<br/>Examples are illustrative only." %}

```
<!--<xml>-->
<Observation>
	<id value="db001012-74ee-4809-962c-e938e3e9dde2"/>
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
	<valueQuantity>
		<value value="6"/>
		<system value="http://unitsofmeasure.org"/>
		<code value="score"/>
	</valueQuantity>
	<related>
		<type value="derived-from"/>
		<target>
			<reference value="Observation/e0818279-51da-4e82-ab44-7798cdab8ccc"/>
		</target>
	</related>
	<related>
		<type value="derived-from"/>
		<target>
			<reference value="Observation/b8287484-53eb-4ae4-b040-c56fcb58df8f"/>
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
<a href="explore_examination_findings.html">Back to top of page</a>


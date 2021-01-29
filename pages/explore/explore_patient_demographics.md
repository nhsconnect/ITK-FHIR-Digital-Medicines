---
title: Patient Demographics Section
keywords:  messaging, sections
tags: [fhir,messaging,section]
sidebar: foundations_sidebar
permalink: explore_patient_demographics.html
summary: "Gives information about the Patient Demographics section"
---
{% include custom/section.warnbanner.html %}


## Patient Demographics Section Content ##
The Patient demographics section contains information about the patient. PRSB Elements should be formatted as subheadings in any HTML sent.

| PATIENT   DEMOGRAPHICS   |                                                                                                            |             |                                                                                                                                                                                                                                                                                                                                       |                                  |                               |
|--------------------------|------------------------------------------------------------------------------------------------------------|-------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------|-------------------------------|
| Data Item                | Description                                                                                                | Cardinality | Values                                                                                                                                                                                                                                                                                                                                | Mandatory/required/     optional | FHIR Target                   |
| Patient name             | The   full name of the patient.                                                                            | 1   ONLY    | The   legal name of the patient. This will normally be volunteered by the patient   or their carer or representative; given by a Patient Demographics Service   (PDS) patient trace, a referral or from the pharmacy system.                                                                                                          | Mandatory                        | Paient.name                   |
| Patient address          | Patient’s   usual place of residence.                                                                      | 1   ONLY    | Sent   in accordance with the NHS Data Dictionary: patient usual address. May be   auto generated from PDS, referral or pharmacy system.                                                                                                                                                                                              | Mandatory                        | Patient.address               |
| Patient telephone number | Telephone   contact details of the patient. To include, e.g., mobile, work and home   number if available. | 0   TO MANY | Both   the actual contact number and its use (work number, home number, mobile   number etc.) should be sent. May be auto generated from PDS, referral or   pharmacy system.                                                                                                                                                          | Required                         | Patient.telecom               |
| Date of birth            | The   date of birth of the patient.                                                                        | 1   ONLY    | The   date of birth will be as precise as possible, but should at least contain a   year. May be auto generated from PDS, referral or pharmacy system.                                                                                                                                                                                | Mandatory                        | Patient.birthDate             |
| NHS number               | The   unique identifier for a patient within the NHS in England and Wales.                                 | 0   TO 1    | Sent as per the NHS Data Dictionary NHS number. Traced   and verified NHS Numbers only should be used i.e. NHS number status indicator   code: value 01. If there is no NHS number then this data item should be   reported as null and other unique identifiers will need to flow.                                                   | Required                         | Patient.identifier(NHSNumber) |
| Sex                      | The   person’s phenotypic sex. Determines how the person will be treated   clinically.                     | 1   ONLY    | Recorded   as per NHS Data Dictionary. Person phenotypic sex is observed by a person,   and is not self-stated:                                                                                                                 1: Male      2: Female      9: Indeterminate (unable to be classified as either male or female)       | Mandatory                        | Patient.gender                |
| Other identifier         | Country   specific or local identifier, e.g., Community Health Index (CHI) in   Scotland.                  | 0   TO MANY | Recorded   as per NHS Data Dictionary: - Local patient identifier, -Local patient   identified (extended), -Health and Care number, -Community Health Index   number.                                                                                                                                                                 | Required                         | Patient.identifier            |


## The sections below are Message specific ##

> **When implementing:**
* Community Pharmacy Consultation Service

Include element(s):

| Data   Item                    | Description                                                                                     | Cardinality | Values      | Mandatory/required/     optional | FHIR Target              |
|--------------------------------|-------------------------------------------------------------------------------------------------|-------------|-------------|----------------------------------|--------------------------|
| Age [Anonymised]| Age of the Patient for whom the referral is being made |  | | Mandatory  | Composition.section.text |


## Example Patient Demographics Section ##

{% include note.html content="These examples have not been clinically assured against Digital Medicines use cases.<br/>Examples are illustrative only." %}

```
<!--<xml>-->
<!-- Patient demographics-->
	<section>
	<title value="Patient demographics"/>
		<code>
			<coding>
				<system value="http://snomed.info/sct"/>
				<code value="886731000000109"/>
				<display value="Patient demographics"/>
			</coding>
		</code>
		<text>
		<status value="additional"/>
		<div xmlns="http://www.w3.org/1999/xhtml">
		<table width="100%">
			<tbody>
			<tr>
			<th>Patient name</th>
			<td>	
					<p>Prefix: Mrs</p>
					<p>Given Name: Julie</p>
					<p>Family Name: Jones</p>
			</td>
		</tr>
		<tr>
			<th>Patient address</th>
			<td>
				<p>Address Line: 22, Brightside Crescent, Overtown</p>
				<p>City: Leeds</p>
				<p>Post Code: LS10 4YU</p>
			</td>
		</tr>
		<tr>
			<th>Patient telephone number</th>
			<td>Telephone contact details of the patient. To include, e.g., mobile, work and home number if available.</td>
		</tr>
		<tr>
			<th>Date of birth</th>
			<td>4 May 1959</td>
		</tr>
		<tr>
			<th>NHS number</th>
			<td>3478526985</td>
		</tr>
		<tr>
			<th>Sex</th>
			<td>Female</td>
		</tr>
		<tr>
			<th>Other identifier</th>
			<td>Country specific or local identifier, e.g., Community Health Index (CHI) in Scotland.</td>
		</tr>
			</tbody>
		</table>
		</div>
		</text>
	<!--reference to further information carried in the patient resource-->
	<entry>
		<reference value="urn:uuid:9589fb37-87a2-48d8-968f-b371429209e3"/>
	</entry>
	</section>
<!--</xml>-->
```
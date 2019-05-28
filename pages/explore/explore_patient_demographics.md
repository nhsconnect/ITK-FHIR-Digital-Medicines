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
			<td>Patient demographics</td>
			<td>Patient details and contact information.</td>
			<td>1 only</td>
			<td>M</td>
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
			<td>Patient name</td>
			<td>The full name of the patient.</td>
			<td>1 only</td>
			<td>M</td>
			<td>The legal name of the patient. This will normally be volunteered by the patient or their carer or representative; given by a Patient Demographics Service (PDS) patient trace, a referral or from the pharmacy system.</td>
		</tr>
		<tr>
			<td>Patient address</td>
			<td>Patient's usual place of residence.</td>
			<td>1 only</td>
			<td>M</td>
			<td>Sent in accordance with the NHS Data Dictionary: patient usual address. May be auto generated from PDS, referral or pharmacy system.</td>
		</tr>
		<tr>
			<td>Patient telephone number</td>
			<td>Telephone contact details of the patient. To include, e.g., mobile, work and home number if available.</td>
			<td>0 to many</td>
			<td>R</td>
			<td>Both the actual contact number and its use (work number, home number, mobile number etc.) should be sent. May be auto generated from PDS, referral or pharmacy system.</td>
		</tr>
		<tr>
			<td>Date of birth</td>
			<td>The date of birth of the patient.</td>
			<td>1 only</td>
			<td>M</td>
			<td>The date of birth will be as precise as possible, but should at least contain a year. May be auto generated from PDS, referral or pharmacy system. This will be in text and carried in the FHIR element <b>Patient.birthDate</b>.</td>
		</tr>
		<tr>
			<td>NHS number</td>
			<td>The unique identifier for a patient within the NHS in England and Wales.</td>
			<td>0 to 1</td> 
			<td>R</td>
			<td>Sent as per the NHS Data Dictionary NHS number. Traced and verified NHS Numbers only should be used i.e. NHS number status indicator code: value 01. If there is no NHS number then this data item should be reported as null and other unique identifiers will need to flow.</td>
		</tr>
		<tr>
			<td>Sex</td>
			<td>The person’s phenotypic sex. Determines how the person will be treated clinically.</td>
			<td>1</td>
			<td>M</td>
			<td>Recorded as per NHS Data Dictionary. Person phenotypic sex is observed by a person, and is not self-stated: 1: Male 2: Female 9: Indeterminate (unable to be classified as either male or female).</td>
		</tr>
		<tr>
			<td>Other identifier</td>
			<td>Country specific or local identifier, e.g., Community Health Index (CHI) in Scotland.</td>
			<td>0 to many</td>
			<td>R</td>
			<td>Recorded as per NHS Data Dictionary: - Local patient identifier, -Local patient identified (extended), -Health and Care number, -Community Health Index number.</td>
		</tr>
		<tr>
		<td colspan="5"><b>* M=Mandatory R=Required O=Optional</b></td>
		</tr>
	</tbody>
</table>

## Example Patient Demographics Section ##

<script src="https://gist.github.com/IOPS-DEV/2e37d0c716ad7f0f23aa5250f8f31ce0.js"></script>







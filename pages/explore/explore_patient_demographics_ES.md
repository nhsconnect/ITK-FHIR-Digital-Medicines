---
title: Patient Demographics Section
keywords:  messaging, sections
tags: [fhir,messaging,section]
sidebar: foundations_sidebar
permalink: explore_patient_demographics_ES.html
summary: "Gives information about the patient"
---
{% include custom/section.warnbanner.html %}


## Patient Demographics Section Content##
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
			<td>The legal name of the patient from the Patient Demographics Service (PDS), or the name volunteered by the patient in text and carried in the FHIR element <b>Patient.name</b> with the <b>Patient.name.use</b> containing the value "official".</td>
		</tr>
		<tr>
			<td>Patient preferred name</td>
			<td>The name by which a patient wishes to be addressed.</td>
			<td>0 to 1</td>
			<td>R</td>
			<td>Not required for Pharmacy to GP communication.</td>
		</tr>
		<tr>
			<td>Patient address</td>
			<td>Patient's usual place of residence.</td>
			<td>1 only</td>
			<td>M</td>
			<td>Sent in accordance with the NHS Data Dictionary: patient usual address. May be auto generated from PDS, referral or pharmacy system. Text and also carried in the FHIR element <b>Patient.address</b></td>
		</tr>
		<tr>
			<td>Patient telephone number</td>
			<td>Telephone contact details of the patient. To include, e.g., mobile, work and home number if available.</td>
			<td>0 to many</td>
			<td>O</td>
			<td>Not required for Pharmacy to GP communication.</td>
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
			<td>Sent as text as per the NHS Data Dictionary NHS number. Traced NHS Numbers only should, be used and the NHS number <b>SHOULD</b> be carried in the FHIR element <b>Patient.identifier</b>.</td>
		</tr>
		<tr>
			<td>Other identifier</td>
			<td>Country specific or local identifier, e.g. Community Health Index (CHI) in Scotland. Two data items: type of identifier and identifier.</td>
			<td>0 to many</td>
			<td>R</td>
			<td>Recorded as per: NHS Data Dictionary - local identifier. The assigning authority should also be supplied along with the country or local identifier. This is carried as text and also carried in the FHIR element <b>Patient.identifier</b>.</td>
		</tr>
		<tr>
			<td>Ethnicity</td>
			<td>The ethnicity of a person as specified by the person.</td>
			<td>0 to 1</td>
			<td>O</td>
			<td>Not required for Pharmacy to GP communication.</td>
		</tr>
		<tr>
			<td>Religion</td>
			<td>The religious affiliation as specified by the person.</td>
			<td>0 to 1</td>
			<td>O</td>
			<td>Not required for Pharmacy to GP communication.</td>
		</tr>
		<tr>
			<td>Patient email address</td>
			<td>Email address of the patient.</td>
			<td>0 to 1</td>
			<td>O</td>
			<td>Not required for Pharmacy to GP communication.</td>
		</tr>
		<tr>
			<td>Communication preferences</td>
			<td>Preferred contact method, e.g., sign language, letter, phone, etc. Also preferred written communication format, e.g., large print, braille.</td>
			<td>0 to many</td>
			<td>O</td>
			<td>Not required for Pharmacy to GP communication.</td>
		</tr>
		<tr>
			<td>Relevant contacts</td>
			<td>Include the most important contacts including:<br>• Personal contacts e.g., next of kin, in case of emergency contact, lasting power of attorney, dependants, informal carers etc.<br>• Health/care professional contacts e.g., social worker, hospital clinician, care coordinator, key worker, Independent Mental Capacity Advocate (IMCA) etc.<br>Name, relationship, role (if formal role), contact details and availability, e.g. out of hours.</td>
			<td>0 to many</td>
			<td>O</td>
			<td>Not required for Pharmacy to GP communication.</td>
		</tr>
		<tr>
		<td colspan="5"><b>* M=Mandatory R=Required O=Optional</b></td>
		</tr>
	</tbody>
</table>

## Example Patient Demographics Section ##

<script src="https://gist.github.com/IOPS-DEV/bfc50c0dfaf8e6966d7c2af02219c87c.js"></script>







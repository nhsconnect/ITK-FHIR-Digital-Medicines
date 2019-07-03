---
title: Distribution list Section
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_distribution_list.html
summary: "Gives information about the Distribution list section"
---

{% include custom/section.warnbanner.html %}

## Distribution list  Content ##
The Distribution list section carries a list of recipients of the document. PRSB Elements should be formatted as subheadings in any HTML sent.

The document may be sent to any number of recipients, however all recipients should be included in the distribution list to allow individual recipients to know who else has received a copy.


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
			<td>Distribution list</td>
			<td>A list of other individuals to receive a copy of this communication.</td>
			<td>0 to 1</td>
			<td>R</td>
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
			<td>Name</td>
			<td>If the communication is being sent to a named individual, then this is the name of the recipient, preferably in a structured format. An identifier for the individual, for example GMC code (for a GP), or an SDS identifier, a NHS Number (for a patient) will be sent alongside the name, but may not displayed on rendered document.</td>
			<td>0 to 1</td>
			<td>R</td>
			<td>Names may be entered as the communication is being created or sourced from the hospital system. Patient names may be from the Patient Demographic Service. Text and carried in the FHIR element <b>Practitioner.name</b> or <b>Patient.name</b>. The identifier will be carried in the FHIR element <b>Practitioner.identifier</b> or <b>Patient.identifier.</b></td>
		</tr>
		<tr>
			<td>Role</td>
			<td>If the communication is being sent to either a named individual, or to a non-named person with a specific role, then this is the role of the recipient.</td>
			<td>0 to 1</td>
			<td>R</td>
			<td>Role may be entered as the communication is being created or sourced from the hospital system. This may be a role defined in the National Workforce data set (see the NHS Data Dictionary Job Role Code). Text and carried in the <b>PractitionerRole.code</b></td>
		</tr>
		<tr>
			<td>Grade</td>
			<td>The recipient's grade.</td>
			<td>0 to 1</td>
			<td>O</td>
			<td>The grade of the recipient, if known by the sending institution, otherwise omitted. Text only</td>
		</tr>
		<tr>
			<td>Organisation name</td>
			<td>The name of the organisation the recipient is representing or the organisation named as the receiving organisation. An identifier for the organisation will be sent alongside the name, but may not displayed on rendered document.</td>
			<td>0 to 1</td>
			<td>R</td>
			<td>Organisation name in text and carried in the FHIR element <b>Organization.name</b> and identifier (which <b>MUST NOT</b> be in carried in the text), taken from the Organisation Data Service (ODS)) and carried in the FHIR element <b>Organization.identifier</b></td>
		</tr>
		<tr>
			<td>Team</td>
			<td>Team that the recipient belongs to in the context of receiving this message, or the team acting as the recipient.</td>
			<td>0 to 1</td>
			<td>O</td>
			<td>There are no national codes for teams, so this value would have to be agreed locally, and entered as free text only.</td>
		</tr>
		<tr>
			<td>Relationship to subject</td>
			<td>The relationship of the receiver to the patient, where the receiver has a personal relationship to the patient, for example, carer or parent</td>
			<td>0 to 1</td>
			<td>O</td>
			<td>This is record of the relationship of the receiver to the patient, where the receiver has a personal relationship to the patient. Free text.</b></td>
		</tr>
		<tr>
		<td colspan="5"><b>* M=Mandatory R=Required O=Optional</b></td>
		</tr>
	</tbody>
</table>



## Example Distribution List Section ##

```
<xml>
<!--Distribution list-->
<section>
	<title value="Distribution list"/>
	<code>
		<coding>
			<system value="http://snomed.info/sct"/>
			<code value="887261000000109"/>
			<display value="Distribution list"/>
		</coding>
	</code>
	<text>
	<status value="generated"/>
	<div xmlns="http://www.w3.org/1999/xhtml">
	<table width="100%">
	<tbody>
		<tr>
			<th>Name</th>
			<td>If the communication is being sent to a named individual, then this is the name of the recipient, preferably in a structured format. An identifier for the individual, for example GMC code (for a GP), or an SDS identifier, a NHS Number (for a patient) will be sent alongside the name, but may not displayed on rendered document.</td>
		</tr>
		<tr>
			<th>Role</th>
			<td>If the communication is being sent to either a named individual, or to a non-named person with a specific role, then this is the role of the recipient.</td>			
		</tr>
		<tr>
			<th>Grade</th>
			<td>The recipient's grade.</td>
		</tr>
		<tr>
			<th>Organisation name</th>
			<td>The name of the organisation the recipient is representing or the organisation named as the receiving organisation. An identifier for the organisation will be sent alongside the name, but may not displayed on rendered document.</td>
		</tr>
		<tr>
			<th>Team</th>
			<td>Team that the recipient belongs to in the context of receiving this message, or the team acting as the recipient.</td>
		</tr>
		<tr>
			<th>Relationship to subject</th>
			<td>The relationship of the receiver to the patient, where the receiver has a personal relationship to the patient, for example, carer or parent</td>
		</tr>
	</tbody>
	</table>
	</div>
	</text>
		<!--Reference to the practitioner entries as recipients of information-->
		<entry>
			<reference value="urn:uuid:8ece9986-9af0-4882-b0cf-23a96ea7b509"/>
		</entry>
		<entry>
			<reference value="urn:uuid:5e414a77-d394-4248-a631-00e45ddb64a0"/>
		</entry>
	</section>
</xml>
```
		
## Coded Resources ##

This text section should be linked to the following FHIR Resources to provide the textual information in a coded format:

- Patient
- Practitioner
- Organization
- RelatedPerson
- Attachment-Binary
- PractitionerRole


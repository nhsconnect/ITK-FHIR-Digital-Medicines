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

| DISTRIBUTION   LIST     |                                                                                                                                                                                                                                                                                                                                                   |             |                                                                                                                                                                                                         |                                  |                          |
|-------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------|--------------------------|
| Data   Item             | Description                                                                                                                                                                                                                                                                                                                                       | Cardinality | Values                                                                                                                                                                                                  | Mandatory/required/     optional | FHIR Target              |
| Name                    | If   the communication is being sent to a named individual, then this is the name   of the recipient, preferably in a structured format. An identifier for the   individual, for example GMC code (for a GP), or an SDS identifier, a NHS   Number (for a patient) will be sent alongside the name, but may not be displayed   on rendered document. | 0   TO 1    | Names   may be entered as the communication is being created, or sourced from the   system. Patient names may be from the Patient Demographic Service                                                   | <font color="red">Optional</font>                         | Practitioner.name        |
| Role                    | If   the communication is being sent to either a named individual, or to a   non-named person with a specific role, then this is the role of the   recipient.                                                                                                                                                                                     | 0   TO 1    | Role   may be entered as the communication is being created, or sourced from the   system. This may be a role defined in the National Workforce data set (see   the NHS Data Dictionary Job Role Code). | <font color="red">Optional</font>                         | PractitionerRole.code    |
| Grade                   | The   recipient’s grade.                                                                                                                                                                                                                                                                                                                          | 0   TO 1    | The   grade of the recipient, if known by the sending institution, otherwise   omitted.                                                                                                                 | <font color="red">Optional</font>                         | Composition.section.text |
| Organisation name       | The   name of the organisation the recipient is representing or the organisation   named as the receiving organisation.          An identifier for the organisation will be sent alongside the name, but may   not be displayed on rendered document.                                                                                                | 0   TO 1    | Organisation   name, and identifier, taken from the Organisation Data Service (ODS).                                                                                                                    | <font color="red">Optional</font>                         | Organization.name        |
| Team                    | Team   that the recipient belongs to in the context of receiving this message, or   the team acting as the recipient.                                                                                                                                                                                                                             | 0   TO 1    | There   are no national codes for teams, so this value would have to be agreed   locally, and entered as free text.                                                                                     | <font color="red">Optional</font>                         | Composition.section.text |
| Relationship to subject | The   relationship of the receiver to the patient, where the receiver has a   personal relationship to the patient, for example, carer or parent                                                                                                                                                                                                  | 0   TO 1    | This   is a  record of the relationship of the receiver to the patient, where the   receiver has a personal relationship to the patient. Free text.                                                        | <font color="red">Optional</font>                         | Composition.section.text |

## Example Distribution List Section ##

{% include note.html content="these examples have not been clinially assured against Digital Medicines use cases" %}

```
<!--<xml>-->
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
			<td>parent</td>
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
<!--</xml>-->
```
		
## Coded Resources ##

This text section should be linked to the following FHIR Resources to provide the textual information in a coded format:

- Patient
- Practitioner
- Organization
- RelatedPerson
- Attachment-Binary
- PractitionerRole


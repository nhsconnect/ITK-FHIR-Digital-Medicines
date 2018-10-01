---
title: Attendance Details Section
keywords:  messaging, sections
tags: [fhir,messaging,section]
sidebar: foundations_sidebar
permalink: explore_attendance_details.html
summary: "Gives information about the Attendance details section"
---

{% include custom/section.warnbanner.html %}

## Attendance Details Section Content ##
The Attendance details section carries information about Attendance details used. PRSB Elements should be formatted as subheadings in any HTML sent.


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
   			<td>Attendance details</td>
  			<td>The details of the patient contact.</td>
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
   			<td>Date and time of contact</td>
   			<td>Date and time of the appointment, contact or attendance.</td>
   			<td>1 only</td>
   			<td>M</td>
   			<td>The date as recorded by the pharmacy system and carried in the FHIR element <b>Encounter.period.start</b>.</td>
  		</tr>
  		<tr>
   			<td>Service</td>
   			<td>The service under which the vaccination was administered.</td>
   			<td>0 to 1</td>
   			<td>R</td>
   			<td>Coded entry e.g. seasonal influenza, travel vaccination, Hepatitis B vaccination etc. carried in the FHIR element <b>TBC</b>.</td>
  		</tr>
		<tr>
   			<td>Organisation name</td>
   			<td>The name, including the identifier, of the organisation where the medicine was supplied.</td>
   			<td>1 only</td>
   			<td>M</td>
   			<td>This would be generated from the ODS code and associated text. In the future the global location number (GLN) may be used - GS1 standard. Carried in the FHIR element <b>Encounter.serviceProvider</b> with a link to <b>CareConnect-Organization-1</b> (identifier and name).</td>
  		</tr>
		<tr>
   			<td>Organisation address</td>
   			<td>The address of the organisation where the medicine was supplied.</td>
   			<td>0 to 1</td>
   			<td>R</td>
   			<td>ODS standard but may be generated from the Directory of Services (DOS). Carried in the FHIR element <b>Encounter.serviceProvider</b> with a link to <b>CareConnect-Organization-1</b> (address).</td>
  		</tr>
		<tr>
   			<td>Location of administration</td>
   			<td>The location of where the vaccine was administered (if different from the organisation address).</td>
   			<td>0 to 1</td>
   			<td>O</td>
   			<td>Free text. Carried in the FHIR element <b>Encounter.location</b>.</td>
  		</tr>
		<tr>
   			<td>Organisation contact details</td>
   			<td>The contact details of the organisation where the medicine was supplied. For example a phone number, NHSmail address etc. Contact details are used to resolve queries about the record entry.</td>
   			<td>0 to many</td>
   			<td>R</td>
   			<td>ODS standard but may be generated from the Directory of Services (DOS). Carried in the FHIR element <b>Encounter.serviceProvider</b> with a link to <b>CareConnect-Organization-1</b> (telecom).</td>
  		</tr>
		<tr>
   			<td>Person accompanying patient</td>
   			<td>Identify, where clinically relevant, others accompanying the patient, e.g. parent, relative or friend. Includes: Name, Relationship, Role (e.g.informal carer).</td>
   			<td>0 to many</td>
   			<td>O</td>
   			<td>Free text. Carried in the FHIR element <b>Encounter.participant</b>.</td>
  		</tr>
		<tr>
   			<td>Care professionals present</td>
   			<td>The name, designation of the additional individuals or team members including consultant(s), nurse consultant(s), allied health professional(s), social worker(s).</td>
   			<td>0 to many</td>
   			<td>O</td>
   			<td>Not required for Pharmacy to GP communication.</td>
  		</tr>
		<tr>
   			<td>Chaperone</td>
   			<td>The name and designation of any.</td>
   			<td>0 to many</td>
   			<td>O</td>
   			<td>Free text. Carried in the FHIR element <b>TBC</b>.</td>
  		</tr>
		<tr>
		<td colspan="5"><b>* M=Mandatory R=Required O=Optional</b></td>
		</tr>
 	</tbody>
</table>


## Example Attendance details Section ##

<script src="https://gist.github.com/IOPS-DEV/6f8df85f74e8039a4c76085b531bfea1.js"></script>

## Coded Resources ##

This text section should be linked to the following FHIR Resources to provide the textual information in a coded format.

- The Digital Medicines specification does not currently support coded attendance details.







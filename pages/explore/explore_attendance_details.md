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
   <td>The date as recorded on the PAS in text and carried in the FHIR element <b>Encounter.period.start</b> and <b>Encounter.period.end</b>.</td>
  </tr>
		<tr>
		<td colspan="5"><b>* M=Mandatory R=Required O=Optional</b></td>
		</tr>
 </tbody>
</table>


## Example Attendance details Section ##

<script src="https://gist.github.com/IOPS-DEV/267964b88b286590ec7a33d6cb678c04.js"></script>

## Coded Resources ##

This text section should be linked to the following FHIR Resources to provide the textual information in a coded format.

- The ITK3 FHIR Emergency Care eDischarge does not currently support coded attendance details.







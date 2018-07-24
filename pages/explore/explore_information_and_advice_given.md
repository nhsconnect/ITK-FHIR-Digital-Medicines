---
title: Information and Advice Given Section
keywords:  messaging, sections
tags: [fhir,messaging,section]
sidebar: foundations_sidebar
permalink: explore_information_and_advice_given.html
summary: "Gives information about the Information and advice given section"
---

{% include custom/section.warnbanner.html %}

## Information and Advice Given Section Content##
The Information and advice given section carries details about the information and advice given. PRSB Elements should be formatted as subheadings in any HTML sent.


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
   <td>Information and advice given</td>
   <td>A record of any information or advice given to the patient, carer or relevant third party.</td>
   <td>0 to 1</td>
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
   <td>Information and advice given</td>
   <td>This includes:- what information-to whom it was given.</td>
   <td>1 only</td>
   <td>M</td>
   <td>Free text description of information and advice given and patient/carer comprehension. For this use case this element may also contain text derived from the  ECDS Emergency Care Discharge Information Given code set (SNOMED CT):
   <br/>Copy of discharge letter NOT provided to patient
   <br/>Copy of discharge letter provided to patient. <br/>Note: there is no provision to send this information in a coded format.</td>
   </tr>
		<tr>
		<td colspan="5"><b>* M=Mandatory R=Required O=Optional</b></td>
		</tr>
 </tbody>
</table>


##  Example Information and Advice Given Section ##


<script src="https://gist.github.com/IOPS-DEV/e71ebe4dbcaf89da92e719307cc56aeb.js"></script>

## Coded Resources ##

This text section should be linked to the following FHIR Resources to provide the textual information in a coded format.

- The ITK3 FHIR FHIR Emergency Care eDischarge does not currently support coded information and advice given.

 









---
title: History Section
keywords:  messaging, sections
tags: [fhir,messaging,sections]
sidebar: foundations_sidebar
permalink: explore_history.html
summary: "Gives information about the History section"
---

{% include custom/section.warnbanner.html %}

## History Section Content##
The History section carries history related to the patient's previous care. Elements should be rendered as subheadings in any HTML sent.

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
   <td>History</td>
   <td>Information relating to the development of each presenting complaint, and the patient's relevant health history.</td>
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
   <td>Patient's reason for referral</td>
   <td>Patient stated reason for referral. This may include any discussions that took place, the level of shared decision making involved, information about patient's source of advice. This may be expressed on behalf of the patient, eg by parent or carer.</td>
   <td>0 to 1</td>
   <td>O</td>
   <td>Not required in Pharmacy to GP communication.</td>
  </tr>
  <tr>
   <td>Presenting complaints or issue</td>
   <td>The list and description of the health problems and issues experienced by the patient resulting in the attendance. This may include disease state, medical condition, response and reaction to therapies, eg blackout, dizziness, chest pain, follow-up from admission, falls, a specific procedure, investigation or treatment.</td>
   <td>0 to many</td>
   <td>R</td>
   <td>Not required in Pharmacy to GP communication.</td>
  </tr>
  <tr>
   <td>History of each presenting complaint or issue</td>
   <td>Information directly related to the development and characteristics of each presenting complaint (eg including travel history). Including if the information is given by the patient or their carer.</td>
   <td>0 to many</td>
   <td>O</td>
   <td>Not required in Pharmacy to GP communication.</td>
  </tr>
  <tr>
   <td>History since last contact</td>
   <td>History since last attendance, discharge from hospital, etc.</td>
   <td>0 to 1</td>
   <td>R</td>
   <td>Not required in Pharmacy to GP communication.</td>
  </tr>
  <tr>
   <td>Relevant past medical, surgical and mental health history</td>
   <td>The record of the person's significant medical, surgical and mental health history. Including relevant previous diagnoses, problems and issues, procedures, investigations, specific anaesthesia issues, etc (will include dental and obstetric history)</td>
   <td>0 to 1</td>
   <td>R</td>
   <td>History pertinent to the vaccination e.g. contraindications, pregnancy, immunosupression. Text and if available for procedures and conditions carried the FHIR elements <b>Procedure.code</b> and <b>Condition.code</b></td>
  </tr>
		<tr>
		<td colspan="5"><b>* M=Mandatory R=Required O=Optional</b></td>
		</tr>
 </tbody>
</table>


##  Example History Section ##

<script src="https://gist.github.com/IOPS-DEV/5b124a0f1388bec20e062d944a80ce1d.js"></script>

## Coded Resources ##

This text section should be linked to the following FHIR Resources to provide the textual information in a coded format.

- [Condition](build_conditions.html)
- [Procedure](build_procedures.html)






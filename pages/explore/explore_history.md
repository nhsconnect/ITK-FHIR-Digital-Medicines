---
title: History Section
keywords:  messaging, sections
tags: [fhir,messaging,sections]
sidebar: foundations_sidebar
permalink: explore_history.html
summary: "Gives information about the History section"
---

{% include custom/section.warnbanner.html %}

## History Section Content ##
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
   <td>Relevant past medical, surgical and mental health history</td>
   <td>The record of the person's significant medical, surgical and mental health history. Including relevant previous diagnoses, problems and issues, procedures, investigations, specific anaesthesia issues, etc (will include dental and obstetric history)</td>
   <td>0 to 1</td>
   <td>R</td>
   <td>History pertinent to the emergency supply of medicine e.g. contraindications, pregnancy, immunosupression. May be a SNOMED CT term or free text.</td>
  </tr>
		<tr>
		<td colspan="5"><b>* M=Mandatory R=Required O=Optional</b></td>
		</tr>
 </tbody>
</table>


##  Example History Section ##

```
<!--<xml>-->
<!--History-->
	<section>
	<title value="History"/>
		<code>
			<coding>
				<system value="http://snomed.info/sct"/>
				<code value="717121000000105"/>
				<display value="History"/>
			</coding>
		</code>
		<text>
		<status value="additional"/>
		<div xmlns="http://www.w3.org/1999/xhtml">
		<table width="100%">
			<tbody>
			<tr>
				<th>Relevant past medical, surgical and mental health history</th>
				<td>
				<p>Patient has Chronic Obstructive Pulmonary Disease (COPD). She was advised to have the flu vaccination as she is at greater risk from flu and its complications when she last attended her GP Practice.</p>
				<p>Patient requested the vaccination.</p>
				<p>No history of vaccination recorded at Pharmacy.</p>
				</td>
			</tr>
			</tbody>
		</table>
		</div>
		</text>
	</section>
<!--</xml>-->
```

## Coded Resources ##

This text section should be linked to the following FHIR Resources to provide the textual information in a coded format.

- [Condition](build_conditions.html)
- [Procedure](build_procedures.html)






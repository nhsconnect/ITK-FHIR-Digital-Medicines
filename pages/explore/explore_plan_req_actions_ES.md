---
title: Plan and Requested Actions Section
keywords:  messaging, sections
tags: [fhir,messaging,section]
sidebar: foundations_sidebar
permalink: explore_plan_req_actions_ES.html
summary: "Gives information about the Plan and Requested Actions section"
---

{% include custom/section.warnbanner.html %}

## Plan and Requested Actions Section Content ##
The Plan and requested actions section carries information about planned and requested actions such as planned investigations, procedures etc. PRSB Elements should be formatted as subheadings in any HTML sent.

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
			<td>Plan and requested actions</td>
			<td>The details of planned investigations, procedures and treatment, and whether this plan has been agreed with the patient or their legitimate representative.</td>
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
			<td>Actions for healthcare professionals</td>
			<td>Including planned investigations, procedures, Interventions and treatment for a patient’s identified conditions and priorities. For each action the following should be identified:<br/>
			<ul>
			<li>a) person responsible - name and designation / department / hospital etc or role (eg GP) responsible for carrying out the proposed action, and where action should take place.<br/></li>
			<li>b) status - requested, planned or completed.<br/></li>
            <li>c) When action requested for - requested date, time, or period - as relevant.<br/></li>
			<li>d) suggested strategies - suggested strategies for potential problems.<br/></li>
            <li>e) outcome expectations, including patient’s expectations</li>
			</ul></td>
			<td>0 to many</td>
			<td>R</td>
			<td>Free text</td>
		</tr>
		<tr>
			<td>Actions for patient or their carer</td>
			<td>For each action the following should be identified: outcome expectations, including patient's expectations.</td>
			<td>0 to many</td>
			<td>R</td>
			<td>A record of the planned and requested actions. May be structured HTML for example a table, with actions, names, dates, status, location, strategies, or free text.</td>
		</tr>
		<tr>
			<td>Agreed with patient or legitimate patient representative.</td>
			<td>Indicates whether the patient or legitimate representative has agreed the entire plan or individual aspects of treatment, expected outcomes, risks and alternative treatments.</td>
			<td>0 to 1</td>
			<td>O</td>
			<td>Not required in Pharmacy to GP communication.</td>
		</tr>
		<tr>
			<td>Investigations requested</td>
			<td>This includes a name or description of the investigation requested and the date requested.</td>
			<td>0 to many</td>
			<td>O</td>
			<td>Not required in Pharmacy to GP communication.</td>
		</tr>
		<tr>
			<td>Procedures requested</td>
			<td>These are the diagnostic or therapeutic procedures that have actually been requested (and the date requested).</td>
			<td>0 to many</td>
			<td>O</td>
			<td>Not required in Pharmacy to GP communication.</td>
		</tr>
		<tr>
		<td colspan="5"><b>* M=Mandatory R=Required O=Optional</b></td>
		</tr>
	</tbody>
</table>

##  Example Plan and Requested Actions Section ##

<script src="https://gist.github.com/IOPS-DEV/a894670cc0a210482280bf7ee0b16f60.js"></script>

## Coded Resources ##

This text section should be linked to the following FHIR Resources to provide the textual information in a coded format.

- The Digital Medicines Specification does not currently support coded Plan and requested actions information.







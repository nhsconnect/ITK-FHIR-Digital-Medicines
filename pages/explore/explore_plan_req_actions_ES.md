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
			<td>0 to many</td>
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
			<td>For each action the following should be identified:<br/>
				<ul>
					<li>a) person responsible - name and designation eg patient or carer responsible for carrying out the proposed action, and where action should take place.<br/></li>
					<li>b) status - requested, planned or completed.<br/></li>
					<li>c)  When action requested for - requested date, time, or period - as relevant.<br/></li>
					<li>d) suggested strategies - suggested strategies for potential problems, eg telephone contact for advice.<br/></li>
					<li>e) outcome expectations, including patient’s expectations.</li>
				</ul></td>
			<td>0 to many</td>
			<td>R</td>
			<td>Free text</td>
		</tr>
		<tr>
			<td colspan="5"><b>* M=Mandatory R=Required O=Optional</b></td>
		</tr>
	</tbody>
</table>

```
<xml>
	<section>
		<title value="Plan and requested actions"/>
			<code>
				<coding>
					<system value="http://snomed.info/sct"/>
					<code value="887201000000105"/>
					<display value="Plan and requested actions"/>
				</coding>
			</code>
			<text>
			<status value="generated"/>
			<div xmlns="http://www.w3.org/1999/xhtml">
			<table width="100%">
				<tbody>
				<tr>
					<th>Plan and requested actions</th>
					<td>
					<p>GP to review medications and speak to Patient regarding electronic repeat dispensing</p>
					</td>
				</tr>
				<tr>
					<th>Actions for healthcare professionals</th>
					<td>Including planned investigations, procedures, Interventions and treatment for a patient’s identified conditions and priorities. For each action the following should be identified:<br/>
						<ul>
							<li>a) person responsible - name and designation / department / hospital etc or role (eg GP) responsible for carrying out the proposed action, and where action should take place.<br/></li>
							<li>b) status - requested, planned or completed.<br/></li>
							<li>c) When action requested for - requested date, time, or period - as relevant.<br/></li>
							<li>d) suggested strategies - suggested strategies for potential problems.<br/></li>
							<li>e) outcome expectations, including patient’s expectations</li>
						</ul></td>
				</tr>
				<tr>
					<th>Actions for patient or their carer</th>
					<td>For each action the following should be identified:<br/>
						<ul>
							<li>a) person responsible - name and designation eg patient or carer responsible for carrying out the proposed action, and where action should take place.<br/></li>
							<li>b) status - requested, planned or completed.<br/></li>
							<li>c)  When action requested for - requested date, time, or period - as relevant.<br/></li>
							<li>d) suggested strategies - suggested strategies for potential problems, eg telephone contact for advice.<br/></li>
							<li>e) outcome expectations, including patient’s expectations.</li>
						</ul></td>
				</tr>
				</tbody>
			</table>
			</div>
			</text>
	</section>
</xml>
```



##  Example Plan and Requested Actions Section ##

##  Coded Resources ##

This text section should be linked to the following FHIR Resources to provide the textual information in a coded format.

- The Digital Medicines Specification does not currently support coded Plan and requested actions information.
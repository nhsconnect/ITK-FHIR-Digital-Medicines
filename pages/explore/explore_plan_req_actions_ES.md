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

| PLAN   AND REQUESTED ACTIONS         |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |             |             |                                  |                          |
|--------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------|-------------|----------------------------------|--------------------------|
| Data Item                            | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | Cardinality | Values      | Mandatory/required/     optional | FHIR Target              |
| Actions for healthcare professionals | Including   planned investigations, procedures, Interventions and treatment for a   patient’s identified conditions and priorities. For each action the following   should be identified:                                                      a) person responsible - name and designation / department / hospital   etc or role (eg GP) responsible for carrying out the proposed action, and   where action should take place.          b) status - requested, planned or completed.                                                      c) When action requested for - requested date, time, or period - as   relevant.                                                         d) suggested strategies - suggested strategies for potential   problems.          e) outcome expectations, including patient’s expectations | 0   TO MANY | Free   text | Required                         | Composition.section.text |
| Actions for patient or their carer   | For   each action the following should be identified:                                                      a) person responsible - name and designation eg patient or carer   responsible for carrying out the proposed action, and where action should   take place.          b) status - requested, planned or completed.                                                c)  When action requested for -   requested date, time, or period - as relevant.                                                         d) suggested strategies - suggested strategies for potential problems,   eg telephone contact for advice.          e) outcome expectations, including patient’s expectations.                                                                                                                                | 0   TO MANY | Free   text | Required                         | Composition.section.text |

{% include note.html content="These examples have not been clinically assured against Digital Medicines use cases.<br/>Examples are illustrative only." %}

```
<!--<xml>-->
<!-- Plan and requested actions-->
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
<!--</xml>-->
```



##  Example Plan and Requested Actions Section ##

##  Coded Resources ##

This text section should be linked to the following FHIR Resources to provide the textual information in a coded format.

- The Digital Medicines Specification does not currently support coded Plan and requested actions information.
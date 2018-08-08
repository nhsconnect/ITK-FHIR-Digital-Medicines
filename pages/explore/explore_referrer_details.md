---
title: Referrer Details Section
keywords:  messaging, sections
tags: [fhir,messaging,section]
sidebar: foundations_sidebar
permalink: explore_referrer_details.html
summary: "Gives information about the Referrer details section"
---

{% include custom/section.warnbanner.html %}

## Referrer Details Section Content##
The Referrer details section carries a narrative summary of the episode, where possible, very brief. PRSB Elements should be formatted as subheadings in any HTML sent.

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
			<td>Referrer details</td>
			<td>Details of the individual or team who referred the patient.</td>
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
			<td>Referrer details</td>
			<td>Name, role, grade, organisation and contact details of referrer. If not an individual, this could be e.g. GP surgery, department, specialty, sub-specialty, educational institution, mental health team etc. Also needs to include self-referral. The referrer details will normally be copied forward from the referral or handover of care, document. Where the referral or handover of care document stated individual, team, department or organisation names and identifies, these should form part of the Referrer details. Where the referral is a self-referral, text should indicate - self referral.</td>
			<td>0 to 1 referrer name<br/>0 to 1 referrer role<br/>0 to 1 referrer grade<br/>0 to 1 referrer department or team name<br/>0 to 1 referrer speciality<br/>0 to 1 referrer organisation<br/>0 to many contact details. </td>
			<td>R</td>
			<td>The referrer details are sent as text and the following FHIR elements.
			<ul>
			<li>Name - <b>Practitioner.name</b></li>
			<li>Role - <b>PractitionerRole.code</b></li>
			<li>Grade - <b>Text Only</b></li>
			<li>Organisation - <b>Organization.name</b></li>
			<li>Contact details - <b>PractitionerRole.telecom</b> or <b>Organization.telecom</b> </li>
			<li>Speciality - <b>PractitionerRole.specialty</b></li>
</ul>
	

</td>
		</tr>
		<tr>
		<td colspan="5"><b>* M=Mandatory R=Required O=Optional</b></td>
		</tr>
	</tbody>
</table>

##  Example Referrer Details Section ##

<script src="https://gist.github.com/IOPS-DEV/324006a867ea11a33997dcb6148b289a.js"></script>








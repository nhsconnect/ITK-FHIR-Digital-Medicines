---
title: GP Practice Section
keywords:  messaging, sections
tags: [fhir,messaging,section]
sidebar: foundations_sidebar
permalink: explore_gp_practice.html
summary: "Gives information about the patient's GP Practice"
---
{% include custom/section.warnbanner.html %}


## GP Practice Section Content##

The GP practice section contains details of the patients GP practice. PRSB Elements should be formatted as subheadings in any HTML sent.
 
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
			<td>GP practice </td>
			<td>Details of the GP practice where the patient is registered.</td>
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
			<td>GP practice identifier</td>
			<td>The identifier of the registered GP Practice. Note: this heading is defined as mandatory however the heading does not appear in the text, but it is mandatory to populate the identifier in the Practitioner Resource.</td>
			<td>1 only</td>
			<td>M</td>
			<td>This should be the Organisation Data Services (ODS) identifier for the practice which <b>MUST NOT</b> be in text but carried in the FHIR element <b>Organization.identifier</b>. This includes codes to use where there is no registered GP practice which should follow the <a href="https://www.datadictionary.nhs.uk/web_site_content/supporting_information/organisation_data_service_default_codes.asp?shownav=1">NHS Data Dictionary default codes</a>.</td>
		</tr>
		<tr>
			<td>GP name</td>
			<td>Where the patient or patient's representative offers the name of a GP as their usual GP.</td>
			<td>0 to 1</td>
			<td>R</td>
			<td>Patients are registered with GP Practices, so their usual GP name will be something volunteered by the patient or their representative. Text and carried in the FHIR element <b>Practitioner.name</b>.</td>
		</tr>
		<tr>
			<td>GP practice details</td>
			<td>Name and address of the patient's registered GP Practice.</td>
			<td>0 to 1</td>
			<td>R</td>
			<td>Registered GP Practice details are available from the Patient Demographics Service (PDS), or volunteered from the patient or their representative or provided by referral contact. Include details of the Practice name and address in text and carried in the FHIR elements <b>Organization.name</b> and <b>Organization.address</b>.</td>
		</tr>
		<tr>
		<td colspan="5"><b>* M=Mandatory R=Required O=Optional</b></td>
		</tr>
	</tbody>
</table>
 
## Example GP Practice Section ##

<script src="https://gist.github.com/IOPS-DEV/935de02a64d69050010e2230f27f93a0.js"></script>







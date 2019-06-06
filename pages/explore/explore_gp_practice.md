---
title: GP Practice Section
keywords:  messaging, sections
tags: [fhir,messaging,section]
sidebar: foundations_sidebar
permalink: explore_gp_practice.html
summary: "Gives information about the GP Practice section"
---
{% include custom/section.warnbanner.html %}


## GP Practice Section Content ##

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
		<td colspan="5"><b>* M=Mandatory R=Required O=Optional</b></td>
		</tr>
	</tbody>
</table>
 
## Example GP Practice Section ##

```
<xml>
<!-- GP Practice-->
	<section>
		<title value="GP practice"/>
			<code>
				<coding>
					<system value="http://snomed.info/sct"/>
					<code value="886711000000101"/>
					<display value="GP practice"/>
				</coding>
			</code>
			<text>
			<status value="additional"/>
			<div xmlns="http://www.w3.org/1999/xhtml">
			<table width="100%">
				<tbody>
				<tr>
					<th>GP name</th>
					<td>
						<p>Prefix: Dr</p>
						<p>Given Name: Paul</p>
						<p>Family Name: Rastall</p>
					</td>
				</tr>
				<tr>
					<th>GP practice identifier</th>
					<td>
						<p>ODS Organization Code:GP123456</p>
					</td>
				</tr>
				<tr>
					<th>GP practice details</th>
					<td>
						<p>Name: MGP Medical Centre</p>
						<p>Address:</p>
						<p>Address Line: 1 MGP House, Overtown</p>
						<p>City: Leeds</p>
						<p>Post Code: LS21 7PA</p>
					</td>
				</tr>
				</tbody>
			</table>
			</div>
			</text>
		<!--Reference to the Organisation entry as the source of information for this section-->
		<entry>
			<reference value="urn:uuid:94ca030c-03aa-4dae-8270-c2de2b7907ef"/>
		</entry>
	</section>
</xml>
```
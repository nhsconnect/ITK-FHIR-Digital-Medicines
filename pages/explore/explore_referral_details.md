---
title: Referral Details Section
keywords:  messaging, sections
tags: [fhir,messaging,section]
sidebar: foundations_sidebar
permalink: explore_referral_details.html
summary: "Gives information about the Referral Details section"
---

{% include custom/section.warnbanner.html %}

## Referral Details Section Content ##
The Referral details section carries a narrative summary of the episode, where possible, very brief. PRSB Elements should be formatted as subheadings in any HTML sent.

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
			<td>Referral details</td>
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
   			<td>Referral to</td>
   			<td>Name, designation and organisation. If not an individual, this could be a service, e.g. GP surgery, department, specialty, subspecialty, educational institution, mental health etc.</td>
   			<td>0 to 1</td>
   			<td>R</td>
   			<td>Free text</td>
  		</tr>		
		<tr>
   			<td>Clinical urgency of referral</td>
   			<td>Referrer’s assessment of urgency (e.g. urgent/ soon/ routine). May include reason if other than routine. Eg two data items:* level of urgency* reason.</td>
   			<td>0 to 1</td>
   			<td>R</td>
   			<td>PRIORITY TYPE (NHS Data Dictionary)https://www.datadictionary.nhs.uk/data_dictionary/<br/>
			attributes/p/prio/priority_type_de.asp?shownav=1
<br/>
Free text reason </td>
  		</tr>		
		<tr>
   			<td>Expectation of referral</td>
   			<td>A clear statement of the expectations of the person making the referral as to the management of the patient eg advice only, diagnosis, treatment, etc. To include any specific patient expectation.</td>
   			<td>0 to many</td>
   			<td>R</td>
   			<td>Free text</td>
  		</tr>		
		<tr>
   			<td>Reason for referral</td>
   			<td>A clear statement of the purpose of the person making the referral e.g. diagnosis, treatment, transfer of care due to relocation, investigation, second opinion, management of the patient (e.g. palliative care), provide referrer with advice / guidance. This may include referral because of carers' concerns.</td>
   			<td>0 to 1</td>
   			<td>R</td>
   			<td>Free text</td>
  		</tr>
		<tr>
		<td colspan="5"><b>* M=Mandatory R=Required O=Optional</b></td>
		</tr>
	</tbody>
</table>

##  Example Referral Details Section ##

```
<xml>
<!-- Referrer details-->
	<section>
		<title value="Referrer details"/>
		<code>
			<coding>
				<system value="http://snomed.info/sct"/>
				<code value="1052891000000108"/>
				<display value="Referrer details"/>
			</coding>
		</code>
		<text>
			<status value="generated"/>
			<div xmlns="http://www.w3.org/1999/xhtml">
			<table width="100%">
			<tbody>				
				<tr>
					<th>Referral details</th>
					<td><p>Self referral.</p></td>
				</tr>
				<tr>
					<th>Referral to</th>
					<td><p>GP surgery</p></td>
				</tr>		
				<tr>
					<th>Clinical urgency of referral</th>
					<td>urgent</td>
				</tr>		
				<tr>
					<th>Expectation of referral</th>
					<td>A clear statement of the expectations of the person making the referral as to the management of the patient eg advice only, diagnosis, treatment, etc. To include any specific patient expectation.</td>
				</tr>		
				<tr>
					<th>Reason for referral</th>
					<td>A clear statement of the purpose of the person making the referral e.g. diagnosis, treatment, transfer of care due to relocation, investigation, second opinion, management of the patient (e.g. palliative care), provide referrer with advice / guidance. This may include referral because of carers' concerns.</td>
				</tr>
			</tbody>
			</table>
			</div>
		</text>
	</section>
</xml>
```
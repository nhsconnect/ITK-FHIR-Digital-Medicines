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

| REFERRAL   DETAILS           |                                                                                                                                                                                                                                                                                                                              |             |                                                                                                                                                                      |                                  |                          |
|------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------|--------------------------|
| Data Item                    | Description                                                                                                                                                                                                                                                                                                                  | Cardinality | Values                                                                                                                                                               | Mandatory/required/     optional | FHIR Target              |
| Referral to                  | Name,   designation and organisation. If not an individual, this could be a service,   e.g. GP surgery, department, specialty, subspecialty, educational   institution, mental health etc.                                                                                                                                   | 0   TO 1    | Free   text                                                                                                                                                          | Required                         | Composition.section.text |
| Clinical urgency of referral | Referrer’s   assessment of urgency (e.g. urgent/ soon/ routine). May include reason if   other than routine. Eg two data items:* level of urgency* reason.                                                                                                                                                                   | 0   TO 1    | PRIORITY   TYPE (NHS Data   Dictionary) https://www.datadictionary.nhs.uk/ data_dictionary/attributes/ p/prio/priority_type_de.asp? shownav=1          Free text reason  | Required                         | Composition.section.text |
| Expectation of referral      | A   clear statement of the expectations of the person making the referral as to   the management of the patient eg advice only, diagnosis, treatment, etc. To   include any specific patient expectation.                                                                                                                    | 0   TO MANY | Free   text                                                                                                                                                          | Required                         | Composition.section.text |
| Reason for referral          | A   clear statement of the purpose of the person making the referral e.g.   diagnosis, treatment, transfer of care due to relocation, investigation,   second opinion, management of the patient (e.g. palliative care), provide   referrer with advice / guidance. This may include referral because of carers'   concerns. | 0   TO 1    | Free   text                                                                                                                                                          | Required                         | Composition.section.text |

##  Example Referral Details Section ##

```
<!--<xml>-->
<!-- Referral details-->
	<section>
		<title value="Referral details"/>
		<code>
			<coding>
				<system value="http://snomed.info/sct"/>
				<code value="1052891000000108"/>
				<display value="Referral details"/>
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
<!--</xml>-->
```
---
title: Referrer Details Section
keywords:  messaging, sections
tags: [fhir,messaging,section,referrer]
sidebar: foundations_sidebar
permalink: explore_referrer_details.html
summary: "Gives information about the Referrer Details section"
---

{% include custom/section.warnbanner.html %}

## Referrer Details Section Content ##
The Referral details section carries a narrative summary of the referrer details, where possible. PRSB Elements should be formatted as subheadings in any HTML sent.

| REFERRER   DETAILS           |                                                                                                                                                                                                                                                                                                                              |             |                                                                                                                                                                      |                                  |                          |
|------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------|--------------------------|
| Data Item  | Description | Cardinality | Values | Mandatory/required/     optional | FHIR Target              |
| Referral Record   |Indicates an active referral in the system | | Active / Inactive   | Mandatory  |Composition.section.text|
|Referrer Provider Name|Name of the referring organisation processing the referral||Format defined by the referring organisation - no local interpretation|Mandatory|ReferralRequest.requester.onBehalfOf > Organization|
|Referrer Provider Address|Address of the referring organisation processing the referral||Format defined by the referring organisation - no local interpretation|Mandatory|Organization.address|
|Referrer Provider ODS Code|ODS code for the referring organisation||Format defined by the referring organisation - no local interpretation|Mandatory|Organization.identifier|
|Sys ID (IT system reference code)|IT system reference code for the identified referral|||Mandatory||
|     Provision Date Time                                         |     Date that the referral was   made by the referring organisation                                           |          |     Standardised format   dd/mm/yyyy      ( e.g. 06/05/2020)                    |     Mandatory    |     ReferralRequest.authoredOn                                                                                                                                   |
|     Initials [Anonymised] (of   Patient being referred)         |     Initials of the Patient for   whom the referral is being made                                             |          |     Full Name captured by the   system                                          |     Mandatory    |     Composition.section.text                                                                                                                                     |
|     Referrer Case ID                                              |     The Case ID from the   referring organisation                                                             |          |     Format defined by the   referring organisation - no local interpretation    |     Mandatory    |     ReferralRequest.identifier                                                                                                                                   |
|     Referrer Case Ref                                             |     The case reference number   from the referring organisation                                               |          |     Format defined by the   referring organisation - no local interpretation    |     Mandatory    |     ReferralRequest.identifier                                                                                                                                   |
|     Referrer Name     OR     ReferrerName     [Anonymised]???    |     Name (Anonymised) of the   referring organisation employee making the referral                            |          |     Full Name captured by the   system                                          |     Mandatory    |     ReferralRequest.requester.agent   > Practitioner (practitioner.name)                                                                                         |
|     Referrer Role                                                |     Role of the referring   organisation employee making the referral                                         |          |     Format defined by the referring   organisation - no local interpretation    |     Mandatory    |     Composition.section.text                                                                                                                                     |
|     Disposition Code                                             |     Dx code from the 111 system   resulting from the Clinical Pathways assessment                             |          |     Standardised naming   convention taken from the Clinical Pathways system    |     Mandatory    |     ReferralRequest.reasonCode   (code)                                                                                                                          |
|     Disposition Description                                      |     Description of the Dx code   taken from the 111 system resulting from the Clinical Pathways assessment    |          |     Standardised naming   convention taken from the Clinical Pathways system    |     Mandatory    |     ReferralRequest.reasonCode   (display)                                                                                                                       |
|     Referral Status                                             |     Shows the current status of   the referral at the time of reporting                                       |          |     Options drop down menu (see   notes)                                        |     Mandatory    |     ReferralRequest.status                                                                                                                                       |
|     Referral History                                            |     Shows the history with   dates and times when referrals status changed                                    |          |                                                                                 |     Mandatory    |     ReferralRequest.note                                                                                                                                         |
|     Signposting Reason                                           |     Reason for signposting                                                                                    |          |     Free text data entry                                                        |     Mandatory    |     ReferralRequest.reasonCode     This is the second use of   reason code – the 2 uses (disposition code & signposting reason) will   need separate systems.    |
|     Escalation Reason                                            |     Reason for escalating                                                                                     |          |     Free text data entry                                                        |     Mandatory    |     ReferralRequest.priority                                                                                                                                     |


##  Example Referrer Details Section ##

{% include note.html content="These examples have not been clinically assured against Digital Medicines use cases.<br/>Examples are illustrative only." %}

```
<!--<xml>-->
<!-- Referral details-->
	<section>
		<title value="Referral details"/>
		<code>
			<coding>
				<system value="http://snomed.info/sct"/>
				<code value="886721000000107"/>
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
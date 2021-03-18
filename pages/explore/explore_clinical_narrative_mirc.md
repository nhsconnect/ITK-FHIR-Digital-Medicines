---
title: Clinical Narrative
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_clinical_narrative_mirc.html
summary: "Gives information about the Clinical Narrative section"
---

{% include custom/section.warnbanner.html %}

## Clinical Narrative Section Content ##
The Clinical Narrative section carries information about the Clinical Narrative details used. PRSB Elements should be formatted as subheadings in any HTML sent.


| CLINICAL   NARRATIVE |                                                                                                                                   |             |             |                                  |                          |
|----------------------|-----------------------------------------------------------------------------------------------------------------------------------|-------------|-------------|----------------------------------|--------------------------|
| Data Item            | Description                                                                                                                       | Cardinality | Values      | Mandatory/required/     optional | FHIR Target              |
| Clinical narrative   | A   description detailing a patient’s reason for attendance,  any red flags, results from the diagnostic   and treatment process. | 1 ONLY   | Free   text | Mandatory                        | Composition.section.text |
|     CKS Checked                                                                                    |     Confirmation   Yes/No whether the Clinical Knowledge Summaries were checked as part of the   referral                                                         |          |     Options   - "Yes", "No"    |     Mandatory    |     Composition.section.text    |
|     Red Flags                                                                                      |     Confirmation   Yes/No whether the presence of clinical Red Flags were checked as part of the   referral                                                       |          |     Options   - "Yes", "No"    |     Mandatory    |     Composition.section.text    |
|     Red Flag Details                                                                                |     Details   captured as to the Clinical Red Flags identified if the redflags were   identified as "Yes"                                                         |          |     Free   text data entry     |     Mandatory    |     Composition.section.text    |
|     Consultation Pharmacist Notes                                                                   |     Consultation   notes from the pharmacist consultation, in addition to that captured from the   referring organisation referral discussion with the patient    |          |     Free   text data entry     |     Mandatory    |     Composition.section.text    |
|     Consultation Outcome                                                                           |     The   Patient outcome of the referral to Community Pharmacy                                                                                                   |          |                                |     Mandatory    |     Composition.section.text    |
|     Consent For Onward Referral                                                                      |     Confirmation   of consent for onward referral to Pharmacy                                                                                                     |          |     Options   - "Yes", "No"    |     Mandatory    |     Composition.section.text    |
|     GP Notification Form -   Referrals for low acuity/minor illness: notification status          |     Confirmation   audit trail that the Post Event Message (PEM ) has been sent to the patient's   GP Practice once the referral is recorded as "Completed"       |          |                                |     Mandatory    |     Composition.section.text    |
|     Incident                                                                                      |     Record   of whether the pharmacy is logging feedback on the referral which relates to   an incident (or potential incident)                                   |          |     Options   - "Yes", "No"    |     Mandatory    |     Composition.section.text    |
|     Incident Pharmacist Feedback                                                                    |     Details   captured of the incident feedback reported as "Yes"                                                                                                 |          |     Free   text data entry     |     Mandatory    |     Composition.section.text    |
|     Survey Consent                                                                                 |     Capturing   of consent to participate in a patient survey on the Service                                                                                      |          |     Options   - "Yes", "No"    |     Mandatory    |     Composition.section.text    |
|     Patient Survey information:   notification status                                             |     Confirmation   audit trail that the Patient Survey has been sent to the patient                                                                               |          |                                |     Mandatory    |     Composition.section.text    |

## Example Clinical Narrative Section ##

{% include note.html content="These examples have not been clinically assured against Digital Medicines use cases.<br/>Examples are illustrative only." %}

```
<!--<xml>-->
<!--Clinical Narrative-->
	<section>
		<title value="Clinical Narrative"/>
		<code>
			<coding>
				<system value="http://snomed.info/sct"/>
				<code value="1077901000000108"/>
				<display value="Clinical narrative"/>
			</coding>
		</code>
		<text>
			<status value="additional"/>
			<div xmlns="http://www.w3.org/1999/xhtml">
			<table width="100%">
				<tbody>
				<tr>
					<th>Clinical Narrative</th>
					<td>A description detailing a patient’s reason for attendance, any red flags, results from the diagnostic and treatment process.</td>
				</tr>
				</tbody>
			</table>
			</div>
		</text>
	</section>
<!--</xml>-->
```
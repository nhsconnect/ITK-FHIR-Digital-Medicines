---
title: Presenting Complaints
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_presenting_complaint_dmirs.html
summary: "Gives information about the Clinical Narrative section"
---

{% include custom/section.warnbanner.html %}

## Consent Section Content ##
The Consent section carries information about the consent details used. PRSB Elements should be formatted as subheadings in any HTML sent.


| PRESENTING   COMPLAINT OR ISSUES  |                                                                                                                                                                                                                                                                                                                    |             |                                                                    |                                  |                          |
|-----------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------|--------------------------------------------------------------------|----------------------------------|--------------------------|
| Data Item                         | Description                                                                                                                                                                                                                                                                                                        | Cardinality | Values                                                             | Mandatory/required/     optional | FHIR Target              |
| Presenting complaint or issue     | The   health problem or issue experienced by the patient resulting in their   attendance. This may include disease state, medical condition, response and   reactions to therapies. Eg, blackout, dizziness, chest pain, follow up from   admission, falls, a specific procedure, investigation or treatment.      | 0 TO MANY   | Free   text   ---- coded text (SNOMED drop   down as search entry) | Required                         | Composition.section.text |

## Example Clinical Narrative Section ##

```
<xml>
<!--Consent-->
	<section>
		<title value="Consent"/>
		<code>
			<coding>
				<system value="http://snomed.info/sct"/>
				<code value="61861000000100"/>
				<display value="Consent"/>
			</coding>
		</code>
		<text>
			<status value="additional"/>
			<div xmlns="http://www.w3.org/1999/xhtml">
			<table width="100%">
				<tbody>
				<tr>
					<th>Consent for treatment record</th>
					<td>Patient's consent for treatment has been attained.</td>
				</tr>
				<tr>
					<th>Consent for information sharing</th>
					<td>Patient is happy for the immunzation details to be shares with their Registered GP.</td>
				</tr>
				<tr>
					<th>Consent relating to child</th>
					<td>Not Applicable</td>
				</tr>
				</tbody>
			</table>
			</div>
		</text>
	</section>
</xml>
```

## Coded Resources ##

This text section should be linked to the following FHIR Resources to provide the textual information in a coded format.

- The Digital Medicines specification does not currently support coded consent details.
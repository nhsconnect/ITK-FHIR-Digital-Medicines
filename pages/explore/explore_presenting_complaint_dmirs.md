---
title: Presenting complaint or issue
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_presenting_complaint_dmirs.html
summary: "Gives information about the Presenting complaint or issue section"
---

{% include custom/section.warnbanner.html %}

## Presenting complaint or issue Section Content ##
The Presenting complaint or issue section carries information about the details used. PRSB Elements should be formatted as subheadings in any HTML sent.


| PRESENTING   COMPLAINT OR ISSUES  |                                                                                                                                                                                                                                                                                                                    |             |                                                                    |                                  |                          |
|-----------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------|--------------------------------------------------------------------|----------------------------------|--------------------------|
| Data Item                         | Description                                                                                                                                                                                                                                                                                                        | Cardinality | Values                                                             | Mandatory/required/     optional | FHIR Target              |
| Presenting complaint or issue     | The   health problem or issue experienced by the patient resulting in their   attendance. This may include disease state, medical condition, response and   reactions to therapies. Eg, blackout, dizziness, chest pain, follow up from   admission, falls, a specific procedure, investigation or treatment.      | 0 TO MANY   | Free   text   ---- coded text (SNOMED drop   down as search entry) | Required                         | Composition.section.text |

## Example Section ##

{% include note.html content="these examples have not been clinially assured against Digital Medicines use cases" %}

```
<!--<xml>-->
<!--Presenting complaint or issue-->
	<section>
		<title value="Presenting complaint or issue"/>
		<code>
			<coding>
				<system value="http://snomed.info/sct"/>
				<code value="886891000000102"/>
				<display value="Presenting complaints or issues"/>
			</coding>
		</code>
		<text>
			<status value="additional"/>
			<div xmlns="http://www.w3.org/1999/xhtml">
			<table width="100%">
				<tbody>
				<tr>
					<th>Presenting complaint or issue</th>
					<td>The health problem or issue experienced by the patient resulting in their attendance. This may include disease state, medical condition, response and reactions to therapies. Eg, blackout, dizziness, chest pain, follow up from admission, falls, a specific procedure, investigation or treatment.</td>
				</tr>
				</tbody>
			</table>
			</div>
		</text>
	</section>
<!--</xml>-->
```
---
title: Clinical Narrative
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_clinical_narrative_dmirs.html
summary: "Gives information about the Clinical Narrative section"
---

{% include custom/section.warnbanner.html %}

## Clinical Narrative Section Content ##
The Clinical Narrative section carries information about the Clinical Narrative details used. PRSB Elements should be formatted as subheadings in any HTML sent.


| CLINICAL   NARRATIVE |                                                                                                                                   |             |             |                                  |                          |
|----------------------|-----------------------------------------------------------------------------------------------------------------------------------|-------------|-------------|----------------------------------|--------------------------|
| Data Item            | Description                                                                                                                       | Cardinality | Values      | Mandatory/required/     optional | FHIR Target              |
| Clinical narrative   | A   description detailing a patient’s reason for attendance,  any red flags, results from the diagnostic   and treatment process. | 1 TO ONLY   | Free   text | Mandatory                        | Composition.section.text |

## Example Clinical Narrative Section ##

```
<!--<xml>-->
<!--Clinical Narrative-->
	<section>
		<title value="Clinical Narrative"/>
		<code>
			<coding>
				<system value="http://snomed.info/sct"/>
				<code value="TBC"/>
				<display value="TBC"/>
			</coding>
		</code>
		<text>
			<status value="additional"/>
			<div xmlns="http://www.w3.org/1999/xhtml">
			<table width="100%">
				<tbody>
				<tr>
					<th>Clinical Narrative</th>
					<td>TBC</td>
				</tr>
				</tbody>
			</table>
			</div>
		</text>
	</section>
<!--</xml>-->
```
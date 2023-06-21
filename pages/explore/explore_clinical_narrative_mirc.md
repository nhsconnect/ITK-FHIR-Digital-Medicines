---
title: Clinical Summary - NOW RETIRED
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_clinical_narrative_mirc.html
summary: "Gives information about the Clinical Summary section"
---

{% include warning.html content="The Minor Illness use case is now retired and you cannot implement it." %}

{% include custom/section.warnbanner.html %}

## Clinical Summary Section Content ##
The Clinical Summary section carries information about the Clinical Summary details used. PRSB Elements should be formatted as subheadings in any HTML sent.


| CLINICAL   NARRATIVE |                                                                                                                                   |             |             |                                  |                          |
|----------------------|-----------------------------------------------------------------------------------------------------------------------------------|-------------|-------------|----------------------------------|--------------------------|
| Data Item            | Description                                                                                                                       | Cardinality | Values      | Mandatory/required/     optional | FHIR Target              |
| Clinical Summary   | A description detailing a patient’s reason for attendance, results from the diagnostic and treatment process. | 1 ONLY   | Free   text | Mandatory                        | Composition.section.text |

## Example Clinical Summary Section ##

{% include note.html content="These examples have not been clinically assured against Digital Medicines use cases.<br/>Examples are illustrative only." %}

```
<!--<xml>-->
<!--Clinical Summary-->
	<section>
		<title value="Clinical Summary"/>
		<code>
			<coding>
				<system value="http://snomed.info/sct"/>
				<code value="887181000000106"/>
				<display value="Clinical Summary"/>
			</coding>
		</code>
		<text>
			<status value="additional"/>
			<div xmlns="http://www.w3.org/1999/xhtml">
			<table width="100%">
				<tbody>
				<tr>
					<th>Clinical Summary</th>
					<td>A description detailing a patient’s reason for attendance, results from the diagnostic and treatment process.</td>
				</tr>
				</tbody>
			</table>
			</div>
		</text>
	</section>
<!--</xml>-->
```
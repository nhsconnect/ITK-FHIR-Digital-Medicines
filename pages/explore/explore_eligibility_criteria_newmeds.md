---
title: Eligibility Criteria Section
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_eligibility_criteria_newmeds.html
summary: "Gives information about the Eligibility Criteria section"
---

{% include custom/section.warnbanner.html %}

## Eligibility Criteria Section Content ##
The Eligibility Criteria section carries information about the eligibility criteria. PRSB Elements should be formatted as subheadings in any HTML sent.

> **Eligibility criteria**
>> **When Implementing:**
* Vaccinations
* New Medicine Service
* Medication Review

Include element(s):

| ELIGIBILITY   CRITERIA |                                                                                 |             |                                                                                                                                              |                                  |                          |
|------------------------|---------------------------------------------------------------------------------|-------------|----------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------|--------------------------|
| Data Item              | Description                                                                     | Cardinality | Values                                                                                                                                       | Mandatory/required/     optional | FHIR Target              |
| Eligibility criteria   | Records   which specific eligibility criteria have been met for the service.    | 0   TO MANY | Free   text. This will be derived from the list of eligible criteria published at   the time as part of the pharmacy service specification.  | Required                         | Composition.section.text |

## Example Eligibility criteria Section ##

{% include note.html content="These examples have not been clinially assured against Digital Medicines use cases.<br/>Examples are illustrative only." %}

```
<!--<xml>-->
<!--Eligibility Criteria-->
	<section>
		<title value="Eligibility Criteria"/>
			<code>
				<coding>
					<system value="http://snomed.info/sct"/>
					<code value="61871000000107"/>
					<display value="Eligibility for treatment"/>
				</coding>
			</code>
			<text>
			<status value="additional"/>
			<div xmlns="http://www.w3.org/1999/xhtml">
				<table width="100%">
					<tbody>
					<tr>
						<th>Eligibility criteria</th>
					</tr>
					<tr>
						<td>
						<p>Patient has Chronic Obstructive Pulmonary Disease (COPD).</p>
						</td>
					</tr>
					</tbody>
				</table>
			</div>
			</text>
	</section>
<!--</xml>-->
```

## Coded Resources ##

This text section should be linked to the following FHIR Resources to provide the textual information in a coded format.

- The Digital Medicines specification does not currently support coded eligibility criteria.
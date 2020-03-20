---
title: Information and Advice Given Section
keywords:  messaging, sections
tags: [fhir,messaging,section]
sidebar: foundations_sidebar
permalink: explore_information_and_advice_given.html
summary: "Gives information about the Information and Advice Given section"
---

{% include custom/section.warnbanner.html %}

## Information and Advice Given Section Content ##
The Information and advice given section carries details about the information and advice given. PRSB Elements should be formatted as subheadings in any HTML sent.

| INFORMATION   AND ADVICE GIVEN |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |             |                                                                                            |                                  |                          |
|--------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------|--------------------------------------------------------------------------------------------|----------------------------------|--------------------------|
| Data   Item                    | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | Cardinality | Values                                                                                     | Mandatory/required/     optional | FHIR Target              |
| Information and advice given   | This   includes     – what information (including health promotional messages)     – to whom it was given.          The oral or written information or advice given to the patient,     carer, other authorised representative, care professional or other third   party. May include advice about actions related to     medicines or other ongoing care activities on an ‘information     prescription’. State here if there are concerns about the extent     to which the patient and/or carer understands the information     provided about diagnosis, prognosis and treatment. | 0 TO MANY   | Free   text description of information and advice given and patient/carer   comprehension. | Required                         | Composition.section.text |

##  Example Information and Advice Given Section ##

{% include note.html content="These examples have not been clinially assured against Digital Medicines use cases.<br/>Examples are illustrative only." %}

```
<!--<xml>-->
<!--Information and advice given-->
	<section>
	<title value="Information and advice given"/>
		<code>
			<coding>
				<system value="http://snomed.info/sct"/>
				<code value="1052951000000105"/>
				<display value="Information and advice given"/>
			</coding>
		</code>
		<text>
		<status value="additional"/>
		<div xmlns="http://www.w3.org/1999/xhtml">
		<table width="100%">
			<tbody>
				<tr>
					<th>Information and advice given</th>
					<td>
					<p>Patient advised the side effects of the vaccine and requested to see their registered GP if any of the symptoms last longer than the expected duration.</p>
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

- The Digital Medicines specification does not currently support coded information and advice given.

 









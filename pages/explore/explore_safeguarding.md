---
title: Safeguarding
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_safeguarding.html
summary: "Gives information about safeguarding concerns"
---

{% include custom/section.warnbanner.html %}

## Safeguarding Section Content ##
Details of safeguarding concerns.<br/><br/>There may be 0 TO MANY safeguarding entries under a section. Each record entry is made up of a number of the elements or data items below.


| SAFEGUARDING  |                                                                                                                                                                                                                                                                                                                    |             |                                                                    |                                  |                          |
|-----------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------|--------------------------------------------------------------------|----------------------------------|--------------------------|
| Data Item        | Description   | Cardinality | Values       | Mandatory/required/     optional | FHIR Target              |
| Safeguarding indicator     |Indicates whether or not the hospital considers that there are safeguarding issues associated with the patient. | 0 TO 1 | Flag: No =N: Yes = Y  | Required| [Presence of a Flag resource]
| Safeguarding concerns     | Identified safeguarding concerns   | 0 TO 1   | Either coded or free text. If coded, then values from SNOMED CT  ^999002381000000108 Safeguarding issues simple reference set (foundation metadata concept) | Required | Flag.code or Flag.code.text |
| Comment | Further details on safeguarding concerns. | 0 TO 1 |Free text | Required | Composition.section.text |

## Example Section ##

{% include note.html content="These examples have not been clinically assured against Digital Medicines use cases.<br/>Examples are illustrative only." %}

```
<!--<xml>-->
<!--safeguarding-->
	<section>
		<title value="Safeguarding"/>
		<code>
			<coding>
				<system value="http://snomed.info/sct"/>
				<code value="1077911000000105"/>
				<display value="Safeguarding"/>
			</coding>
		</code>
		<text>
			<status value="additional"/>
			<div xmlns="http://www.w3.org/1999/xhtml">
			<table width="100%">
				<tbody>
				<tr>
					<th>Safeguarding indicator</th>
					<td>Yes</td>
				</tr>
				<tr>
					<td>Safeguarding concerns</td>
					<td>Family is cause for concern</td>
				</tr>
				<tr>
					<td>Comment</td>
					<td>During consultation patient opened up about activities of direct family.</td>
				</tr>
				</tbody>
			</table>
			</div>
		</text>
		<!-- if coded data included, this links to the coded Flag -->
		<entry>
			<reference value="urn:uuid:9f1f81a1-f1f1-4fcf-b89f-c1acf73a1329"/>
		</entry>
	</section>
<!--</xml>-->
```

## Example Coding ##
```
<!--<xml>-->
<!-- Flag -->
<entry>
	<fullUrl value="urn:uuid:9f1f81a1-f1f1-4fcf-b89f-c1acf73a1329"/>
	<resource>
		<Flag>
			<id value="9f1f81a1-f1f1-4fcf-b89f-c1acf73a1329"/>
			<meta>
				<profile value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Flag-1"/>
			</meta>
			<!-- status is mandatory -->
			<status value="active"/>
			<!-- safeguarding concern -->
			<code>
				<coding>
					<code value="300731000000106"/>
					<system value="http://snomed.info/sct"/>
					<display value="Family is cause for concern"/>
				</coding>
			</code>
			<!-- if using free text rather than coded
			<code>
				<text value="Family is cause for concern"/>
			</code> -->				
			<subject>
				<reference value="urn:uuid:9af701f7-5eb2-4402-bb3c-8ef8c8190082"/>
			</subject>				
		</Flag>
	</resource>
</entry>

<!--</xml>-->
```

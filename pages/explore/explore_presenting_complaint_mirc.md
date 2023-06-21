---
title: Presenting complaint or issue - NOW RETIRED
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_presenting_complaint_mirc.html
summary: "Gives information about the Presenting complaint or issue section"
---

{% include warning.html content="The Minor Illness use case is now retired and you cannot implement it." %}

{% include custom/section.warnbanner.html %}

## Presenting complaint or issue Section Content ##
The Presenting complaint or issue section carries information about the details used. PRSB Elements should be formatted as subheadings in any HTML sent.


| PRESENTING   COMPLAINT OR ISSUES  |                                                                                                                                                                                                                                                                                                                    |             |                                                                    |                                  |                          |
|-----------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------|--------------------------------------------------------------------|----------------------------------|--------------------------|
| Data Item                         | Description                                                                                                                                                                                                                                                                                                        | Cardinality | Values                                                             | Mandatory/required/     optional | FHIR Target              |
| Presenting complaint or issue     | The   health problem or issue experienced by the patient resulting in their attendance. This may include disease state, medical condition, response and   reactions to therapies. Eg, blackout, dizziness, chest pain, follow up from   admission, falls, a specific procedure, investigation or treatment.      | 0 TO MANY   | A coded value from SNOMED-CT (^1127581000000103 - Health issues simple reference set).<br/>If no code exists, Free Text may be used | Required                         | Condition.code |

## Example Section ##

{% include note.html content="These examples have not been clinically assured against Digital Medicines use cases.<br/>Examples are illustrative only." %}

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
					<td>Burn of ear</td>
				</tr>
				</tbody>
			</table>
			</div>
		</text>
		<entry>
			<reference value="urn:uuid:be79bf3e-baec-4d99-91e8-1d851e6fec7f"/>
		</entry>		
	</section>
	
<!-- further sections -->	
	
<!-- coded data -->
<entry>
	<fullUrl value="urn:uuid:be79bf3e-baec-4d99-91e8-1d851e6fec7f"/>
	<resource>
		<Condition xmlns="http://hl7.org/fhir">
			<clinicalStatus value="active"/> 
			<code> 
				<coding> 
					<system value="http://snomed.info/sct"/> 
					<code value="39065001"/> 
					<display value="Burn of ear"/> 
				</coding> 
			</code> 
			<subject>
				<reference value="urn:uuid:9af701f7-5eb2-4402-bb3c-8ef8c8190082"/>
			</subject>
		</Condition> 
	</resource>
</entry>

<!--</xml>-->
```

## Coded Resources ##

[CareConnect-ITK-Condition-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Condition-1)
---
title: History Section
keywords:  messaging, sections
tags: [fhir,messaging,sections]
sidebar: foundations_sidebar
permalink: explore_history.html
summary: "Gives information about the History section"
---

{% include custom/section.warnbanner.html %}

## History Section Content ##
The History section carries history related to the patient's previous care. Elements should be rendered as subheadings in any HTML sent.

| HISTORY                                                   |                                                                                                                                                                                                                                                                   |             |                                                                                                                                                      |                                  |                          |
|-----------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------|------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------|--------------------------|
| Data Item                                                 | Description                                                                                                                                                                                                                                                       | Cardinality | Values                                                                                                                                               | Mandatory/required/     optional | FHIR Target              |
| Relevant past medical, surgical and mental health history | The   record of the person’s significant medical, surgical and mental health   history. Including relevant previous diagnoses, problems and issues,   procedures, investigations, specific anaesthesia issues, etc (will include   dental and obstetric history). | 0   TO 1    | History   pertinent to the emergency supply of medicine e.g. contraindications,   pregnancy, immunosupression. May be a SNOMED CT term or free text. | Required                         | Composition.section.text |
|     Medical History                             |     Some   summary of the patient'srecent and relevant medical history. Summary only.   Pharmacist will need to access SCR and not rely on this summary                |          |          |     Mandatory    |     Composition.section.text    |
|     Relevant Information                        |     Notes   from the referring organisation referral that may be relevant to the   consultation. Supports the medical history                                          |          |          |     Mandatory    |     Composition.section.text    |
|     Other Details                               |     Additional   information relating to the referral & presenting complaint, captured by   the the referring organisation initial referral.                           |          |          |     Mandatory    |     Composition.section.text    |
|     Prescribed Meds Already Taken                |     Additional   notes on Medicines already taken from the referring organisation referral   that may be relevant to the consultation. Supports the medical history    |          |          |     Mandatory    |     Composition.section.text    |
|     Over the counter (OTC)   RemediesToDate    |     Additional   notes on remedies to date from the referring organisation referral that may   be relevant to the consultation. Supports the medical history           |          |          |     Mandatory    |     Composition.section.text    |
|     Associated Symptoms                         |     Additional   notes on Associated symptoms from the referring organisation referral that   may be relevant to the consultation. Supports the medical history        |          |          |     Mandatory    |     Composition.section.text    |
|     Other Symptoms                              |     Additional   notes on other symptoms from the referring organisation referral that may be   relevant to the consultation. Supports the medical history             |          |          |     Mandatory    |     Composition.section.text    |

##  Example History Section ##

{% include note.html content="These examples have not been clinically assured against Digital Medicines use cases.<br/>Examples are illustrative only." %}

```
<!--<xml>-->
<!--History-->
	<section>
	<title value="History"/>
		<code>
			<coding>
				<system value="http://snomed.info/sct"/>
				<code value="717121000000105"/>
				<display value="History"/>
			</coding>
		</code>
		<text>
		<status value="additional"/>
		<div xmlns="http://www.w3.org/1999/xhtml">
		<table width="100%">
			<tbody>
			<tr>
				<th>Relevant past medical, surgical and mental health history</th>
				<td>
				<p>Patient has Chronic Obstructive Pulmonary Disease (COPD). She was advised to have the flu vaccination as she is at greater risk from flu and its complications when she last attended her GP Practice.</p>
				<p>Patient requested the vaccination.</p>
				<p>No history of vaccination recorded at Pharmacy.</p>
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

- [Condition](build_conditions.html)
- [Procedure](build_procedures.html)






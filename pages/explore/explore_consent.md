---
title: Legal information Section
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_consent.html
summary: "Gives information about the Legal information section"
---

{% include custom/section.warnbanner.html %}

## Legal information Section Content ##
The Legal information section carries information about the consent details used. PRSB Elements should be formatted as subheadings in any HTML sent.

| CONSENT                          |                                                                                                                                                                                                                                                                    |             |                                                                                                                                                                                              |                                  |                          |
|----------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------|--------------------------|
| Data Item                        | Description| Cardinality | Values | Mandatory/required/     optional | FHIR Target              |
| Legal information for treatment record     | Whether   consent has been obtained for the treatment. May include where record of   consent is located or record of consent.                                                                                                                                      | 0   TO 1    | Free   text.| <font color="red">Optional</font>                         | Composition.section.text |
|Legal information for treatment record _(for MIRC)_|Indication from the referring organisation as to whether consent has been granted for the referral by the patient in line with referring organisation consent guidelines.||options - "Yes", "implied"|Mandatory|Composition.section.text|
| Legal information for information sharing  | This   is a record of consent for information sharing under the common law duty of   confidentiality. Where consent has not been obtained or sought, the reason   why should be provided. Include best interests decision where person lacks   capacity            | 0   TO 1    |  • Text      • Refset: Document consent simple   reference set (foundation metadata concept) Refset Id :   999000731000000109  https://dd4c.digital.nhs.uk/dd4c/ publishedmetadatas/intid/66. | <font color="red">Optional</font>                         | Composition.section.text |
| Legal information relating to child        | Consideration   of age and competency, applying Gillick competency or Fraser guidelines.   Record of person with parental responsibility or appointed guardian where   child lacks competency. Record if there is disagreement between patient and   parent.       | 0   TO 1    | Free   text.                                                                                                                                                                                 | <font color="red">Optional</font>                         | Composition.section.text |

## Example Legal information Section ##

{% include note.html content="These examples have not been clinically assured against Digital Medicines use cases.<br/>Examples are illustrative only." %}

```
<!--<xml>-->
<!--Legal information-->
	<section>
		<title value="Legal information"/>
		<code>
			<coding>
				<system value="http://snomed.info/sct"/>
				<code value="61861000000100"/>
				<display value="Legal information"/>
			</coding>
		</code>
		<text>
			<status value="additional"/>
			<div xmlns="http://www.w3.org/1999/xhtml">
			<table width="100%">
				<tbody>
				<tr>
					<th>Legal information for treatment record</th>
					<td>Patient's consent for treatment has been attained.</td>
				</tr>
				<tr>
					<th>Legal information for information sharing</th>
					<td>Patient is happy for the immunzation details to be shares with their Registered GP.</td>
				</tr>
				<tr>
					<th>Legal information relating to child</th>
					<td>Not Applicable</td>
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

- The Digital Medicines specification does not currently support coded consent details.
---
title: GP Practice Section
keywords:  messaging, sections
tags: [fhir,messaging,section]
sidebar: foundations_sidebar
permalink: explore_gp_practice.html
summary: "Gives information about the GP Practice section"
---
{% include custom/section.warnbanner.html %}


## GP Practice Section Content ##

The GP practice section contains details of the patients GP practice. PRSB Elements should be formatted as subheadings in any HTML sent.
 
| GP   PRACTICE          |                                                 |             |                                                                                                                                                                                            |                                  |                         |
|------------------------|-------------------------------------------------|-------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------|-------------------------|
| Data   Item            | Description                                     | Cardinality | Values                                                                                                                                                                                     | Mandatory/required/     optional | FHIR Target             |
| GP practice identifier | The   identifier of the registered GP practice. | 1   ONLY    | This   should be the Organisation Data Services (ODS) identifier for the practice   (not displayed in the message). This includes codes to use where there is no   registered GP practice. | Mandatory                        | Organization.identifier |
 
## Example GP Practice Section ##

{% include note.html content="These examples have not been clinically assured against Digital Medicines use cases.<br/>Examples are illustrative only." %}

```
<!--<xml>-->
<!-- GP Practice-->
	<section>
		<title value="GP practice"/>
			<code>
				<coding>
					<system value="http://snomed.info/sct"/>
					<code value="886711000000101"/>
					<display value="GP practice"/>
				</coding>
			</code>
			<text>
			<status value="additional"/>
			<div xmlns="http://www.w3.org/1999/xhtml">
			<table width="100%">
				<tbody>
				<tr>
					<th>GP practice identifier</th>
					<td>
						<p>ODS Organization Code:GP123456</p>
					</td>
				</tr>
				</tbody>
			</table>
			</div>
			</text>
		<!--Reference to the Organisation entry as the source of information for this section-->
		<entry>
			<reference value="urn:uuid:94ca030c-03aa-4dae-8270-c2de2b7907ef"/>
		</entry>
	</section>
<!--</xml>-->
```
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


<table style="width:100%;max-width: 100%;">
	<thead>
		<tr>
			<th width="15%">Section</th>
			<th width="35%">Description</th>
			<th width="5%">Card.</th>
			<th width="5%">MRO*</th>
			<th width="40%">FHIR Target and Guidance</th>
		</tr>
	</thead>
 <tbody>
  <tr>
   <td>Information and advice given</td>
   <td>A record of any information or advice given to the patient, carer or relevant third party.</td>
   <td>0 to 1</td>
   <td>M</td>
			<td>Carried in the CodeableConcept of <b>Composition.section.code</b> FHIR element.</td>
  </tr>
		<tr>
			<th>PRSB Element</th>
			<th>Description</th>
			<th>Card.</th>
			<th>MRO*</th>
			<th>FHIR Target and Guidance</th>		
		</tr>
  <tr>
   <td>Information and advice given</td>
   <td>This includes<br/>
– what information (including health promotional messages)<br/>
– to whom it was given.<br/>
<br/>
The oral or written information or advice given to the patient,
carer, other authorised representative, care professional or other third party. May include advice about actions related to
medicines or other ongoing care activities on an ‘information
prescription’. State here if there are concerns about the extent
to which the patient and/or carer understands the information
provided about diagnosis, prognosis and treatment.</td>
   <td>0 to many</td>
   <td>R</td>
   <td>Free text description of information and advice given and patient/carer comprehension.</td>
   </tr>
		<tr>
		<td colspan="5"><b>* M=Mandatory R=Required O=Optional</b></td>
		</tr>
 </tbody>
</table>


##  Example Information and Advice Given Section ##

```
<xml>
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
</xml>
```

## Coded Resources ##

This text section should be linked to the following FHIR Resources to provide the textual information in a coded format.

- The Digital Medicines specification does not currently support coded information and advice given.

 









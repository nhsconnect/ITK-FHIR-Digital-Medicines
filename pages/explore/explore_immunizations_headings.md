---
title: Digital Medicines Immunization Administration Headings
keywords:  messaging
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_immunizations_headings.html
summary: "Overview of the Pharmacy Immunization Administration notification headings"
---


{% include custom/section.warnbanner.html %}

## Overview ##

This section provides a list of the PRSB headings used for text sections in the ITK3 FHIR Digital Medicines Immunizations notification based on the "Standards for the clinical structure and content of patient records" documentation. 

This section lists the following

- The headings used
- An overview of the type of information carried within the text section
- An example of a text section instance
- A list of the coded resources which may be used to give the text carried in the section in a coded format. 


## Immunization Sections and Coded profiles ##
This diagram illustrates the sections used in Digital Medicines Immunizations document and which sections allow coded representation of the section text.

<a href="images/explore/digital_meds_immunization_composition_overview.png" target="_blank" style="width: 100%;max-width: 100%;"><b>Click to open in a new window</b></a>

<img src="images/explore/digital_meds_immunization_composition_overview.png" style="width:auto;height: auto;"/>


The text sections are carried in the FHIR Composition Resource. 

This is profiled as the [ITK-DM-Composition](https://fhir.nhs.uk/STU3/StructureDefinition/ITK-DM-Composition-1)


 
## Typical Text Section Content ##
This diagram shows the elements of a typical text section which is found in the FHIR Composition Resource.
Note: the examples of section HTML in this specification show only example HTML format such as tables. This is an exemplar format. There is no mandated format for the section HTML. 

<img src="images/explore/section_description.png" style="width:90%;max-width: 90%;">
## Must Support Property ##
Some elements in the Composition Resource used within ITK3 Transfer of Care documents have the must support property set to "true".  
These are :
- Composition.encounter
- Composition.custodian
- Composition.section(slice) sections: Attendance details, Consent

The “must support” property has been added to all the elements that must be supported regardless of cardinality.  Whether the conformance of the element is mandatory or optional has no relevance for the “must support” property. This means that for sending or receiving systems to claim conformance to any ITK3 Transfer of Care Composition Profile the following MUST be true:

- The sending system MUST support the creation and sending of all the elements in the list above.
- The sending system MUST support the creation and sending of all Composition.section slices with the specified sub-elements and narrative.* See Note 1. 
- The receiving system MUST support the processing of all the elements in the list above.  
- The receiving system MUST support the display of all Composition.section slices with the specified sub-elements and narrative.

**Note 1** - There are rules around when sections are sent or not sent in a document. These are specified in the document headings sections.


## Headings Used By Immunization Administration Document ##

<table>
	<tr>
		<th width="40%">Section Name</th>
		<th width="20%">SNOMED Concept</th>
		<th width="13%">Cardinality</th>
		<th width="13%">Conformance</th>
		<th width="13%">Associated Coded Profiles</th>
	</tr>
	<tr>
		<td>
			<a href="explore_allergies_and_adverse_reactions.html">Allergies and adverse reactions</a>
		</td>
		<td>886921000000105</td>
		<td>0..1</td>
		<td>Optional</td>
		<td>1</td>
	</tr>
	<tr>
		<td>
			<a href="explore_attendance_details.html">Attendance details</a>
		</td>
		<td>1077881000000105</td>
	    <td>0..1</td>
		<td>Required</td>	
		<td>1</td>
	</tr>

	<tr>
		<td>
			<a href="explore_consent.html">Consent</a>
		</td>
		<td>cons</td>
    	<td>0..1</td>
		<td>Required</td>
		<td>0</td>
	</tr>
	<tr>
		<td>
			<a href="explore_eligibility_criteria.html">Eligibility criteria</a>
		</td>
		<td>eligcrit</td>
    	<td>0..1</td>
		<td>Optional</td>
		<td>1</td>
	</tr>
	<tr>
		<td>
			<a href="explore_gp_practice.html">GP practice</a>
		</td>
		<td>886711000000101</td>
    	<td>1..1</td>
		<td>Mandatory</td>
		<td>1</td>
	</tr>
	<tr>
		<td>
			<a href="explore_immunizations.html">Immunizations</a>
		</td>
		<td>imms</td>
    	<td>1..*</td>
		<td>Mandatory</td>
		<td>0</td>
	</tr>
	<tr>
		<td>
			<a href="explore_information_and_advice_given.html">Information and advice given</a>
		</td>
		<td>1052951000000105</td>
    	<td>0..1</td>
		<td>Optional</td>
		<td>0</td>
	</tr>
	<tr>
		<td>
			<a href="explore_patient_demographics.html">Patient demographics</a>
		</td>
		<td>886731000000109</td>
    	<td>1..1</td>
		<td>Mandatory</td>
		<td>1</td>
	</tr>
</table>





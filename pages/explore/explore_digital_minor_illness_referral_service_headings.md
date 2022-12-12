---
title: Digital Medicines DMIRS Headings
keywords:  messaging
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_digital_minor_illness_referral_service_headings.html
summary: "Overview of the Pharmacy DMIRS Headings notification"
---


{% include custom/section.warnbanner.html %}


## Overview ##

This section provides a list of the PRSB headings used for text sections in the ITK3 FHIR Digital Medicines DMIRS Headings notification based on the "Standards for the clinical structure and content of patient records" documentation. 

This section lists the following

- The headings used
- An overview of the type of information carried within the text section
- An example of a text section instance
- A list of the coded resources which may be used to give the text carried in the section in a coded format. 


## DMIRS Sections and Coded profiles ##
This diagram illustrates the sections used in Digital Medicines DMIRS Headings document and which sections allow coded representation of the section text.

<a href="images/explore/digital_medicine_emergency_supply_composition_overview.png" target="_blank" style="width: 100%;max-width: 100%;"><b>Click to open in a new window</b></a>

<img src="images/explore/digital_medicine_emergency_supply_composition_overview.png" style="width:auto;height: auto;"/>


The text sections are carried in the FHIR Composition Resource. 

This is profiled as the [CareConnect-ITK-DM-EmergencySupply-Composition](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-DM-EmergencySupply-Composition-1)


 
## Typical Text Section Content ##
This diagram shows the elements of a typical text section which is found in the FHIR Composition Resource.
Note: the examples of section HTML in this specification show only example HTML format such as tables. This is an exemplar format. There is no mandated format for the section HTML. 

<img src="images/explore/section_description_1.png" style="width:90%;max-width: 90%;">
## Must Support Property ##
Some elements in the Composition Resource used within ITK3 Digital Medicines documents have the "mustSupport" property set to "true".  
These are :
- Composition.encounter
- Composition.custodian
- Composition.section(slice) sections: Contacts with professionals, Legal information, History, Information and advice given, Plan and requested actions and Referrer details

The “mustSupport” property has been added to all the elements that must be supported regardless of cardinality.  Whether the conformance of the element is mandatory or optional has no relevance for the “mustSupport” property. This means that for sending or receiving systems to claim conformance to any ITK3 Digital Medicines Composition Profile the following MUST be true:

- The sending system MUST support the creation and sending of all the elements in the list above.
- The sending system MUST support the creation and sending of all Composition.section slices with the specified sub-elements and narrative.* See Note 1. 
- The receiving system MUST support the processing of all the elements in the list above.  
- The receiving system MUST support the display of all Composition.section slices with the specified sub-elements and narrative.

**Note 1** - There are rules around when sections are sent or not sent in a document. These are specified in the document headings sections.


## Headings Used By DMIRS Headings Document ##

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
			<a href="explore_contacts_professionals.html">Contacts with professionals</a>
		</td>
		<td>contacts-with-professionals</td>
	    <td>0..1</td>
		<td>Required</td>	
		<td>1</td>
	</tr>	
	<tr>
		<td>
			<a href="explore_clinical_narrative_mirc.html">Clinical Summary</a>
		</td>
		<td>887181000000106</td>
    	<td>0..1</td>
		<td>Required</td>
		<td>0</td>
	</tr>	
	<tr>
		<td>
			<a href="explore_legal_information.html">Legal information</a>
		</td>
		<td>886961000000102</td>
    	<td>0..1</td>
		<td>Required</td>
		<td>0</td>
	</tr>
	<tr>
		<td>
			<a href="explore_distribution_list.html">Distribution list</a>
		</td>
		<td>887261000000109</td>
    	<td>0..1</td>
		<td>Required</td>
		<td>7</td>
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
			<a href="explore_history.html">History</a>
		</td>
		<td>717121000000105</td>
    	<td>0..1</td>
		<td>Required</td>
		<td>0</td>
	</tr>
	<tr>
		<td>
			<a href="explore_information_and_advice_given.html">Information and advice given</a>
		</td>
		<td>1052951000000105</td>
    	<td>0..1</td>
		<td>Required</td>
		<td>0</td>
	</tr>
	<tr>
		<td>
			<a href="explore_medication_dmirs.html">Medications and medical devices</a>
		</td>
		<td>933361000000108</td>
    	<td>1..1</td>
		<td>Mandatory</td>
		<td>2</td>
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
	<tr>
		<td>
			<a href="explore_plan_req_actions_ES.html">Plan and requested actions</a>
		</td>
		<td>887201000000105</td>
    	<td>0..1</td>
		<td>Required</td>
		<td>0</td>
	</tr>
	<tr>
		<td>
			<a href="explore_presenting_complaint_dmirs.html">Presenting complaint or issue</a>
		</td>
		<td>886891000000102</td>
    	<td>0..1</td>
		<td>Required</td>
		<td>0</td>
	</tr>
	<tr>
		<td>
			<a href="explore_referral_details.html">Referral details</a>
		</td>
		<td>886721000000107</td>
    	<td>0..1</td>
		<td>Required</td>
		<td>0</td>
	</tr>
</table>
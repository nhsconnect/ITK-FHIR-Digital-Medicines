---
title: Digital Medicines Headings
keywords:  messaging
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_headings.html
summary: "Overview of the Digital Medicines headings"
---

{% include warning.html content="The following document headings are now retired:<br/>
* Headings Used By New Medicine Service Document<br/>
* Headings Used By Medication Review Headings Document<br/>
* Headings Used By Appliance Use Review Document" %}

{% include custom/section.warnbanner.html %}

## Overview ##

This section provides a list of the PRSB headings used for text sections in the ITK3 FHIR Digital Medicines Vaccinations notification based on the "Standards for the clinical structure and content of patient records" documentation. 

This section lists the following

- The headings used
- An overview of the type of information carried within the text section
- An example of a text section instance
- A list of the coded resources which may be used to give the text carried in the section in a coded format. 

## Typical Text Section Content ##
This diagram shows the elements of a typical text section which is found in the FHIR Composition Resource.
Note: the examples of section HTML in this specification show only example HTML format such as tables. This is an exemplar format. There is no mandated format for the section HTML.

{% include important.html content="Unstructured Data (in the Composition.section.text elements) MUST be kept aligned with the underlying structured data in the relevant resources.<br/><br/>Additional unstructured data added to the Composition.section.text narratives MUST comply with the guidance defined in the Message Headings section." %}

<img src="images/explore/section_description_1.png" style="width:90%;max-width:90%;">

## Must Support Property ##
Some elements in the Composition Resource used within ITK3 Digital Medicines documents have the "mustSupport" property set to "true".  
These are :
- Composition.encounter
- Composition.custodian
- Composition.section(slice) sections: Contacts with professionals, Legal information, Referrer details

The “mustSupport” property has been added to all the elements that must be supported regardless of cardinality.  Whether the conformance of the element is mandatory or optional has no relevance for the “mustSupport” property. This means that for sending or receiving systems to claim conformance to any ITK3 Digital Medicines Composition Profile the following MUST be true:

- The sending system MUST support the creation and sending of all the elements in the list above.
- The sending system MUST support the creation and sending of all Composition.section slices with the specified sub-elements and narrative.* See Note 2. 
- The receiving system MUST support the processing of all the elements in the list above.  
- The receiving system MUST support the display of all Composition.section slices with the specified sub-elements and narrative.

**Note 2** - There are rules around when sections are sent or not sent in a document. These are specified in the document headings sections.


## Headings used by Common Headings ##

These headings are common across all the Digital Medicines document types, so are documented once under the Common Headings menu. 

Each document may have specific requirements around common headings, for example Contacts with professionals has an additional “Person collecting the medicine” header when used for Emergency Supply & Minor illness referral consultation. These specific requirements are documented on each common header. 

Each document type may have supplementary headers that are found under the specific document types listed below

## Headings Used By Vaccinations Administration Document ##

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
			<a href="explore_attendance_details.html">Contacts with professionals</a>
		</td>
		<td>1077881000000105</td>
	    <td>0..1</td>
		<td>Required</td>	
		<td>1</td>
	</tr>
	<tr>
		<td>
			<a href="explore_consent.html">Legal information</a>
		</td>
		<td>61861000000100</td>
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
			<a href="explore_eligibility_criteria_vacc.html">Eligibility criteria</a>
		</td>
		<td>61871000000107</td>
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
			<a href="explore_history.html">History</a>
		</td>
		<td>717121000000105</td>
    	<td>0..1</td>
		<td>Optional</td>
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
	<tr>
		<td>
			<a href="explore_referral_details.html">Referral details</a>
		</td>
		<td>886721000000107</td>
    	<td>0..1</td>
		<td>Required</td>
		<td>0</td>
	</tr>
	<tr>
		<td>
			<a href="explore_vaccinations.html">Vaccinations</a>
		</td>
		<td>1102181000000102</td>
    	<td>1..*</td>
		<td>Mandatory</td>
		<td>0</td>
	</tr>
</table>

## Headings Used By Emergency Supply Document ##

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
			<a href="explore_attendance_details.html">Contacts with professionals</a>
		</td>
		<td>1077881000000105</td>
	    <td>0..1</td>
		<td>Required</td>	
		<td>1</td>
	</tr>	
	<tr>
		<td>
			<a href="explore_consent.html">Legal information</a>
		</td>
		<td>61861000000100</td>
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
			<a href="explore_medication_ES.html">Medications and medical devices</a>
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
			<a href="explore_referral_details.html">Referral details</a>
		</td>
		<td>886721000000107</td>
    	<td>0..1</td>
		<td>Required</td>
		<td>0</td>
	</tr>
</table>

## Headings Used By New Medicine Service Document - NOW RETIRED ##

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
			<a href="explore_attendance_details.html">Contacts with professionals</a>
		</td>
		<td>1077881000000105</td>
	    <td>0..1</td>
		<td>Required</td>	
		<td>1</td>
	</tr>	
	<tr>
		<td>
			<a href="explore_consent.html">Legal information</a>
		</td>
		<td>61861000000100</td>
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
			<a href="explore_eligibility_criteria_newmeds.html">Eligibility criteria</a>
		</td>
		<td>61871000000107</td>
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
			<a href="explore_history.html">History</a>
		</td>
		<td>717121000000105</td>
    	<td>0..1</td>
		<td>Required</td>
		<td>0</td>
	</tr>
	<tr>
		<td>
			<a href="explore_medication_newmeds.html">Medications and medical devices</a>
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
</table>

## Headings Used By Medication Review Headings Document - NOW RETIRED ##

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
			<a href="explore_attendance_details.html">Contacts with professionals</a>
		</td>
		<td>1077881000000105</td>
	    <td>0..1</td>
		<td>Required</td>	
		<td>1</td>
	</tr>	
	<tr>
		<td>
			<a href="explore_consent.html">Legal information</a>
		</td>
		<td>61861000000100</td>
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
			<a href="explore_eligibility_criteria_medrev.html">Eligibility criteria</a>
		</td>
		<td>61871000000107</td>
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
			<a href="explore_medication_medrev.html">Medications and medical devices</a>
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
			<a href="explore_referral_details.html">Referral details</a>
		</td>
		<td>886721000000107</td>
    	<td>0..1</td>
		<td>Required</td>
		<td>0</td>
	</tr>
</table>

## Headings Used By Minor illness referral consultation Headings Document ##

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
			<a href="explore_attendance_details.html">Contacts with professionals</a>
		</td>
		<td>1077881000000105</td>
	    <td>0..1</td>
		<td>Required</td>	
		<td>1</td>
	</tr>	
	<tr>
		<td>
			<a href="explore_clinical_narrative_dmirs.html">Clinical narrative</a>
		</td>
		<td>1077901000000108</td>
    	<td>0..1</td>
		<td>Required</td>
		<td>0</td>
	</tr>	
	<tr>
		<td>
			<a href="explore_consent.html">Legal information</a>
		</td>
		<td>61861000000100</td>
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

## Headings Used By Appliance Use Review Document - NOW RETIRED ##

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
			<a href="explore_appliances_appuse.html">Appliances</a>
		</td>
		<td>334251007</td>
    	<td>1..1</td>
		<td>Mandatory</td>
		<td>1</td>
	</tr>
	<tr>
		<td>
			<a href="explore_attendance_details.html">Contacts with professionals</a>
		</td>
		<td>1077881000000105</td>
	    <td>0..1</td>
		<td>Required</td>	
		<td>1</td>
	</tr>	
	<tr>
		<td>
			<a href="explore_consent.html">Legal information</a>
		</td>
		<td>61861000000100</td>
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
			<a href="explore_referral_details.html">Referral details</a>
		</td>
		<td>886721000000107</td>
    	<td>0..1</td>
		<td>Required</td>
		<td>0</td>
	</tr>
</table>

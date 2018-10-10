---
title: Eligibility Criteria Section
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_eligibility_criteria.html
summary: "Gives information about the Eligibility Criteria section"
---

{% include custom/section.warnbanner.html %}

## Eligibility Criteria Section Content ##
The Eligibility Criteria section carries information about the eligibility criteria. PRSB Elements should be formatted as subheadings in any HTML sent.


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
   <td>Eligibility criteria</td>
   <td>This acts as a container that holds all of the elements for each instance of a eligibility criteria entry.</td>
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
   <td>Eligibility criteria</td>
   <td>Records which specific eligibility criteria have been met in order to administer the vaccine.</td>
   <td>0 to Many</td>
   <td>R</td>
   <td>Free text. This will be derived from the list of eligible criteria published at the time as part of the pharmacy service specification.</td>
  </tr>
		<tr>
		<td colspan="5"><b>* M=Mandatory R=Required O=Optional</b></td>
		</tr>
 </tbody>
</table>


## Example Eligibility criteria Section ##

<script src="https://gist.github.com/IOPS-DEV/19c8063f90b45e8b2ee1f6d9edf96287.js"></script>

## Coded Resources ##

This text section should be linked to the following FHIR Resources to provide the textual information in a coded format.

- The Digital Medicines specification does not currently support coded eligibility criteria.
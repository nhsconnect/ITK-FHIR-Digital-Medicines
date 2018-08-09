---
title: Immunizations Section
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_immunizations.html
summary: "Gives information about the Immunizations section"
---

{% include custom/section.warnbanner.html %}

## Immunizations Section Content ##
The Immunizations section carries information about the immunization administered. PRSB Elements should be formatted as subheadings in any HTML sent.


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
   <td>Immunizations section</td>
   <td>This acts as a container that holds all of the elements for each instance of an vaccination entry.</td>
   <td>1 only</td>
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
   <td>Vaccine product</td>
   <td>Vaccine product administered.</td>
   <td>1 only</td>
   <td>M</td>
   <td>Text and if coding is available carried in the CodeableConcept of the <b>Immunization.vaccineCode</b> FHIR element.</td>
  </tr>
  <tr>
   <td>Vaccine procedure</td>
   <td>The vaccination that was given e.g. seasonal influenza vaccination.</td>
   <td>1 only</td>
   <td>M</td>
   <td>Text and if coding is available carried in the CodeableConcept of the <b>Immunization.extension(vaccinationProcedure)</b> FHIR element.</td>
  </tr>
  <tr>
   <td>Manufacturer</td>
   <td>Name of vaccine manufacturer</td>
   <td>0 to 1</td>
   <td>R</td>
   <td>Not required for Pharmacy to GP communication.</td>
  </tr>
  <tr>
   <td>Batch number</td>
   <td>The batch number of the vaccine product.</td>
   <td>0 to 1</td>
   <td>R</td>
   <td>Not required for Pharmacy to GP communication.</td>
  </tr>
  <tr>
   <td>Expiry date</td>
   <td>The date on which the vaccine will expire.</td>
   <td></td>
   <td></td>
   <td>Not required for Pharmacy to GP communication.</td>
  </tr>
 <tr>
   <td>Serialisation code</td>
   <td>A code that separately identifies two identical vaccines (i.e. same product, same batch).</td>
   <td>0 to 1</td>
   <td>O</td>
   <td>Derived from FMD code or free text.</td>
  </tr>
 <tr>
   <td>Site</td>
   <td>Body site vaccine was administered into.</td>
   <td>0 to 1</td>
   <td>R</td>
   <td>Text and if coding is available carried in the CodeableConcept of the <b>Immunization.site</b> FHIR element.</td>
  </tr>
 <tr>
   <td>Route</td>
   <td>How vaccine entered the body.</td>
   <td>0 to 1</td>
   <td>R</td>
   <td>Text and if coding is available carried in the CodeableConcept of the <b>Immunization.route</b> FHIR element.</td>
  </tr>
 <tr>
   <td>Indication</td>
   <td>The clinical indication or reason for administering the vaccine.</td>
   <td>0 to 1</td>
   <td>O</td>
   <td>Text and if coding is available carried in the CodeableConcept of the <b>Immunization.explanation.reason</b> FHIR element.</td>
  </tr>
 <tr>
   <td>Dose amount</td>
   <td>Amount of vaccine administered.</td>
   <td>0 to 1</td>
   <td>R</td>
   <td>This will be free text. Coded units of measure (from DM+D) <br> Guidance on how to use the dose amount field will follow.</td>
  </tr>
 <tr>
   <td>Dose sequence</td>
   <td>Nominal position in a series of vaccines.</td>
   <td>0 to 1</td>
   <td>R</td>
   <td>Not required for Pharmacy to GP communication.</td>
  </tr>
 <tr>
   <td>Administered by</td>
   <td>The name of the person who administered the vaccine, preferably in a structured format.</td>
   <td>1 only</td>
   <td>M</td>
   <td>Send as structured name, the receiver can form free text if needed. This will be carried in the FHIR element <b>Immunization.practitioner.actor</b>.</td>
  </tr>
 <tr>
   <td>Role</td>
   <td>The role of the person who administered the vaccine.</td>
   <td>0 to 1</td>
   <td>R</td>
   <td>The role may be held on the source system, be from an authoritative source such as SDS, or use an existing vocabulary such as the job role title (from the national workforce dataset). This will be carried in the FHIR element <b>Immunization.practitioner.role</b>.</td>
  </tr>
 <tr>
   <td>Professional identifier</td>
   <td>Professional identifier & regulatory body of the person who administered the vaccine</td>
   <td>0 to 1</td>
   <td>R</td>
   <td>GPhC number of the pharmacist(default in from the log in, in the system). This will be carried in the FHIR element <b>Immunization.practitioner.actor</b>.</td>
  </tr>
 <tr>
   <td>DateTime</td>
   <td>The date/time on which the vaccine was administered.</td>
   <td>0 to 1</td>
   <td>R</td>
   <td>The date/time as recorded by the pharmacy system. This will be carried in the FHIR element <b>Immunization.date</b>.</td>
  </tr>
		<tr>
		<td colspan="5"><b>* M=Mandatory R=Required O=Optional</b></td>
		</tr>
 </tbody>
</table>


## Example Immunization Section ##

<script src="https://gist.github.com/IOPS-DEV/e3f8338cef252ede9812669198d2fa71.js"></script>

## Coded Resources ##

This text section should be linked to the following FHIR Resources to provide the textual information in a coded format.

- Immunization
 

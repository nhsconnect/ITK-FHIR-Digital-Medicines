---
title: Attendance Details Section
keywords:  messaging, sections
tags: [fhir,messaging,section]
sidebar: foundations_sidebar
permalink: explore_attendance_details.html
summary: "Gives information about the Attendance Details section"
---

{% include custom/section.warnbanner.html %}

## Attendance Details Section Content ##
The Attendance details section carries information about Attendance details used. PRSB Elements should be formatted as subheadings in any HTML sent.


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
   			<td>Attendance details</td>
  			<td>The details of the patient contact.</td>
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
   			<td>Date and time of contact</td>
   			<td>Date and time of the appointment, contact or attendance.</td>
   			<td>1 only</td>
   			<td>M</td>
   			<td>The date as recorded by the pharmacy system and carried in the FHIR element <b>Encounter.period.start</b>.</td>
  		</tr>
  		<tr>
   			<td>Service</td>
   			<td>The service under which the vaccination was administered.</td>
   			<td>0 to 1</td>
   			<td>R</td>
   			<td>Coded entry e.g. seasonal influenza, travel vaccination, Hepatitis B vaccination etc. carried in the FHIR element <b>TBC</b>.</td>
  		</tr>
		<tr>
   			<td>Organisation name</td>
   			<td>The name, including the identifier, of the organisation where the medicine was supplied.</td>
   			<td>1 only</td>
   			<td>M</td>
   			<td>This would be generated from the ODS code and associated text. In the future the global location number (GLN) may be used - GS1 standard. Carried in the FHIR element <b>Encounter.serviceProvider</b> with a link to <b>CareConnect-Organization-1</b> (identifier and name).</td>
  		</tr>
		<tr>
   			<td>Organisation address</td>
   			<td>The address of the organisation where the medicine was supplied.</td>
   			<td>0 to 1</td>
   			<td>R</td>
   			<td>ODS standard but may be generated from the Directory of Services (DOS). Carried in the FHIR element <b>Encounter.serviceProvider</b> with a link to <b>CareConnect-Organization-1</b> (address).</td>
  		</tr>
		<tr>
   			<td>Organisation contact details</td>
   			<td>The contact details of the organisation where the medicine was supplied. For example a phone number, NHSmail address etc. Contact details are used to resolve queries about the record entry.</td>
   			<td>0 to many</td>
   			<td>R</td>
   			<td>ODS standard but may be generated from the Directory of Services (DOS). Carried in the FHIR element <b>Encounter.serviceProvider</b> with a link to <b>CareConnect-Organization-1</b> (telecom).</td>
  		</tr>
		<tr>
   			<td>Location of event</td>
   			<td>The location of where the vaccine was administered (if different from the organisation address).</td>
   			<td>0 to 1</td>
   			<td>R</td>
   			<td>Free text e.g. care homes, patient’s home etc.</td>
  		</tr>
		<tr>
   			<td>Reason for non-provision of service</td>
   			<td>The reason why the patient was not provided with the service e.g. declined, did not attend etc. </td>
   			<td>0 to 1</td>
   			<td>O</td>
   			<td>Free text e.g. did not attend, declined by patient or clinician etc. Maybe coded text in the future if a reference set is created.</td>
  		</tr>
		<tr>
   			<td>Clinician name</td>
   			<td>The name of the person providing the service, preferably in a structured format.</td>
   			<td>1</td>
   			<td>M</td>
   			<td>The person name as held on the source system. Where possible this should be broken down into its constituent parts (prefix, given name, family name, suffix).</td>
  		</tr>
		<tr>
   			<td>Role</td>
   			<td>The role of the person providing the service.</td>
   			<td>0 to 1</td>
   			<td>R</td>
   			<td>The role may be held on the source system, be from an authoritative source such as SDS, or use an existing vocabulary such as the job role title (from the national workforce dataset).</td>
  		</tr>
		<tr>
   			<td>Professional identifier</td>
   			<td>Professional identifier of the person providing the service.</td>
   			<td>0 to 1</td>
   			<td>R</td>
   			<td>The regulatory body and the identifier itself of the person held on the source system. e.g. GPhC number of the pharmacist.</td>
  		</tr>
		<tr>
   			<td>Person accompanying patient</td>
   			<td>Identify, where clinically relevant, others accompanying the patient, e.g. parent, relative or friend. Includes: Name, Relationship, Role (e.g.informal carer).</td>
   			<td>0 to many</td>
   			<td>O</td>
   			<td>Free text. Carried in the FHIR element <b>Encounter.participant</b>.</td>
  		</tr>
		<tr>
   			<td>Chaperone</td>
   			<td>The name and designation of any chaperone(s).</td>
   			<td>0 to many</td>
   			<td>O</td>
   			<td>Free text. Carried in the FHIR element.</td>
  		</tr>
		<tr>
		<td colspan="5"><b>* M=Mandatory R=Required O=Optional</b></td>
		</tr>
 	</tbody>
</table>


## Example Attendance details Section ##

```
<xml>
<!--Attendance details-->
	<section>
		<title value="Attendance details"/>
		<code>
			<coding>
				<system value="http://snomed.info/sct"/>
				<code value="1077881000000105"/>
				<display value="Attendance details"/>
			</coding>
		</code>
		<text>
		<status value="additional"/>
		<div xmlns="http://www.w3.org/1999/xhtml">
		<table width="100%">
		<tbody>
		<tr>
			<th>Date and time of contact</th>
			<td>9-May-2018 10:00</td>
		</tr>
		<tr>
			<th>Organisation name</th>
			<td>Name: Overtown Pharmacy</td>
		</tr>
		<tr>
			<th>Organisation address</th>
			<td>
				<p>Address:</p>
				<p>Address Line: 1, High Street, Overtown</p>
				<p>City: Leeds</p>
				<p>Post Code: LS1 9AM</p>
			</td>
		</tr>
		<tr>
			<th>Organisation contact details</th>
			<td>
				<p>Contact details: Tel. 01134875516 Email. overtonpharmacy118@mymail.com</p>
			</td>
		</tr>
		<tr>
			<th>Person accompanying patient</th>
			<td>Not Applicable</td>
		</tr>
	</tbody>
	</table>
	</div>
	</text>
	<!--Reference to Encounter resource as the source of information for this section-->
	<entry>
		<reference value="urn:uuid:1c1f74ac-b4a1-468b-b1e1-0df0e0692064"/>
	</entry>
	</section>
</xml>
```

## Coded Resources ##

This text section should be linked to the following FHIR Resources to provide the textual information in a coded format.

- The Digital Medicines specification does not currently support coded attendance details.







---
title: Contacts with professionals Section
keywords:  messaging, sections
tags: [fhir,messaging,section]
sidebar: foundations_sidebar
permalink: explore_contacts_professionals.html
summary: "Gives information about the Contacts with professionals section"
---

{% include warning.html content="The following implementations are now retired:<br/>
* new medicine service<br/>
* medication review<br/>
* appliance use review" %}

{% include custom/section.warnbanner.html %}

## Contacts with professionals Common Section Content ##
The Contacts with professionals section carries information about Contacts with professionals used. PRSB Elements should be formatted as subheadings in any HTML sent.

Contacts with professionals will be carried in the CodeableConcept of <b>Composition.section.code</b> FHIR element.

| ATTENDANCE   DETAILS                |                                                                                                                                                                                           |             |                                                                                                                                                                                               |                                  |                                                                                                                                                                                                         |
|-------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Data Item | Description | Cardinality | Values | Mandatory/required/     optional | FHIR Target|
| Date and time of contact            | Date   and time of the patient contact or attendance. | 1   ONLY    | The   date and time as recorded by the pharmacy system.   | Mandatory                        | Encounter.period.start. |
|Service    | The   service being provided.                                                                                                                                             | 0 TO 1      | Coded   entry                                                                                                                                                                                 | Required                         | Encounter.serviceProvider.Organization.Healthcareservice                                                                                                                                                 |
| Organisation name                   | The   name, including the identifier, of the organisation providing the   service. *(MIRC items __FollowupProviderName__ and __FollowupProviderODSCode__ can be used here)*| 1 ONLY      | This   would be generated from the ODS code and associated text.In the future the   global location number (GLN) may be used - GS1 standard.                                                  | Mandatory                        | Encounter.serviceProvider with   a link to CareConnect-Organization-1 (identifier and name).                                                                                                            |
| Organisation address                | The   address of the organisation providing the service. *(MIRC item __FollowupProviderAddress__ can be used here)* | 0 TO 1      | ODS   standard but may be generated from the Directory of Services (DOS).| Required | Encounter.serviceProvider with   a link to CareConnect-Organization-1(address).                                                                                                                          |
| Organisation contact details        | The   contact details of the organisation providing the service. For example a   phone number, NHSmail address etc. Contact details are used to resolve   queries about the record entry. | 0 TO MANY   | ODS   standard but may be generated from the Directory of Services (DOS).                                                                                                                     | Required                         | Encounter.serviceProvider with   a link to CareConnect-Organization-1(telecom).                                                                                                                          |
| Reason for non-provision of service | The   reason why the patient was not provided with the service e.g. declined, did   not attend etc.                                                                                       | 0   TO 1    | Free   text e.g. did not attend, declined by patient or clinician etc. Maybe coded   text in the future if a reference set is created.                                                        | <font color="red">Optional</font>  | Composition.section.text|
| Clinician name| The   name of the person providing the service, preferably in a structured format. *(MIRC item __EnrolledPractitioner__ __[Anonymised]__ can be used here)*| 1 ONLY      | The   person name as held on the source system. Where possible this should be   broken down into its constituent parts (prefix, given name, family name,   suffix).                           | Mandatory                        | Encounter.participant                                                                                                                                                                                   |
| Role                                | The   role of the person providing the service.                                                                                                                                           | 0   TO 1    | The   role may be held on the source system, be from an authoritative source such   as SDS, or use an existing vocabulary such as the job role title (from the   national workforce dataset). | Required                         | Encounter.participant.individual.     Reference.Practitioner.identifier     Encounter.participant.individual.     Reference.Practitioner.name     PractitionerRole.code     PractitionerRole.identifier |
| Professional identifier             | Professional   identifier of the person providing the service. *(MIRC item __EnrolledPractitionerRegistration__ can be used here)*| 0   TO 1    | The   regulatory body and the identifier itself of the person held on the source   system. e.g. GPhC number of the pharmacist.| Required   | Encounter.participant.individual|
| Person accompanying patient         | Identify,   where clinically relevant, others accompanying the patient, eg parent,   relative, friend. Includes: Name, Relationship, role (e.g. informal carer). *(MIRC item __PatientAccompanied__ and __Relationship__ can be used here)* | 0   TO MANY | Free   text| <font color="red">Optional</font>   | Composition.section.text  |

## The sections below are Message specific ##

## Person collecting the medicine ##
>> **When implementing:**
* Emergency Supply
* Minor Illness Referral Consultation

Include element(s):

| Data   Item                    | Description                                                                                     | Cardinality | Values      | Mandatory/required/     optional | FHIR Target              |
|--------------------------------|-------------------------------------------------------------------------------------------------|-------------|-------------|----------------------------------|--------------------------|
| Person collecting the medicine | The   person collecting the emergency supply of medicine (if someone other than the   patient). | 0   TO 1    | Free   text | Required                         | Composition.section.text |


> **Chaperone**
>> **When implementing:**
* Appliance Use Review
* Vaccinations

Include element(s):

| Data   Item | Description                                      | Cardinality | Values       | Mandatory/required/     optional | FHIR Target              |
|-------------|--------------------------------------------------|-------------|--------------|----------------------------------|--------------------------|
| Chaperone   | The   name and designation of any chaperone(s).  | 0   TO MANY | Free   text. | Optional                         | Composition.section.text |


> **Contact type**
>> **When implementing:**
* New Medicine Service

Include element(s):

| Data Item      | Description                                                                                           | Cardinality | Values                              | Mandatory/required/     optional | FHIR Target                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|----------------|-------------------------------------------------------------------------------------------------------|-------------|-------------------------------------|----------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Contact   type | A   record of whether the current attendance is an initial appointment or a   follow up appointment.  | 0   TO 1    | First   contact, follow-up contact. | Required                         | Text.   Contact type may come from those recorded on the local PAS. NHS Data   dictionary First attendance.     1  	First attendance face to   face     2  	Follow-up attendance face to   face     3  	First telephone or telemedicine   consultation     4  	Follow-up telephone or   telemedicine consultation     This should also be carried in the FHIR element Encounter.type and as this   is an example ValueSet the Encounter.type.Coding.system should contain the   value "https://www.datadictionary.nhs.uk". |


> **Location of event**
>> **When implementing:**
* New Medicine Service
* Medication Review
* Appliance Use Review
* Vaccinations
* Minor Illness Referral Consultation

Include element(s):

| Data Item             | Description                                                                                                                                                                     | Cardinality | Values                                                                                                                                                                                                       | Mandatory/required/     optional | FHIR Target              |
|-----------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------|--------------------------|
| Location of event | The   location where the event took place (if different from the organisation address). | 0   TO 1    | Freetext. e.g. Care Home, Patient's Home, Community Pharmacy etc. | Required                         | Composition.section.text<br/><br/> PRSB standard states this element is optional, and is required if different from the organisation address. <br/><br/> Some supplier implementations always populate location. They are using 'Community Pharmacy' to indicate the location matches the organisation address. |



> **Consultation method**
>> **When Implementing:**
* Emergancy Supply
* New Medicine Service
* Medication Review
* Appliance Use Review

Include element(s):

| Data Item             | Description                                                                                                                                                                     | Cardinality | Values                                                                                                                                                                                                       | Mandatory/required/     optional | FHIR Target              |
|-----------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------|--------------------------|
| Consultation   method | Consultation   method identifies the communication mechanism used to relay information   between the care professional and the person who is the subject of the   consultation. | 0   TO 1    | Consultation   method may come from those recorded on the local PAS. NHS Data   Dictionary.     -Face-to-face,      -telephone,      -tele medicine web camera,      -talk type for a person unable to speak | Required                         | Composition.section.text |


> **Reason for service**
>> **When Implementing:**
* New Medicine Service
* Medication Review
* Appliance Use Review
* Emergency Supply

Include element(s):

| Data Item          | Description                                                  | Cardinality | Values      | Mandatory/required/     optional | FHIR Target              |
|--------------------|--------------------------------------------------------------|-------------|-------------|----------------------------------|--------------------------|
| Reason for service | The   reason why the patient has been offered the service.   | 0   TO 1    | Free   text | Required                         | Composition.section.text |


> **Consultation type**
>> **When implementing:**
* Minor Illness Referral Consultation

Include element(s):

| Data Item      | Description  | Cardinality | Values                              | Mandatory/required/     optional | FHIR Target|
|----------------|-------------------------------------------------------------------------------------------------------|-------------|-------------------------------------|----------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Consultation   type | Describes The Type Of Consultation Conducted  |    | Free Text |Mandatory| Composition.section.text  |


> **Legal information for 3rd party**
>> **When implementing:**
* Minor Illness Referral Consultation 

Include element(s):

| Data Item      | Description  | Cardinality | Values                              | Mandatory/required/     optional | FHIR Target|
|----------------|-------------------------------------------------------------------------------------------------------|-------------|-------------------------------------|----------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Legal information for 3rd party| Confirmation of consent from the patient that the third party can act on their behalf  |    | Free Text |Mandatory| Composition.section.text  |



## Example Contacts with professionals Section ##

{% include note.html content="These examples have not been clinically assured against Digital Medicines use cases.<br/>Examples are illustrative only." %}

```
<!--<xml>-->
<!--Contacts with professionals-->
	<section>
		<title value="Contacts with professionals"/>
		<code>
			<coding>
				<system value="https://fhir.nhs.uk/CodeSystem/SectionCode"/>
				<code value="contacts-with-professionals"/>
				<display value="Contacts with professionals"/>
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
				<!--For Vaccinations Service would be-->
  				<tr>
   					<th>Service</th>
   					<td>The service under which the vaccination was administered.</td>
   				</tr>
				<!--For Emergency Supply Service would be-->
  				<tr>
   					<th>Service</th>
   					<td>Urgent supply of prescription items by community pharmacy</td>
   				</tr>				
				<tr>
   					<th>Organisation name</th>
   					<td>Overtown Pharmacy</td>
  				</tr>
				<tr>
   					<th>Organisation address</th>			
					<td>1, High Street, Overtown<br/>Leeds<br/>LS1 9AM</td>
  				</tr>
				<tr>
   					<th>Organisation contact details</th>
   					<td>Tel: 01134875516<br/>Email: overtonpharmacy118@mymail.com</td>
  				</tr>
				<tr>
   					<th>Location of event</th>
   					<td>Community Pharmacy</td>
   				</tr>
				<tr>
   					<th>Consultation method</th>
   					<td>Face to face</td>
   				</tr>				
				<tr>
   					<th>Reason for non-provision of service</th>
   					<td>did not attend</td>
   				</tr>
				<tr>
   					<th>Clinician name</th>
   					<td>Dr, John, Castle</td>
   				</tr>
				<tr>
   					<th>Role</th>
   					<td>Community pharmacist</td>
  				</tr>
				<tr>
   					<th>Professional identifier</th>
   					<td>General Pharmaceutical Council registration number: 7654321</td></tr>
				<tr>
   					<th>Person accompanying patient</th>
   					<td>parent</td>
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
<!--</xml>-->
```

## Coded Resources ##

This text section should be linked to the following FHIR Resources to provide the textual information in a coded format.

- The Digital Medicines specification does not currently support coded Contacts with professionals.







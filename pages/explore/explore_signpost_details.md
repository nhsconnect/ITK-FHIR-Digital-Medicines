---
title: Signpost Details
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_signpost_details.html
summary: "Gives information about patient signposting during consultation"
---

{% include custom/section.warnbanner.html %}

## Signposting Section Content ##
The signpost details section carries information about the signposting that a patient recieves during a consultation. PRSB Elements should be formatted as subheadings in any HTML sent.<br/><br/>There may be 0 TO MANY record entries under a section. Each record entry is made up of a number of the elements or data items below.<br/><br/>In order to distinguish a signposting using a ReferralRequest,<br/>
* ReferralRequest.status should be set to "draft"
* ReferralRequest.intent set to "proposal"


| SIGNPOST DETAILS  |                                                                                                                                                                                                                                                                                                                    |             |                                                                    |                                  |                          |
|-----------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------|--------------------------------------------------------------------|----------------------------------|--------------------------|
| Data Item        | Description   | Cardinality | Values       | Mandatory/required/     optional | FHIR Target              |
| Date             |Date of signpost. | 0 TO 1 | DateTime | Required| ReferralRequest.authoredOn
| Signpost To     | Details of where the signpost is to.<br/>If not an individual, this could be a service.   | 0 TO 1   | Either a HealthcareService, or Practitioner | Required     | ReferralRequest.recipient |
| [Signpost To] Individual | Include:<br/>* Name of person signposted to<br/> * Role of person signposted to <br/> * The grade of the person signposted to <br/> * The team or department signposted to (individual) <br/> * The specialty signposted to e.g. physiotherapy, oncology, mental health etc| 0 TO 1 |Individual details captured by the system | Required | ReferralRequest.recipient -> Practitioner/PractitionerRole/HealthcareService/CareTeam |
| [Signpost To] Service  | Details of where the signpost is to (service)<br/> * Service (either coded or free text) | 0 TO 1   | ReferralRequest.recipient->HealthcareService | Required     | ReferralRequest.recipient->HealthcareService |
| Contact details  | The contact details of where the person has been signposted to.   | 0 TO 1   | free text | Required     | PractitionerRole.telecom (for individual)<br/>HealthcareService.telecom (for service) |
| Reason for Signpost  | The reason for signposting.   | 0 TO 1   | free text or coded | Required     | ReferralRequest.reasonCode |
| Urgency for Signpost  | The details of the clinical urgency of signpost.   | 0 TO 1   | free text or coded | Required     | * ReferralRequest.priority (for coded)<br/> * ReferralRequest.note (for text) |


## Example Section ##

{% include note.html content="These examples have not been clinically assured against Digital Medicines use cases.<br/>Examples are illustrative only." %}

```
<!--<xml>-->
<!--Signpost details-->
	<section>
		<title value="Signpost details"/>
		<code>
			<coding>
				<system value="http://snomed.info/sct"/>
				<code value="975131000000104"/>
				<display value="Signposting"/>
			</coding>
		</code>
		<text>
			<status value="additional"/>
			<div xmlns="http://www.w3.org/1999/xhtml">
			<table width="100%">
				<tbody>
				<tr>
					<th>Date</th>
					<td>2021-09-04T12:34</td>
				</tr>
				<tr>
					<th>Signpost To</th>
					<td></td>
				</tr>
								<tr>
					<td>Name</td>
					<td>BROWN, John</td>
				</tr>
				<tr>
					<td>Role</td>
					<td>Senior Social Worker (Mental Health)</td>
				</tr>
								<tr>
					<td>Grade</td>
					<td>Consultant</td>
				</tr>
				<tr>
					<td>Team</td>
					<td>Cambridge Mental Health Team</td>
				</tr>	
				<tr>
					<td>Specialty</td>
					<td>Mental Health</td>
				</tr>	
				<tr>
					<th>Contact details</th>
					<td>cmh@nhs.net</td>
				</tr>	
				<tr>
					<th>Reason for Signpost</th>
					<td>Signs of depressions noted during consultation</td>
				</tr>	
				<tr>
					<th>Urgency for Signpost</th>
					<td>Routine</td>
				</tr>					
				</tbody>
			</table>
			</div>
		</text>
		<!-- if coded data included, this links to the coded ReferralRequest -->
		<entry>
			<reference value="urn:uuid:a0dc6fe6-e7a9-4cfd-90d2-ab587007f20f"/>
		</entry>
	</section>
<!--</xml>-->
```

## Example Coding ##
```
<!--<xml>-->
<!-- the ReferralRequest -->
	<entry>
		<fullUrl value="urn:uuid:a0dc6fe6-e7a9-4cfd-90d2-ab587007f20f"/>
		<resource>
			<ReferralRequest>
				<id value="a0dc6fe6-e7a9-4cfd-90d2-ab587007f20f"/>
				<meta>
					<profile value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-ReferralRequest-1"/>
				</meta>
				<status value="draft"/>
				<intent value="proposal"/>				
				<authoredOn value="2021-09-04T12:34:00+00:00"/>
				<recipient>
					<!-- link to the practitioner (individual) -->
						<reference value="urn:uuid:48d54dd7-28ef-455c-a5e1-375fab1db59e"/>
						<display value="BROWN John"/>
				</recipient>
				<!-- reason for signpost -->
				<reasonCode>
					<coding>
						<code value="394924000"/>
						<system value="http://snomed.info/sct"/>
						<display value="Symptoms of depression"/>
					</coding>
				</reasonCode>
				<!-- for free text reason use reasonCode.text
				<reasonCode>
					<text value="Observed symptoms of depression"/>
				</reasonCode> -->
				<!-- urgency for signpost -->
				<priority value="routine"/>
				<subject>
					<reference value="urn:uuid:9af701f7-5eb2-4402-bb3c-8ef8c8190082"/>
				</subject>
				<!-- for free text urgency use ReferralRequest.note
				<note>
						<text value="non urgent referral"/>
				</note>  -->
			</ReferralRequest>
		</resource>
	</entry>

	<entry>
		<fullUrl value="urn:uuid:48d54dd7-28ef-455c-a5e1-375fab1db59e"/>
		<resource>
			<Practitioner>
				<id value="48d54dd7-28ef-455c-a5e1-375fab1db59e"/>
				<meta>
					<profile value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1"/>
				</meta>
				<!-- Practitioner's name -->
				<name>
					<family value="BROWN"/>
					<given value="John"/>
				</name>
			</Practitioner>
		</resource>
	</entry>

	<entry>
		<fullUrl value="urn:uuid:71ed95ba-4bbc-4080-a8d2-56dd0f5ca036"/>
		<resource>
			<PractitionerRole>
				<id value="71ed95ba-4bbc-4080-a8d2-56dd0f5ca036"/>
				<meta>
					<profile value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-PractitionerRole-1"/>
				</meta>
				<!-- link to the practitioner -->
				<practitioner>
					<reference value="urn:uuid:48d54dd7-28ef-455c-a5e1-375fab1db59e"/>
				</practitioner>
				<!-- role or Practitioner -->
				<code>
					<coding>
						<code value="R9590"/>
						<system value="https://fhir.hl7.org.uk/STU3/ValueSet/CareConnect-SDSJobRoleName-1"/>
						<display value="Senior Social Worker (Mental Health)"/>
					</coding>
				</code>
				<!-- specialty -->
				<specialty>
					<coding>
						<code value="708168004"/>
						<system value="http://snomed.info/sct"/>
						<display value="Mental health service"/>
					</coding>
				</specialty>
				<telecom>
						<system value="email"/>
						<value value="cmh@nhs.net"/>
				</telecom>				
			</PractitionerRole>
		</resource>
	</entry>

	<entry>
		<fullUrl value="urn:uuid:1d2c557c-97f0-4e05-9d30-b25a4d4b6c9e"/>
		<resource>
			<CareTeam>
				<id value="1d2c557c-97f0-4e05-9d30-b25a4d4b6c9e"/>
				<meta>
					<profile value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-CareTeam-1"/>
				</meta>
				<!-- name of care team -->
				<name value="Cambridge Mental Health Team"/>
				<!-- link to the Practitioner -->
				<participant>
					<member>
						<reference value="urn:uuid:48d54dd7-28ef-455c-a5e1-375fab1db59e"/>
					</member>
				</participant>
			</CareTeam>
		</resource>
	</entry>	

<!--</xml>-->
```

## Example Coding for a Service ##
```
<!--<xml>-->

	<entry>
		<fullUrl value="urn:uuid:75802b19-7a33-416e-89a8-2fbabfa75726"/>
		<resource>
			<HealthcareService>
				<id value="75802b19-7a33-416e-89a8-2fbabfa75726"/>
				<meta>
					<profile value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-HealthcareService-1"/>
				</meta>
				<!-- type of healthcare service -->
				<type>
					<coding>
						<code value="708168004"/>
						<system value="http://snomed.info/sct"/>
						<display value="Mental health service"/>
					</coding>
				</type>
				<!-- contact details -->
				<telecom>
						<system value="email"/>
						<value value="cmh@nhs.net"/>
				</telecom>
			</HealthcareService>
		</resource>
	</entry>

<!--</xml>-->
```
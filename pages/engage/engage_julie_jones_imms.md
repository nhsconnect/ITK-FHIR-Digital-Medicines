---
title: Julie Jones Pharmacy Flu Vaccination Scenario
keywords: workflow
tags: [development,fhir,profiles]
sidebar: overview_sidebar
permalink: engage_julie_jones_imms.html
summary: "Example scenario - Julie Jones Pharmacy Flu Vaccination"
---

## Background ##

Mrs Jones is a 59 year old lady who has Chronic Obstructive Pulmonary Disease (COPD). She attends her GP practice to see the nurse practitioner for her 6 month review.
- As part of the review is advised that she has the flu vaccination as she is at greater risk from flu and its complications.
- Mrs Jones agrees to make an appointment for the vaccination at reception on her way out.
- Since reception is busy she decides she will call later on.

Mrs Jones attends her local pharmacy later that day to collect her regular medicines. She notices that her local pharmacy offers the flu vaccination.
- She asks the pharmacist if she is able to have her vaccination in the pharmacy.
- The pharmacist informs her she is eligible for the flu vaccination free of charge and that she can have it now while she is waiting for her medicines.

Mrs Jones agrees to have the vaccination at the pharmacy.
During the consultation, Mrs Jones is asked by the pharmacist if she is happy for this information to be shared with her GP. Mrs Jones agrees.
The pharmacist completes the vaccination and sends the relevant information captured from Mrs Jones to her GP.

## The Pharmacy Encounter ##

The Pharmacy Encounter is documented in the [Encounter Resource](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Encounter-1)

## Named Participants ##

- Patient - **Julie Jones** - [Patient Resource](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1)
- Pharmacist (Document Author) - **Mr Eric Smith** - [Practitioner Resource](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1)
- Patient's GP (Document Recipient) - **Dr Paul Rastall** - [Practitioner Resource](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1)

## Named Organisations ##

- Pharmacy - **Overtown Pharmacy** - [Organization Resource](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- Patient's GP Practice - **MGP Medical Centre** - [Organization Resource](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)

## Example Instance of Scenario ##

{% include note.html content="These examples have not been clinically assured against Digital Medicines use cases.<br/>Examples are illustrative only." %}

```
<!--<xml>-->
<!--This xml example is for illustrative purposes only and has not been clinically verified.-->
<Bundle xmlns="http://hl7.org/fhir">
	<id value="40e225a0-8f48-11e8-b568-0800200c9a66"/>
	<meta>
		<lastUpdated value="2018-05-09T10:00:00+00:00"/>
		<profile value="https://fhir.nhs.uk/STU3/StructureDefinition/ITK-Document-Bundle-1"/>
	</meta>
	<identifier>
		<system value="https://tools.ietf.org/html/rfc4122"/>
		<value value="739aeb30-8f48-11e8-b568-0800200c9a66"/>
	</identifier>
	<type value="document"/>
	<!--Pharmacy Vaccinations Notification Document-->
	<entry>
		<fullUrl value="urn:uuid:979a4ef0-8b5a-11e8-b568-0800200c9a66"/>
		<resource>
			<!-- A Resource carrying a set of healthcare-related information about the patient-->
			<Composition xmlns="http://hl7.org/fhir">
				<id value="979a4ef0-8b5a-11e8-b568-0800200c9a66"/>
				<meta>
					<profile value="https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-DM-Immunization-Composition-1"/>
				</meta>
				<!-- Extension to carry details of the Correspondence Care Setting Type. -->
				<extension url="https://fhir.nhs.uk/STU3/StructureDefinition/Extension-CareSettingType-1">
					<valueCodeableConcept>
						<coding>
							<system value="http://snomed.info/sct"/>
							<code value="310080006"/>
							<display value="Pharmacy service"/>
						</coding>
					</valueCodeableConcept>
				</extension>
				<identifier>
					<system value="https://tools.ietf.org/html/rfc4122"/>
					<value value="86943780-8b5d-11e8-b568-0800200c9a66"/>
				</identifier>
				<!--The workflow/clinical status of this composition. The status is a marker for the clinical standing of the document.-->
				<status value="final"/>
				<type>
					<!--Digital Medicines document type-->
					<coding>
						<system value="http://snomed.info/sct"/>
						<code value="41000179103"/>
						<display value="Immunisation record"/>
					</coding>
				</type>
				<!--Reference to the patient subject of the Composition-->
				<subject>
					<reference value="urn:uuid:9589fb37-87a2-48d8-968f-b371429209e3"/>
				</subject>
				<!--Reference to the clinical encounter or type of care this documentation is associated with.-->
				<encounter>
					<reference value="urn:uuid:1c1f74ac-b4a1-468b-b1e1-0df0e0692064"/>
				</encounter>
				<!--The composition editing time, when the composition was last logically changed by the author.-->
				<date value="2018-05-09T10:00:00+00:00"/>
				<!--Identifies who is responsible for the information in the composition, 
not necessarily who typed it in-->
				<author>
					<reference value="urn:uuid:666f8ce8-3f3b-43ac-9f8d-5bb020539d74"/>
				</author>
				<title value="Overtown Pharmacy 118 Immunization Record"/>
				<!--Identifies the organization responsible for ongoing maintenance of and access 
to the composition/document information.-->
				<custodian>
					<reference value="urn:uuid:94ca030c-03aa-4dae-8270-c2de2b7907ef"/>
				</custodian>
				<!--Allergies and adverse reactions-->
				<section>
					<title value="Allergies and adverse reactions"/>
					<code>
						<coding>
							<system value="http://snomed.info/sct"/>
							<code value="886921000000105"/>
							<display value="Allergies and adverse reactions"/>
						</coding>
					</code>
					<text>
						<status value="additional"/>
						<div xmlns="http://www.w3.org/1999/xhtml">
							<table width="100%">
								<tbody>
									<tr>
										<th>Causative agent</th>
										<td>NHS dm+d TF</td>
									</tr>
									<tr>
										<th>Description of reaction</th>
										<td>Signs of a skin rash</td>
									</tr>
									<tr>
										<th>Type of reaction</th>
										<td>allergy</td>
									</tr>
									<tr>
										<th>Severity</th>
										<td>mild</td>
									</tr>
									<tr>
										<th>Certainty</th>
										<td>unconfirmed</td>
									</tr>
									<tr>
										<th>Probability of recurrence</th>
										<td>Until the cause of the allergy is determined the chances of it coming back are high.</td>
									</tr>
									<tr>
										<th>Date first experienced</th>
										<td>9-May-2018 10:00</td>
									</tr>
									<tr>
										<th>Comment</th>
										<td>Suggest refer to a dermatologist</td>
									</tr>
									<tr>
										<th>Date recorded</th>
										<td>10-May-2018 10:00</td>
									</tr>
								</tbody>
							</table>
						</div>
					</text>
					<!--Reference to Allergies List as the source of information for this section-->
					<entry>
						<reference value="urn:uuid:66204550-8e57-11e8-b568-0800200c9a66"/>
					</entry>
				</section>
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
										<th>Location of event</th>
										<td>Community Pharmacy</td>
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
				<!--Legal information-->
				<section>
					<title value="Legal information"/>
					<code>
						<coding>
							<system value="http://snomed.info/sct"/>
							<code value="886961000000102"/>
							<display value="Legal information"/>
						</coding>
					</code>
					<text>
						<status value="additional"/>
						<div xmlns="http://www.w3.org/1999/xhtml">
							<table width="100%">
								<tbody>
									<tr>
										<th>Consent for treatment record</th>
										<td>Patient's consent for treatment has been attained.</td>
									</tr>
									<tr>
										<th>Consent for information sharing</th>
										<td>Patient is happy for the immunization details to be shares with their Registered GP.</td>
									</tr>
									<tr>
										<th>Consent relating to child</th>
										<td>Not Applicable</td>
									</tr>
								</tbody>
							</table>
						</div>
					</text>
				</section>
				<!--Eligibility Criteria-->
				<section>
					<title value="Eligibility Criteria"/>
					<code>
						<coding>
							<system value="http://snomed.info/sct"/>
							<code value="61871000000107"/>
							<display value="Eligibility for treatment"/>
						</coding>
					</code>
					<text>
						<status value="additional"/>
						<div xmlns="http://www.w3.org/1999/xhtml">
							<table width="100%">
								<tbody>
									<tr>
										<th>Eligibility criteria</th>
									</tr>
									<tr>
										<td>
											<p>Patient has Chronic Obstructive Pulmonary Disease (COPD).</p>
										</td>
									</tr>
								</tbody>
							</table>
						</div>
					</text>
				</section>
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
										<th>GP name</th>
										<td>
											<p>Prefix: Dr</p>
											<p>Given Name: Paul</p>
											<p>Family Name: Rastall</p>
										</td>
									</tr>
									<tr>
										<th>GP practice identifier</th>
										<td>
											<p>ODS Organization Code:GP123456</p>
										</td>
									</tr>
									<tr>
										<th>GP practice details</th>
										<td>
											<p>Name: MGP Medical Centre</p>
											<p>Address:</p>
											<p>Address Line: 1 MGP House, Overtown</p>
											<p>City: Leeds</p>
											<p>Post Code: LS21 7PA</p>
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
				<!--History-->
				<section>
					<title value="History"/>
					<code>
						<coding>
							<system value="http://snomed.info/sct"/>
							<code value="717121000000105"/>
							<display value="History"/>
						</coding>
					</code>
					<text>
						<status value="additional"/>
						<div xmlns="http://www.w3.org/1999/xhtml">
							<table width="100%">
								<tbody>
									<tr>
										<th>Relevant past medical, surgical and mental health history</th>
										<td>
											<p>Patient has Chronic Obstructive Pulmonary Disease (COPD). She was advised to have the flu vaccination as she is at greater risk from flu and its complications when she last attended her GP Practice.</p>
											<p>Patient requested the vaccination.</p>
											<p>No history of vaccination recorded at Pharmacy.</p>
										</td>
									</tr>
								</tbody>
							</table>
						</div>
					</text>
				</section>
				<!--Vaccinations-->
				<section>
					<title value="Vaccinations"/>
					<code>
						<coding>
							<system value="http://snomed.info/sct"/>
							<code value="1102181000000102"/>
							<display value="Immunisations"/>
						</coding>
					</code>
					<text>
						<status value="additional"/>
						<div xmlns="http://www.w3.org/1999/xhtml">
							<table width="100%">
								<tbody>
									<tr>
										<td>Vaccine product: Influvac sub-unit Tetra vaccine suspension for injection 0.5ml pre-filled syringes (Mylan)</td>
										<td>Vaccine procedure: Seasonal influenza vaccination given by pharmacist.</td>
										<td>Site: Upper right arm</td>
										<td>Route: Subcutaneous route</td>
										<td>Indication: Patient requested procedure.</td>
									</tr>
									<tr>
										<td>Administered by: Mr Eric Smith</td>
										<td>GPhC identifier: 2145879</td>
										<td>Date Time: 9-May-2018 10:00</td>
									</tr>
								</tbody>
							</table>
						</div>
					</text>
					<entry>
						<reference value="urn:uuid:631ec8d3-6341-4c9e-b2a1-131af62718f2"/>
					</entry>
				</section>
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
				<!-- Patient demographics-->
				<section>
					<title value="Patient demographics"/>
					<code>
						<coding>
							<system value="http://snomed.info/sct"/>
							<code value="886731000000109"/>
							<display value="Patient demographics"/>
						</coding>
					</code>
					<text>
						<status value="additional"/>
						<div xmlns="http://www.w3.org/1999/xhtml">
							<table width="100%">
								<tbody>
									<tr>
										<th>Patient name</th>
										<td>
											<p>Prefix: Mrs</p>
											<p>Given Name: Julie</p>
											<p>Family Name: Jones</p>
										</td>
									</tr>
									<tr>
										<th>Date of birth</th>
										<td>4 May 1959</td>
									</tr>
									<tr>
										<th>Sex</th>
										<td>Female</td>
									</tr>
									<tr>
										<th>NHS number</th>
										<td>3478526985</td>
									</tr>
									<tr>
										<th>Patient address</th>
										<td>
											<p>Address Line: 22, Brightside Crescent, Overtown</p>
											<p>City: Leeds</p>
											<p>Post Code: LS10 4YU</p>
										</td>
									</tr>
									<tr>
										<th>Relevant contacts</th>
										<td>Name: Philip Jones <p>Relationship: Next of kin</p>
											<p>Contact details: Tel. 01138698975 Email. pjones@mymail.com</p>
										</td>
									</tr>
								</tbody>
							</table>
						</div>
					</text>
					<!--reference to further information carried in the patient resource-->
					<entry>
						<reference value="urn:uuid:9589fb37-87a2-48d8-968f-b371429209e3"/>
					</entry>
				</section>
				<!-- Referral details-->
				<section>
					<title value="Referral details"/>
					<code>
						<coding>
							<system value="http://snomed.info/sct"/>
							<code value="886721000000107"/>
							<display value="Referral details"/>
						</coding>
					</code>
					<text>
						<status value="generated"/>
						<div xmlns="http://www.w3.org/1999/xhtml">
							<table width="100%">
								<tbody>
									<tr>
										<th>Referral details</th>
										<td>
											<p>Self referral.</p>
										</td>
									</tr>
								</tbody>
							</table>
						</div>
					</text>
				</section>
			</Composition>
		</resource>
	</entry>
	<!--Pharmacy Encounter-->
	<entry>
		<fullUrl value="urn:uuid:1c1f74ac-b4a1-468b-b1e1-0df0e0692064"/>
		<resource>
			<!--Encounter resource providing context for the pharmacy visit-->
			<Encounter xmlns="http://hl7.org/fhir">
				<id value="1c1f74ac-b4a1-468b-b1e1-0df0e0692064"/>
				<meta>
					<profile value="https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Encounter-1"/>
				</meta>
				<status value="finished"/>
				<subject>
					<reference value="urn:uuid:9589fb37-87a2-48d8-968f-b371429209e3"/>
					<display value="JONES, Julie (Mrs)"/>
				</subject>
				<participant>
					<type>
						<coding>
							<system value="http://hl7.org/fhir/v3/ParticipationType"/>
							<code value="PPRF"/>
							<display value="primary performer"/>
						</coding>
					</type>
					<individual>
						<reference value="urn:uuid:666f8ce8-3f3b-43ac-9f8d-5bb020539d74"/>
						<display value="SMITH, Eric (Mr)"/>
					</individual>
				</participant>
				<period>
					<start value="2018-05-09T10:00:00+00:00"/>
				</period>
				<serviceProvider>
					<reference value="urn:uuid:09cf4c3d-2ba0-40dc-a633-27fca0151a91"/>
					<display value="Overtown Pharmacy"/>
				</serviceProvider>
			</Encounter>
		</resource>
	</entry>
	<!--Pharmacy associated with the encounter. -->
	<entry>
		<fullUrl value="urn:uuid:09cf4c3d-2ba0-40dc-a633-27fca0151a91"/>
		<resource>
			<Organization xmlns="http://hl7.org/fhir">
				<id value="09cf4c3d-2ba0-40dc-a633-27fca0151a91"/>
				<meta>
					<profile value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1"/>
				</meta>
				<identifier>
					<system value="https://fhir.nhs.uk/Id/ods-organization-code"/>
					<value value="FA000"/>
				</identifier>
				<name value="Overtown Pharmacy"/>
				<telecom>
					<system value="phone"/>
					<value value="01134875516"/>
				</telecom>
				<telecom>
					<system value="email"/>
					<value value="overtonpharmacy118@mymail.com"/>
				</telecom>
				<address>
					<line value="1 High Street, Overtown"/>
					<city value="Leeds"/>
					<postalCode value="LS1 9AM"/>
				</address>
			</Organization>
		</resource>
	</entry>
	<!--Patient's registered GP Practice.-->
	<entry>
		<fullUrl value="urn:uuid:94ca030c-03aa-4dae-8270-c2de2b7907ef"/>
		<resource>
			<Organization xmlns="http://hl7.org/fhir">
				<id value="94ca030c-03aa-4dae-8270-c2de2b7907ef"/>
				<meta>
					<profile value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1"/>
				</meta>
				<identifier>
					<system value="https://fhir.nhs.uk/Id/ods-organization-code"/>
					<value value="GP123456"/>
				</identifier>
				<name value="MGP Medical Centre"/>
				<address>
					<line value="1 MGP House, Overtown"/>
					<city value="Leeds"/>
					<postalCode value="LS21 7PA"/>
				</address>
			</Organization>
		</resource>
	</entry>
	<!--Patient associated with the encounter.-->
	<entry>
		<fullUrl value="urn:uuid:9589fb37-87a2-48d8-968f-b371429209e3"/>
		<resource>
			<Patient xmlns="http://hl7.org/fhir">
				<id value="9589fb37-87a2-48d8-968f-b371429209e3"/>
				<meta>
					<profile value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1"/>
				</meta>
				<identifier>
					<extension url="https://fhir.hl7.org.uk/STU3/StructureDefinition/Extension-CareConnect-NHSNumberVerificationStatus-1">
						<valueCodeableConcept>
							<coding>
								<system value="https://fhir.hl7.org.uk/STU3/CodeSystem/CareConnect-NHSNumberVerificationStatus-1"/>
								<code value="01"/>
								<display value="Number present and verified"/>
							</coding>
						</valueCodeableConcept>
					</extension>
					<system value="https://fhir.nhs.uk/Id/nhs-number"/>
					<value value="3478526985"/>
				</identifier>
				<name>
					<use value="official"/>
					<text value="Mrs Julie Jones"/>
					<family value="Jones"/>
					<given value="Julie"/>
					<prefix value="Mrs"/>
				</name>
				<telecom>
					<system value="phone"/>
					<value value="01138698975"/>
					<use value="home"/>
				</telecom>
				<gender value="female"/>
				<birthDate value="1959-05-04"/>
				<address>
					<use value="home"/>
					<type value="both"/>
					<text value="22 Brightside Crescent, Overtown, West Yorkshire, LS10 4YU"/>
					<line value="22 Brightside Crescent"/>
					<city value="Overtown"/>
					<district value="West Yorkshire"/>
					<postalCode value="LS10 4YU"/>
				</address>
				<maritalStatus>
					<coding>
						<system value="http://hl7.org/fhir/v3/MaritalStatus"/>
						<code value="M"/>
						<display value="Married"/>
					</coding>
				</maritalStatus>
				<contact>
					<relationship>
						<coding>
							<system value="http://hl7.org/fhir/v2/0131"/>
							<code value="N"/>
							<display value="Next-of-Kin"/>
						</coding>
					</relationship>
					<name>
						<use value="official"/>
						<family value="Jones"/>
						<given value="Philip"/>
					</name>
					<telecom>
						<system value="phone"/>
						<value value="01138698975"/>
					</telecom>
					<telecom>
						<system value="email"/>
						<value value="pjones@mymail.com"/>
					</telecom>
					<gender value="male"/>
				</contact>
				<generalPractitioner>
					<reference value="urn:uuid:4d8b5538-c495-459c-9187-6a050ebc06ea"/>
				</generalPractitioner>
				<managingOrganization>
					<reference value="urn:uuid:94ca030c-03aa-4dae-8270-c2de2b7907ef"/>
				</managingOrganization>
			</Patient>
		</resource>
	</entry>
	<!--Patient's registered GP.-->
	<entry>
		<fullUrl value="urn:uuid:4d8b5538-c495-459c-9187-6a050ebc06ea"/>
		<resource>
			<Practitioner xmlns="http://hl7.org/fhir">
				<id value="4d8b5538-c495-459c-9187-6a050ebc06ea"/>
				<meta>
					<profile value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1"/>
				</meta>
				<identifier>
					<system value="https://fhir.hl7.org.uk/Id/gmc-number"/>
					<value value="6122477"/>
				</identifier>
				<name>
					<family value="Rastall"/>
					<given value="Paul"/>
					<prefix value="Dr"/>
				</name>
				<telecom>
					<system value="phone"/>
					<value value="01136323200"/>
					<use value="work"/>
				</telecom>
				<gender value="male"/>
			</Practitioner>
		</resource>
	</entry>
	<!--Pharmacist associated with the encounter. -->
	<entry>
		<fullUrl value="urn:uuid:666f8ce8-3f3b-43ac-9f8d-5bb020539d74"/>
		<resource>
			<Practitioner xmlns="http://hl7.org/fhir">
				<id value="666f8ce8-3f3b-43ac-9f8d-5bb020539d74"/>
				<meta>
					<profile value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1"/>
				</meta>
				<identifier>
					<system value="https://fhir.hl7.org.uk/Id/gphc-number"/>
					<value value="2145879"/>
				</identifier>
				<name>
					<family value="Smith"/>
					<given value="Eric"/>
					<prefix value="Mr"/>
				</name>
				<telecom>
					<system value="phone"/>
					<value value="0113895123"/>
					<use value="work"/>
				</telecom>
				<gender value="male"/>
			</Practitioner>
		</resource>
	</entry>
	<!--Vaccinations administered during the encounter-->
	<entry>
		<fullUrl value="urn:uuid:631ec8d3-6341-4c9e-b2a1-131af62718f2"/>
		<resource>
			<Immunization xmlns="http://hl7.org/fhir">
				<id value="631ec8d3-6341-4c9e-b2a1-131af62718f2"/>
				<meta>
					<profile value="https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-DM-Immunization-1"/>
				</meta>
				<extension url="https://fhir.hl7.org.uk/STU3/StructureDefinition/Extension-CareConnect-VaccinationProcedure-1">
					<valueCodeableConcept>
						<coding>
							<system value="http://snomed.info/sct"/>
							<code value="955691000000108"/>
							<display value="Seasonal influenza vaccination given by pharmacist"/>
						</coding>
					</valueCodeableConcept>
				</extension>
				<status value="completed"/>
				<notGiven value="false"/>
				<vaccineCode>
					<coding>
						<system value="http://snomed.info/sct"/>
						<code value="35727111000001109"/>
						<display value="Influvac sub-unit Tetra vaccine suspension for injection 0.5ml pre-filled syringes (Mylan)"/>
					</coding>
				</vaccineCode>
				<patient>
					<reference value="urn:uuid:9589fb37-87a2-48d8-968f-b371429209e3"/>
					<display value="JONES, Julie (Mrs)"/>
				</patient>
				<encounter>
					<reference value="urn:uuid:1c1f74ac-b4a1-468b-b1e1-0df0e0692064"/>
				</encounter>
				<date value="2018-05-09"/>
				<primarySource value="true"/>
				<site>
					<coding>
						<system value="http://snomed.info/sct"/>
						<code value="368209003"/>
						<display value="Right upper arm"/>
					</coding>
				</site>
				<route>
					<coding>
						<system value="http://snomed.info/sct"/>
						<code value="34206005"/>
						<display value="Subcutaneous route"/>
					</coding>
				</route>
				<practitioner>
					<role>
						<coding>
							<system value="http://hl7.org/fhir/v2/0443"/>
							<code value="AP"/>
							<display value="Administering Provider"/>
						</coding>
					</role>
					<actor>
						<reference value="urn:uuid:666f8ce8-3f3b-43ac-9f8d-5bb020539d74"/>
						<display value="SMITH, Eric (Mr)"/>
					</actor>
				</practitioner>
				<explanation>
					<reason>
						<coding>
							<system value="http://snomed.info/sct"/>
							<code value="398192003"/>
							<display value="Co-morbid conditions"/>
						</coding>
					</reason>
				</explanation>
			</Immunization>
		</resource>
	</entry>
	<!--Allergies list-->
	<entry>
		<fullUrl value="urn:uuid:66204550-8e57-11e8-b568-0800200c9a66"/>
		<resource>
			<List xmlns="http://hl7.org/fhir">
				<id value="66204550-8e57-11e8-b568-0800200c9a66"/>
				<meta>
					<profile value="https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Allergy-List-1"/>
				</meta>
				<identifier>
					<system value="https://tools.ietf.org/html/rfc4122"/>
					<value value="66204550-8e57-11e8-b568-0800200c9a66"/>
				</identifier>
				<status value="current"/>
				<mode value="snapshot"/>
				<code>
					<coding>
						<system value="http://snomed.info/sct"/>
						<code value="886921000000105"/>
						<display value="Allergies and adverse reactions"/>
					</coding>
				</code>
				<subject>
					<reference value="urn:uuid:9589fb37-87a2-48d8-968f-b371429209e3"/>
					<display value="JONES, Julie (Mrs)"/>
				</subject>
				<encounter>
					<reference value="urn:uuid:1c1f74ac-b4a1-468b-b1e1-0df0e0692064"/>
				</encounter>
				<source>
					<reference value="urn:uuid:666f8ce8-3f3b-43ac-9f8d-5bb020539d74"/>
					<display value="SMITH, Eric (Mr)"/>
				</source>
				<entry>
					<item>
						<reference value="urn:uuid:11003483-70bf-4025-805f-a9defed13e9a"/>
					</item>
				</entry>
			</List>
		</resource>
	</entry>
	<!--Allergies documented during the encounter.-->
	<entry>
		<fullUrl value="urn:uuid:11003483-70bf-4025-805f-a9defed13e9a"/>
		<resource>
			<AllergyIntolerance xmlns="http://hl7.org/fhir">
				<id value="11003483-70bf-4025-805f-a9defed13e9a"/>
				<meta>
					<profile value="https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-AllergyIntolerance-1"/>
				</meta>
				<identifier>
					<system value="https://tools.ietf.org/html/rfc4122"/>
					<value value="11003483-70bf-4025-805f-a9defed13e9a"/>
				</identifier>
				<clinicalStatus value="active"/>
				<verificationStatus value="confirmed"/>
				<code>
					<coding>
						<system value="http://snomed.info/sct"/>
						<code value="716186003"/>
						<display value="No known allergy"/>
					</coding>
				</code>
				<patient>
					<reference value="urn:uuid:9589fb37-87a2-48d8-968f-b371429209e3"/>
					<display value="JONES, Julie (Mrs)"/>
				</patient>
				<assertedDate value="2018-05-09"/>
			</AllergyIntolerance>
		</resource>
	</entry>
</Bundle>
<!--</xml>-->
```

## Example Instance of Scenario - ITK Wrapper ##

{% include note.html content="These examples have not been clinically assured against Digital Medicines use cases.<br/>Examples are illustrative only." %}

```
<!--<xml>-->
<!--This xml example is for illustrative purposes only and has not been clinically verified.-->
<Bundle xmlns="http://hl7.org/fhir">
	<id value="e6492db3-3788-4519-bebd-2bdf7d7236d8"/>
	<meta>
		<profile value="https://fhir.nhs.uk/STU3/StructureDefinition/ITK-Message-Bundle-1"/>
	</meta>
	<identifier>
		<system value="https://tools.ietf.org/html/rfc4122"/>
		<value value="a3940bf5-b82e-4c4f-9477-9bbe6861d634"/>
	</identifier>
	<type value="message"/>
	<entry>
		<fullUrl value="urn:uuid:a4409d7c-b613-477c-b623-87e60406c2f0"/>
		<resource>
			<MessageHeader>
				<id value="a4409d7c-b613-477c-b623-87e60406c2f0"/>
				<meta>
					<profile value="https://fhir.nhs.uk/STU3/StructureDefinition/ITK-MessageHeader-2"/>
				</meta>
				<extension url="https://fhir.nhs.uk/STU3/StructureDefinition/Extension-ITK-MessageHandling-2">
					<!--The value of this handling specification is dependant on the response pattern.-->
					<extension url="BusAckRequested">
						<valueBoolean value="true"/>
					</extension>
					<extension url="InfAckRequested">
						<valueBoolean value="true"/>
					</extension>
					<extension url="RecipientType">
						<valueCoding>
							<system value="https://fhir.nhs.uk/STU3/CodeSystem/ITK-RecipientType-1"/>
							<code value="FA"/>
							<display value="For Action"/>
						</valueCoding>
					</extension>
					<extension url="MessageDefinition">
						<valueReference>
							<reference value="https://fhir.nhs.uk/STU3/MessageDefinition/ITK-DM-Immunization-MessageDefinition-1"/>
						</valueReference>
					</extension>
					<extension url="SenderReference">
						<valueString value="None"/>
					</extension>
					<extension url="LocalExtension">
						<valueString value="None"/>
					</extension>
				</extension>
				<event>
					<system value="https://fhir.nhs.uk/STU3/CodeSystem/ITK-MessageEvent-2"/>
					<code value="ITK009D"/>
					<display value="ITK Digital Medicine Immunization Document"/>
				</event>
				<receiver>
					<reference value="urn:uuid:c7d0d92f-4db9-4ab0-89c8-375afca971ad"/>
				</receiver>
				<sender>
					<reference value="urn:uuid:b86216fe-6a51-4687-af97-4b7d58154c39"/>
				</sender>
				<timestamp value="2017-01-23T10:10:16+00:00"/>
				<source>
					<endpoint value="NOROT003"/>
				</source>
				<focus>
					<reference value="urn:uuid:289f9d42-6f97-40d2-890a-d3d0af397ac7"/>
				</focus>
			</MessageHeader>
		</resource>
	</entry>
	<!--Practitioner-->
	<entry>
		<fullUrl value="urn:uuid:b86216fe-6a51-4687-af97-4b7d58154c39"/>
		<resource>
			<Practitioner>
				<id value="b86216fe-6a51-4687-af97-4b7d58154c39"/>
				<meta>
					<profile value="https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Header-Practitioner-1"/>
				</meta>
				<identifier>
					<system value="https://fhir.nhs.uk/Id/sds-user-id"/>
					<value value="033345750518"/>
				</identifier>
				<name>
					<family value="Rastall"/>
					<given value="Paul"/>
					<prefix value="Dr"/>
				</name>
			</Practitioner>
		</resource>
	</entry>
	<!--Organization-->
	<entry>
		<fullUrl value="urn:uuid:c7d0d92f-4db9-4ab0-89c8-375afca971ad"/>
		<resource>
			<Organization>
				<id value="c7d0d92f-4db9-4ab0-89c8-375afca971ad"/>
				<meta>
					<profile value="https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Header-Organization-1"/>
				</meta>
				<identifier>
					<system value="https://fhir.nhs.uk/Id/ods-organization-code"/>
					<value value="RY6"/>
				</identifier>
			</Organization>
		</resource>
	</entry>
	<entry>
		<fullUrl value="urn:uuid:289f9d42-6f97-40d2-890a-d3d0af397ac7"/>
		<resource>
			<!--This xml example is for illustrative purposes only and has not been clinically verified.-->
			<Bundle xmlns="http://hl7.org/fhir">
				<id value="40e225a0-8f48-11e8-b568-0800200c9a66"/>
				<meta>
					<lastUpdated value="2018-05-09T10:00:00+00:00"/>
					<profile value="https://fhir.nhs.uk/STU3/StructureDefinition/ITK-Document-Bundle-1"/>
				</meta>
				<identifier>
					<system value="https://tools.ietf.org/html/rfc4122"/>
					<value value="739aeb30-8f48-11e8-b568-0800200c9a66"/>
				</identifier>
				<type value="document"/>
				<!--Pharmacy Vaccinations Notification Document-->
				<entry>
					<fullUrl value="urn:uuid:979a4ef0-8b5a-11e8-b568-0800200c9a66"/>
					<resource>
						<!--A resource carrying a set of healthcare-related information about the patient-->
						<Composition xmlns="http://hl7.org/fhir">
							<id value="979a4ef0-8b5a-11e8-b568-0800200c9a66"/>
							<meta>
								<profile value="https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-DM-Immunization-Composition-1"/>
							</meta>
							<!-- Extension to carry details of the Correspondence Care Setting Type. -->
							<extension url="https://fhir.nhs.uk/STU3/StructureDefinition/Extension-CareSettingType-1">
								<valueCodeableConcept>
									<coding>
										<system value="http://snomed.info/sct"/>
										<code value="310080006"/>
										<display value="Pharmacy service"/>
									</coding>
								</valueCodeableConcept>
							</extension>
							<identifier>
								<system value="https://tools.ietf.org/html/rfc4122"/>
								<value value="86943780-8b5d-11e8-b568-0800200c9a66"/>
							</identifier>
							<!--The workflow/clinical status of this composition. The status is a marker for the clinical standing of the document.-->
							<status value="final"/>
							<type>
								<!--Digital Medicines document type-->
								<coding>
									<system value="http://snomed.info/sct"/>
									<code value="41000179103"/>
									<display value="Immunisation record"/>
								</coding>
							</type>
							<!--Reference to the patient subject of the Composition-->
							<subject>
								<reference value="urn:uuid:9589fb37-87a2-48d8-968f-b371429209e3"/>
							</subject>
							<!--Reference to the clinical encounter or type of care this documentation is associated with.-->
							<encounter>
								<reference value="urn:uuid:1c1f74ac-b4a1-468b-b1e1-0df0e0692064"/>
							</encounter>
							<!--The composition editing time, when the composition was last logically changed by the author.-->
							<date value="2018-05-09T10:00:00+00:00"/>
							<!--Identifies who is responsible for the information in the composition, 
not necessarily who typed it in-->
							<author>
								<reference value="urn:uuid:666f8ce8-3f3b-43ac-9f8d-5bb020539d74"/>
							</author>
							<title value="Overtown Pharmacy 118 Immunization Record"/>
							<!--Identifies the organization responsible for ongoing maintenance of and access 
to the composition/document information.-->
							<custodian>
								<reference value="urn:uuid:94ca030c-03aa-4dae-8270-c2de2b7907ef"/>
							</custodian>
							<!--Allergies and adverse reactions-->
							<section>
								<title value="Allergies and adverse reactions"/>
								<code>
									<coding>
										<system value="http://snomed.info/sct"/>
										<code value="886921000000105"/>
										<display value="Allergies and adverse reactions"/>
									</coding>
								</code>
								<text>
									<status value="additional"/>
									<div xmlns="http://www.w3.org/1999/xhtml">
										<table width="100%">
											<tbody>
												<tr>
													<th>Causative agent</th>
													<td>NHS dm+d TF</td>
												</tr>
												<tr>
													<th>Description of reaction</th>
													<td>Signs of a skin rash</td>
												</tr>
												<tr>
													<th>Type of reaction</th>
													<td>allergy</td>
												</tr>
												<tr>
													<th>Severity</th>
													<td>mild</td>
												</tr>
												<tr>
													<th>Certainty</th>
													<td>unconfirmed</td>
												</tr>
												<tr>
													<th>Probability of recurrence</th>
													<td>Until the cause of the allergy is determined the chances of it coming back are high.</td>
												</tr>
												<tr>
													<th>Date first experienced</th>
													<td>9-May-2018 10:00</td>
												</tr>
												<tr>
													<th>Comment</th>
													<td>Suggest refer to a dermatologist</td>
												</tr>
												<tr>
													<th>Date recorded</th>
													<td>10-May-2018 10:00</td>
												</tr>
											</tbody>
										</table>
									</div>
								</text>
								<!--Reference to Allergies List as the source of information for this section-->
								<entry>
									<reference value="urn:uuid:66204550-8e57-11e8-b568-0800200c9a66"/>
								</entry>
							</section>
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
													<th>Location of event</th>
													<td>Community Pharmacy</td>
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
							<!--Legal information-->
							<section>
								<title value="Legal information"/>
								<code>
									<coding>
										<system value="http://snomed.info/sct"/>
										<code value="886961000000102"/>
										<display value="Legal information"/>
									</coding>
								</code>
								<text>
									<status value="additional"/>
									<div xmlns="http://www.w3.org/1999/xhtml">
										<table width="100%">
											<tbody>
												<tr>
													<th>Consent for treatment record</th>
													<td>Patient's consent for treatment has been attained.</td>
												</tr>
												<tr>
													<th>Consent for information sharing</th>
													<td>Patient is happy for the immunization details to be shares with their Registered GP.</td>
												</tr>
												<tr>
													<th>Consent relating to child</th>
													<td>Not Applicable</td>
												</tr>
											</tbody>
										</table>
									</div>
								</text>
							</section>
							<!--Eligibility Criteria-->
							<section>
								<title value="Eligibility Criteria"/>
								<code>
									<coding>
										<system value="http://snomed.info/sct"/>
										<code value="61871000000107"/>
										<display value="Eligibility for treatment"/>
									</coding>
								</code>
								<text>
									<status value="additional"/>
									<div xmlns="http://www.w3.org/1999/xhtml">
										<table width="100%">
											<tbody>
												<tr>
													<th>Eligibility criteria</th>
												</tr>
												<tr>
													<td>
														<p>Patient has Chronic Obstructive Pulmonary Disease (COPD).</p>
													</td>
												</tr>
											</tbody>
										</table>
									</div>
								</text>
							</section>
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
													<th>GP name</th>
													<td>
														<p>Prefix: Dr</p>
														<p>Given Name: Paul</p>
														<p>Family Name: Rastall</p>
													</td>
												</tr>
												<tr>
													<th>GP practice identifier</th>
													<td>
														<p>ODS Organization Code:GP123456</p>
													</td>
												</tr>
												<tr>
													<th>GP practice details</th>
													<td>
														<p>Name: MGP Medical Centre</p>
														<p>Address:</p>
														<p>Address Line: 1 MGP House, Overtown</p>
														<p>City: Leeds</p>
														<p>Post Code: LS21 7PA</p>
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
							<!--History-->
							<section>
								<title value="History"/>
								<code>
									<coding>
										<system value="http://snomed.info/sct"/>
										<code value="717121000000105"/>
										<display value="History"/>
									</coding>
								</code>
								<text>
									<status value="additional"/>
									<div xmlns="http://www.w3.org/1999/xhtml">
										<table width="100%">
											<tbody>
												<tr>
													<th>Relevant past medical, surgical and mental health history</th>
													<td>
														<p>Patient has Chronic Obstructive Pulmonary Disease (COPD). She was advised to have the flu vaccination as she is at greater risk from flu and its complications when she last attended her GP Practice.</p>
														<p>Patient requested the vaccination.</p>
														<p>No history of vaccination recorded at Pharmacy.</p>
													</td>
												</tr>
											</tbody>
										</table>
									</div>
								</text>
							</section>
							<!--Vaccinations-->
							<section>
								<title value="Vaccinations"/>
								<code>
									<coding>
										<system value="http://snomed.info/sct"/>
										<code value="1102181000000102"/>
										<display value="Immunisations"/>
									</coding>
								</code>
								<text>
									<status value="additional"/>
									<div xmlns="http://www.w3.org/1999/xhtml">
										<table width="100%">
											<tbody>
												<tr>
													<td>Vaccine product: Influvac sub-unit Tetra vaccine suspension for injection 0.5ml pre-filled syringes (Mylan)</td>
													<td>Vaccine procedure: Seasonal influenza vaccination given by pharmacist.</td>
													<td>Route: Subcutaneous route</td>
													<td>Indication: Patient requested procedure.</td>
												</tr>
												<tr>
													<td>Administered by: Mr Eric Smith</td>
													<td>GPhC identifier: 2145879</td>
													<td>Date Time: 9-May-2018 10:00</td>
												</tr>
											</tbody>
										</table>
									</div>
								</text>
								<entry>
									<reference value="urn:uuid:631ec8d3-6341-4c9e-b2a1-131af62718f2"/>
								</entry>
							</section>
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
							<!-- Patient demographics-->
							<section>
								<title value="Patient demographics"/>
								<code>
									<coding>
										<system value="http://snomed.info/sct"/>
										<code value="886731000000109"/>
										<display value="Patient demographics"/>
									</coding>
								</code>
								<text>
									<status value="additional"/>
									<div xmlns="http://www.w3.org/1999/xhtml">
										<table width="100%">
											<tbody>
												<tr>
													<th>Patient name</th>
													<td>
														<p>Prefix: Mrs</p>
														<p>Given Name: Julie</p>
														<p>Family Name: Jones</p>
													</td>
												</tr>
												<tr>
													<th>Date of birth</th>
													<td>4 May 1959</td>
												</tr>
												<tr>
													<th>Sex</th>
													<td>Female</td>
												</tr>
												<tr>
													<th>NHS number</th>
													<td>3478526985</td>
												</tr>
												<tr>
													<th>Patient address</th>
													<td>
														<p>Address Line: 22, Brightside Crescent, Overtown</p>
														<p>City: Leeds</p>
														<p>Post Code: LS10 4YU</p>
													</td>
												</tr>
												<tr>
													<th>Relevant contacts</th>
													<td>Name: Philip Jones <p>Relationship: Next of kin</p>
														<p>Contact details: Tel. 01138698975 Email. pjones@mymail.com</p>
													</td>
												</tr>
											</tbody>
										</table>
									</div>
								</text>
								<!--reference to further information carried in the patient resource-->
								<entry>
									<reference value="urn:uuid:9589fb37-87a2-48d8-968f-b371429209e3"/>
								</entry>
							</section>
							<!-- Referral details-->
							<section>
								<title value="Referral details"/>
								<code>
									<coding>
										<system value="http://snomed.info/sct"/>
										<code value="886721000000107"/>
										<display value="Referral details"/>
									</coding>
								</code>
								<text>
									<status value="generated"/>
									<div xmlns="http://www.w3.org/1999/xhtml">
										<table width="100%">
											<tbody>
												<tr>
													<th>Referral details</th>
													<td>
														<p>Self referral.</p>
													</td>
												</tr>
											</tbody>
										</table>
									</div>
								</text>
							</section>
						</Composition>
					</resource>
				</entry>
				<!--Pharmacy Encounter-->
				<entry>
					<fullUrl value="urn:uuid:1c1f74ac-b4a1-468b-b1e1-0df0e0692064"/>
					<resource>
						<!--Encounter resource providing context for the pharmacy visit-->
						<Encounter xmlns="http://hl7.org/fhir">
							<id value="1c1f74ac-b4a1-468b-b1e1-0df0e0692064"/>
							<meta>
								<profile value="https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Encounter-1"/>
							</meta>
							<status value="finished"/>
							<subject>
								<reference value="urn:uuid:9589fb37-87a2-48d8-968f-b371429209e3"/>
								<display value="JONES, Julie (Mrs)"/>
							</subject>
							<participant>
								<type>
									<coding>
										<system value="http://hl7.org/fhir/v3/ParticipationType"/>
										<code value="PPRF"/>
										<display value="primary performer"/>
									</coding>
								</type>
								<individual>
									<reference value="urn:uuid:666f8ce8-3f3b-43ac-9f8d-5bb020539d74"/>
									<display value="SMITH, Eric (Mr)"/>
								</individual>
							</participant>
							<period>
								<start value="2018-05-09T10:00:00+00:00"/>
							</period>
							<serviceProvider>
								<reference value="urn:uuid:09cf4c3d-2ba0-40dc-a633-27fca0151a91"/>
								<display value="Overtown Pharmacy"/>
							</serviceProvider>
						</Encounter>
					</resource>
				</entry>
				<!--Pharmacy associated with the encounter. -->
				<entry>
					<fullUrl value="urn:uuid:09cf4c3d-2ba0-40dc-a633-27fca0151a91"/>
					<resource>
						<Organization xmlns="http://hl7.org/fhir">
							<id value="09cf4c3d-2ba0-40dc-a633-27fca0151a91"/>
							<meta>
								<profile value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1"/>
							</meta>
							<identifier>
								<system value="https://fhir.nhs.uk/Id/ods-organization-code"/>
								<value value="FA000"/>
							</identifier>
							<name value="Overtown Pharmacy"/>
							<telecom>
								<system value="phone"/>
								<value value="01134875516"/>
							</telecom>
							<telecom>
								<system value="email"/>
								<value value="overtonpharmacy118@mymail.com"/>
							</telecom>
							<address>
								<line value="1 High Street, Overtown"/>
								<city value="Leeds"/>
								<postalCode value="LS1 9AM"/>
							</address>
						</Organization>
					</resource>
				</entry>
				<!--Patient's registered GP Practice.-->
				<entry>
					<fullUrl value="urn:uuid:94ca030c-03aa-4dae-8270-c2de2b7907ef"/>
					<resource>
						<Organization xmlns="http://hl7.org/fhir">
							<id value="94ca030c-03aa-4dae-8270-c2de2b7907ef"/>
							<meta>
								<profile value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1"/>
							</meta>
							<identifier>
								<system value="https://fhir.nhs.uk/Id/ods-organization-code"/>
								<value value="GP123456"/>
							</identifier>
							<name value="MGP Medical Centre"/>
							<address>
								<line value="1 MGP House, Overtown"/>
								<city value="Leeds"/>
								<postalCode value="LS21 7PA"/>
							</address>
						</Organization>
					</resource>
				</entry>
				<!--Patient associated with the encounter.-->
				<entry>
					<fullUrl value="urn:uuid:9589fb37-87a2-48d8-968f-b371429209e3"/>
					<resource>
						<Patient xmlns="http://hl7.org/fhir">
							<id value="9589fb37-87a2-48d8-968f-b371429209e3"/>
							<meta>
								<profile value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1"/>
							</meta>
							<identifier>
								<extension url="https://fhir.hl7.org.uk/STU3/StructureDefinition/Extension-CareConnect-NHSNumberVerificationStatus-1">
									<valueCodeableConcept>
										<coding>
											<system value="https://fhir.hl7.org.uk/STU3/CodeSystem/CareConnect-NHSNumberVerificationStatus-1"/>
											<code value="01"/>
											<display value="Number present and verified"/>
										</coding>
									</valueCodeableConcept>
								</extension>
								<system value="https://fhir.nhs.uk/Id/nhs-number"/>
								<value value="3478526985"/>
							</identifier>
							<name>
								<use value="official"/>
								<text value="Mrs Julie Jones"/>
								<family value="Jones"/>
								<given value="Julie"/>
								<prefix value="Mrs"/>
							</name>
							<telecom>
								<system value="phone"/>
								<value value="01138698975"/>
								<use value="home"/>
							</telecom>
							<gender value="female"/>
							<birthDate value="1959-05-04"/>
							<address>
								<use value="home"/>
								<type value="both"/>
								<text value="22 Brightside Crescent, Overtown, West Yorkshire, LS10 4YU"/>
								<line value="22 Brightside Crescent"/>
								<city value="Overtown"/>
								<district value="West Yorkshire"/>
								<postalCode value="LS10 4YU"/>
							</address>
							<maritalStatus>
								<coding>
									<system value="http://hl7.org/fhir/v3/MaritalStatus"/>
									<code value="M"/>
									<display value="Married"/>
								</coding>
							</maritalStatus>
							<contact>
								<relationship>
									<coding>
										<system value="http://hl7.org/fhir/v2/0131"/>
										<code value="N"/>
										<display value="Next-of-Kin"/>
									</coding>
								</relationship>
								<name>
									<use value="official"/>
									<family value="Jones"/>
									<given value="Philip"/>
								</name>
								<telecom>
									<system value="phone"/>
									<value value="01138698975"/>
								</telecom>
								<telecom>
									<system value="email"/>
									<value value="pjones@mymail.com"/>
								</telecom>
								<gender value="male"/>
							</contact>
							<generalPractitioner>
								<reference value="urn:uuid:4d8b5538-c495-459c-9187-6a050ebc06ea"/>
							</generalPractitioner>
							<managingOrganization>
								<reference value="urn:uuid:94ca030c-03aa-4dae-8270-c2de2b7907ef"/>
							</managingOrganization>
						</Patient>
					</resource>
				</entry>
				<!--Patient's registered GP.-->
				<entry>
					<fullUrl value="urn:uuid:4d8b5538-c495-459c-9187-6a050ebc06ea"/>
					<resource>
						<Practitioner xmlns="http://hl7.org/fhir">
							<id value="4d8b5538-c495-459c-9187-6a050ebc06ea"/>
							<meta>
								<profile value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1"/>
							</meta>
							<identifier>
								<system value="https://fhir.hl7.org.uk/Id/gmc-number"/>
								<value value="6122477"/>
							</identifier>
							<name>
								<family value="Rastall"/>
								<given value="Paul"/>
								<prefix value="Dr"/>
							</name>
							<telecom>
								<system value="phone"/>
								<value value="01136323200"/>
								<use value="work"/>
							</telecom>
							<gender value="male"/>
						</Practitioner>
					</resource>
				</entry>
				<!--Pharmacist associated with the encounter. -->
				<entry>
					<fullUrl value="urn:uuid:666f8ce8-3f3b-43ac-9f8d-5bb020539d74"/>
					<resource>
						<Practitioner xmlns="http://hl7.org/fhir">
							<id value="666f8ce8-3f3b-43ac-9f8d-5bb020539d74"/>
							<meta>
								<profile value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1"/>
							</meta>
							<identifier>
								<system value="https://fhir.hl7.org.uk/Id/gphc-number"/>
								<value value="2145879"/>
							</identifier>
							<name>
								<family value="Smith"/>
								<given value="Eric"/>
								<prefix value="Mr"/>
							</name>
							<telecom>
								<system value="phone"/>
								<value value="0113895123"/>
								<use value="work"/>
							</telecom>
							<gender value="male"/>
						</Practitioner>
					</resource>
				</entry>
				<!--Vaccinations administered during the encounter-->
				<entry>
					<fullUrl value="urn:uuid:631ec8d3-6341-4c9e-b2a1-131af62718f2"/>
					<resource>
						<Immunization xmlns="http://hl7.org/fhir">
							<id value="631ec8d3-6341-4c9e-b2a1-131af62718f2"/>
							<meta>
								<profile value="https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-DM-Immunization-1"/>
							</meta>
							<extension url="https://fhir.hl7.org.uk/STU3/StructureDefinition/Extension-CareConnect-VaccinationProcedure-1">
								<valueCodeableConcept>
									<coding>
										<system value="http://snomed.info/sct"/>
										<code value="955691000000108"/>
										<display value="Seasonal influenza vaccination given by pharmacist"/>
									</coding>
								</valueCodeableConcept>
							</extension>
							<status value="completed"/>
							<notGiven value="false"/>
							<vaccineCode>
								<coding>
									<system value="http://snomed.info/sct"/>
									<code value="35727111000001109"/>
									<display value="Influvac sub-unit Tetra vaccine suspension for injection 0.5ml pre-filled syringes (Mylan)"/>
								</coding>
							</vaccineCode>
							<patient>
								<reference value="urn:uuid:9589fb37-87a2-48d8-968f-b371429209e3"/>
								<display value="JONES, Julie (Mrs)"/>
							</patient>
							<encounter>
								<reference value="urn:uuid:1c1f74ac-b4a1-468b-b1e1-0df0e0692064"/>
							</encounter>
							<date value="2018-05-09"/>
							<primarySource value="true"/>
							<site>
								<coding>
									<system value="http://snomed.info/sct"/>
									<code value="368209003"/>
									<display value="Right upper arm"/>
								</coding>
							</site>
							<route>
								<coding>
									<system value="http://snomed.info/sct"/>
									<code value="34206005"/>
									<display value="Subcutaneous route"/>
								</coding>
							</route>
							<practitioner>
								<role>
									<coding>
										<system value="http://hl7.org/fhir/v2/0443"/>
										<code value="AP"/>
										<display value="Administering Provider"/>
									</coding>
								</role>
								<actor>
									<reference value="urn:uuid:666f8ce8-3f3b-43ac-9f8d-5bb020539d74"/>
									<display value="SMITH, Eric (Mr)"/>
								</actor>
							</practitioner>
							<explanation>
								<reason>
									<coding>
										<system value="http://snomed.info/sct"/>
										<code value="398192003"/>
										<display value="Co-morbid conditions"/>
									</coding>
								</reason>
							</explanation>
						</Immunization>
					</resource>
				</entry>
				<!--Allergies list-->
				<entry>
					<fullUrl value="urn:uuid:66204550-8e57-11e8-b568-0800200c9a66"/>
					<resource>
						<List xmlns="http://hl7.org/fhir">
							<id value="66204550-8e57-11e8-b568-0800200c9a66"/>
							<meta>
								<profile value="https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Allergy-List-1"/>
							</meta>
							<identifier>
								<system value="https://tools.ietf.org/html/rfc4122"/>
								<value value="66204550-8e57-11e8-b568-0800200c9a66"/>
							</identifier>
							<status value="current"/>
							<mode value="snapshot"/>
							<code>
								<coding>
									<system value="http://snomed.info/sct"/>
									<code value="886921000000105"/>
									<display value="Allergies and adverse reactions"/>
								</coding>
							</code>
							<subject>
								<reference value="urn:uuid:9589fb37-87a2-48d8-968f-b371429209e3"/>
								<display value="JONES, Julie (Mrs)"/>
							</subject>
							<encounter>
								<reference value="urn:uuid:1c1f74ac-b4a1-468b-b1e1-0df0e0692064"/>
							</encounter>
							<source>
								<reference value="urn:uuid:666f8ce8-3f3b-43ac-9f8d-5bb020539d74"/>
								<display value="SMITH, Eric (Mr)"/>
							</source>
							<entry>
								<item>
									<reference value="urn:uuid:11003483-70bf-4025-805f-a9defed13e9a"/>
								</item>
							</entry>
						</List>
					</resource>
				</entry>
				<!--Allergies documented during the encounter.-->
				<entry>
					<fullUrl value="urn:uuid:11003483-70bf-4025-805f-a9defed13e9a"/>
					<resource>
						<AllergyIntolerance xmlns="http://hl7.org/fhir">
							<id value="11003483-70bf-4025-805f-a9defed13e9a"/>
							<meta>
								<profile value="https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-AllergyIntolerance-1"/>
							</meta>
							<identifier>
								<system value="https://tools.ietf.org/html/rfc4122"/>
								<value value="11003483-70bf-4025-805f-a9defed13e9a"/>
							</identifier>
							<clinicalStatus value="active"/>
							<verificationStatus value="confirmed"/>
							<code>
								<coding>
									<system value="http://snomed.info/sct"/>
									<code value="716186003"/>
									<display value="No known allergy"/>
								</coding>
							</code>
							<patient>
								<reference value="urn:uuid:9589fb37-87a2-48d8-968f-b371429209e3"/>
								<display value="JONES, Julie (Mrs)"/>
							</patient>
							<assertedDate value="2018-05-09"/>
						</AllergyIntolerance>
					</resource>
				</entry>
			</Bundle>
		</resource>
	</entry>
</Bundle>
<!--</xml>-->
```
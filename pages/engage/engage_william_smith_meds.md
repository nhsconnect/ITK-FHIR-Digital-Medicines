---
title: William Smith Pharmacy Emergency Supply Scenario
keywords: workflow
tags: [development,fhir,profiles]
sidebar: overview_sidebar
permalink: engage_william_smith_meds.html
summary: "Example scenario - William Smith Pharmacy Emergency Supply Notification"
---

## Background ##

Mr Smith is a 62 year old gentleman who has Type 2 Diabetes and Hypertension. He is on a number of regular medicines for management of his long term conditions.
Mr Smith’s wife usually orders his medication for him each month but she has recently been unwell.

It is Easter bank holiday weekend and Mr Smith suddenly realises on the Friday morning that he only has two more doses of his insulin remaining. Mr Smith calls his daughter who advises he rings NHS111 for advice as his GP practice is closed.
- When Mr Smith rings NHS111, the call handler advises him that as his insulin is a regular, repeat medication he can obtain this as an “emergency supply” from a nearby pharmacy free of charge. 
- Mr Smith is given the option to select from 2 nearby pharmacies to collect the medication from.
- Once Mr Smith selects the pharmacy he would like to go to, the call handler completes a referral and sends this to the selected pharmacy.

Mr Smith arrives at the selected pharmacy.
- The pharmacist asks Mr Smith to confirm which insulin he is on and if Mr Smith is happy for the pharmacist to confirm this by accessing his SCR.
- The pharmacist is happy that the insulin details are correct and decides to supply the medication enough to last him at least 2 weeks, together with a pack of needles.
- The pharmacist asks Mr Smith if he is happy for the details of this supply to be shared with his GP. Mr Smith agrees.
- The pharmacist sends the relevant information captured from Mr Smith to his GP. 
- The pharmacist also advises Mr Smith that he should consider discussing with his GP whether he can be set up for electronic repeat dispensing if his medication regime is stable. This will mean Mr Smith does not need to order his medicines via the GP each month. The GP can simply authorise prescriptions in a batch of for example 6 months and Mr Smith simply has to collect from his usual pharmacy each month the medicines which he needs.
- Mr Smith says he will consider this and thanks the pharmacist for the emergency supply.

## The Pharmacy Encounter ##

The Pharmacy Encounter is documented in the [Encounter Resource](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Encounter-1)

## Named Participants ##

- Patient - **William Smith** - [Patient Resource](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1)
- Pharmacist (Document Author) - **Mr Eric Smith** - [Practitioner Resource](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1)
- Patient's GP (Document Recipient) - **Dr Paul Rastall** - [Practitioner Resource](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1)

## Named Organisations ##

- Pharmacy - **Overtown Pharmacy** - [Organization Resource](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- Patient's GP Practice - **MGP Medical Centre** - [Organization Resource](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)

## Example Instance of Scenario ##

{% include note.html content="These examples have not been clinically assured against Digital Medicines use cases.<br/>Examples are illustrative only." %}

```
<xml>
<?xml version="1.0" encoding="UTF-8"?>
<!--This xml example is for illustrative purposes only and has not been clinically verified.-->
<Bundle xmlns="http://hl7.org/fhir">
	<id value="32e2adf8-595b-4b39-b6f1-f0073464c7f8"/>
	<meta>
		<lastUpdated value="2018-08-28T10:00:00+00:00"/>
		<profile value="https://fhir.nhs.uk/STU3/StructureDefinition/ITK-Document-Bundle-1"/>
	</meta>
	<identifier>
		<system value="https://tools.ietf.org/html/rfc4122"/>
		<value value="b19b305c-697b-4d76-b97f-9b2ef2914d10"/>
	</identifier>
	<type value="document"/>
	<!--Emergency Medication Supply Notification Document-->
	<entry>
		<fullUrl value="urn:uuid:cf325583-18e2-4c56-8d91-9fdeaee79ade"/>
		<resource>
			<!--A resource carrying a set of healthcare-related information about the patient-->
			<Composition xmlns="http://hl7.org/fhir">
				<id value="cf325583-18e2-4c56-8d91-9fdeaee79ade"/>
				<meta>
					<profile value="https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-DM-EmergencySupply-Composition-1"/>
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
					<value value="1ed8db1e-968d-4332-811c-92df8b240fdc"/>
				</identifier>
				<!--The workflow/clinical status of this composition. The status is a marker for the clinical standing of the document.-->
				<status value="final"/>
				<type>
					<!--Digital Medicines document type-->
					<coding>
						<system value="http://snomed.info/sct"/>
						<code value="1218611000000102"/>
						<display value="Urgent supply of prescription items by community pharmacy"/>
					</coding>
				</type>
				<!--Reference to the patient subject of the Composition-->
				<subject>
					<reference value="urn:uuid:1e2b5223-1cd8-43ff-8a67-55dec3edb9b0"/>
				</subject>
				<!--Reference to the clinical encounter or type of care this documentation is associated with.-->
				<encounter>
					<reference value="urn:uuid:adb353f9-0953-4fb4-a4ab-f0ab04a44dbc"/>
				</encounter>
				<!--The composition editing time, when the composition was last logically changed by the author.-->
				<date value="2018-05-09T10:00:00+00:00"/>
				<!--Identifies who is responsible for the information in the composition, 
not necessarily who typed it in-->
				<author>
					<reference value="urn:uuid:0e4c13d4-e61f-48f2-89ee-7cf8f5f3dbb3"/>
				</author>
				<title value="Overtown Pharmacy 118 Emergency Medication Supply Record"/>
				<!--Identifies the organization responsible for ongoing maintenance of and access 
to the composition/document information.-->
				<custodian>
					<reference value="urn:uuid:1226082b-315e-40be-83cf-5d21a964219e"/>
				</custodian>
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
										<th>Service</th>
										<td>Community Pharmacist Consultation Service</td>
									</tr>
									<tr>
										<th>Organisation</th>
										<td>
											<p>Name: Overtown Pharmacy</p>
											<p>Address: 1 High Street, Overtown, Leeds</p>
											<p>Postcode: LS1 9AM</p>
											<p>Telephone: 01134875516</p>
											<p>Email: overtonpharmacy118@mymail.com</p>
										</td>
									</tr>
									<tr>
										<th>Clincian</th>
										<td>
											<p>Name: Mr Eric Smith</p>
											<p>Role: Pharmacist</p>
											<p>Registration No: 2145879</td>
									</tr>
									<tr>
										<th>Person collecting the medication</th>
										<td>Patient</td>
									</tr>
									<tr>
										<th>Reason for service</th>
										<td>Emergency supply of medication. Patient had not ordered their prescription.</td>
									</tr>
								</tbody>
							</table>
						</div>
					</text>
					<!--Reference to Encounter resource as the source of information for this section-->
					<entry>
						<reference value="urn:uuid:adb353f9-0953-4fb4-a4ab-f0ab04a44dbc"/>
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
										<th>Consent relating to child</th>
										<td>Not Applicable</td>
									</tr>
								</tbody>
							</table>
						</div>
					</text>
				</section>
				<!-- GP Practice-->
				<section>
					<title value="GP Practice"/>
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
						<reference value="urn:uuid:e46d86bf-1720-4c55-878f-a034d8349bbd"/>
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
											<p>Patient has Type 2 diabetes and hypertension.</p>
										</td>
									</tr>
								</tbody>
							</table>
						</div>
					</text>
				</section>
				<!--Information and advice given-->
				<section>
					<title value="Information and Advice given"/>
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
											<p>Patient advised that he should consider discussing with his GP whether he can be set up for electronic repeat dispensing if his medication regime is stable.</p>
										</td>
									</tr>
								</tbody>
							</table>
						</div>
					</text>
				</section>
				<!-- Medications and medical devices-->
				<section>
					<title value="Medications and medical devices"/>
					<code>
						<coding>
							<system value="http://snomed.info/sct"/>
							<code value="933361000000108"/>
							<display value="Medications and medical devices"/>
						</coding>
					</code>
					<text>
						<status value="additional"/>
						<div xmlns="http://www.w3.org/1999/xhtml">
							<table width="100%">
								<tbody>
									<tr>
										<th>Medication</th>
										<td>Humulin M3 100units/ml suspension for injection 3ml cartridges (CST Pharma Ltd)</td>
									</tr>
									<tr>
										<th>Dose directions</th>
										<td>As needed</td>
									</tr>
									<tr>
										<th>Quantity Supplied</th>
										<td>2 cartridge</td>
									</tr>
									<tr>
										<th>Days Supply</th>
										<td>14 days</td>
									</tr>
									<tr>
										<th>Medication</th>
										<td>BD Viva hypodermic insulin needles for pre-filled / reusable pen injectors screw on 5mm/31gauge (Becton, Dickinson UK Ltd)</td>
									</tr>
									<tr>
										<th>Dose directions</th>
										<td>As needed</td>
									</tr>
									<tr>
										<th>Quantity Supplied</th>
										<td>90 needle</td>
									</tr>
									<tr>
										<th>Days Supply</th>
										<td>14 days</td>
									</tr>
								</tbody>
							</table>
						</div>
					</text>
					<!--reference to further information carried in the medication dispense list resource-->
					<entry>
						<reference value="urn:uuid:4bc7faea-5974-407a-b658-d6ed1d4c9187"/>
					</entry>
				</section>
				<!-- Patient demographics-->
				<section>
					<title value="Patient Demographics"/>
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
										<th>Patient</th>
										<td>
											<p>Prefix: Mr</p>
											<p>Given Name: William</p>
											<p>Family Name: Smith</p>
										</td>
									</tr>
									<tr>
										<th>Date of birth</th>
										<td>4 February 1956</td>
									</tr>
									<tr>
										<th>Gender</th>
										<td>Male</td>
									</tr>
									<tr>
										<th>NHS number</th>
										<td>2378954317</td>
									</tr>
									<tr>
										<th>Patient address</th>
										<td>
											<p>Address Line: 14, Sunny Mews, Overtown,</p>
											<p>City: Leeds</p>
											<p>Post Code: LS17 4NK</p>
										</td>
									</tr>
									<tr>
										<th>Patient telephone number</th>
										<td>
											<p>Home: 01135540935</p>
											<p>Mobile: 07823123456</p>
										</td>
									</tr>
									<tr>
										<th>Relevant contacts</th>
										<td>Name: June Smith <p>Relationship: Next of kin</p>
											<p>Contact details: Tel. 01132789365</p>
										</td>
									</tr>
								</tbody>
							</table>
						</div>
					</text>
					<!--reference to further information carried in the patient resource-->
					<entry>
						<reference value="urn:uuid:1e2b5223-1cd8-43ff-8a67-55dec3edb9b0"/>
					</entry>
				</section>
				<!--Plan and requested actions - GP to review medication and speak to Patient about repeat prescriptions-->
				<section>
					<title value="Plan and requested actions"/>
					<code>
						<coding>
							<system value="http://snomed.info/sct"/>
							<code value="887201000000105"/>
							<display value="Plan and requested actions"/>
						</coding>
					</code>
					<text>
						<status value="generated"/>
						<div xmlns="http://www.w3.org/1999/xhtml">
							<table width="100%">
								<tbody>
									<tr>
										<th>Plan and requested actions</th>
										<td>GP to review medications and speak to Patient regarding electronic repeat dispensing</td>
									</tr>
								</tbody>
							</table>
						</div>
					</text>
				</section>
				<!-- Referral details-->
				<section>
					<title value="Referral Details"/>
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
										<td>NHS 111</td>
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
		<fullUrl value="urn:uuid:adb353f9-0953-4fb4-a4ab-f0ab04a44dbc"/>
		<resource>
			<!--Encounter resource providing context for the pharmacy visit-->
			<Encounter>
				<id value="adb353f9-0953-4fb4-a4ab-f0ab04a44dbc"/>
				<meta>
					<profile value="https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Encounter-1"/>
				</meta>
				<status value="finished"/>
				<subject>
					<reference value="urn:uuid:1e2b5223-1cd8-43ff-8a67-55dec3edb9b0"/>
					<display value="SMITH, William (Mr)"/>
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
						<reference value="urn:uuid:0e4c13d4-e61f-48f2-89ee-7cf8f5f3dbb3"/>
						<display value="SMITH, Eric (Mr)"/>
					</individual>
				</participant>
				<period>
					<start value="2018-05-09T10:00:00+00:00"/>
				</period>
				<serviceProvider>
					<reference value="urn:uuid:1226082b-315e-40be-83cf-5d21a964219e"/>
					<display value="Overtown Pharmacy"/>
				</serviceProvider>
			</Encounter>
		</resource>
	</entry>
	<!--Pharmacy associated with the encounter. -->
	<entry>
		<fullUrl value="urn:uuid:1226082b-315e-40be-83cf-5d21a964219e"/>
		<resource>
			<Organization>
				<id value="1226082b-315e-40be-83cf-5d21a964219e"/>
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
		<fullUrl value="urn:uuid:e46d86bf-1720-4c55-878f-a034d8349bbd"/>
		<resource>
			<Organization>
				<id value="e46d86bf-1720-4c55-878f-a034d8349bbd"/>
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
		<fullUrl value="urn:uuid:1e2b5223-1cd8-43ff-8a67-55dec3edb9b0"/>
		<resource>
			<Patient>
				<id value="1e2b5223-1cd8-43ff-8a67-55dec3edb9b0"/>
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
					<value value="2378954317"/>
				</identifier>
				<name>
					<use value="official"/>
					<text value="Mr William Smith"/>
					<family value="Smith"/>
					<given value="William"/>
					<prefix value="Mr"/>
				</name>
				<telecom>
					<system value="phone"/>
					<value value="01132789365"/>
					<use value="home"/>
				</telecom>
				<gender value="male"/>
				<birthDate value="1956-02-04"/>
				<address>
					<use value="home"/>
					<type value="both"/>
					<text value="14 Sunny Mews, Overtown, West Yorkshire, LS17 4NK"/>
					<line value="14 Sunny Mews"/>
					<city value="Overtown"/>
					<district value="West Yorkshire"/>
					<postalCode value="LS17 4NK"/>
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
						<family value="Smith"/>
						<given value="June"/>
					</name>
					<telecom>
						<system value="phone"/>
						<value value="01132789365"/>
					</telecom>
					<gender value="female"/>
				</contact>
				<generalPractitioner>
					<reference value="urn:uuid:33cd4a2a-417f-4449-8293-31b15ea37470"/>
				</generalPractitioner>
				<managingOrganization>
					<reference value="urn:uuid:e46d86bf-1720-4c55-878f-a034d8349bbd"/>
				</managingOrganization>
			</Patient>
		</resource>
	</entry>
	<!--Patient's registered GP.-->
	<entry>
		<fullUrl value="urn:uuid:33cd4a2a-417f-4449-8293-31b15ea37470"/>
		<resource>
			<Practitioner>
				<id value="33cd4a2a-417f-4449-8293-31b15ea37470"/>
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
		<fullUrl value="urn:uuid:0e4c13d4-e61f-48f2-89ee-7cf8f5f3dbb3"/>
		<resource>
			<Practitioner>
				<id value="0e4c13d4-e61f-48f2-89ee-7cf8f5f3dbb3"/>
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
	<!--List of medications dispensed during the pharmacy visit-->
	<entry>
		<fullUrl value="urn:uuid:4bc7faea-5974-407a-b658-d6ed1d4c9187"/>
		<resource>
			<List>
				<id value="4bc7faea-5974-407a-b658-d6ed1d4c9187"/>
				<meta>
					<profile value="https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-MedicationDispense-List-1"/>
				</meta>
				<identifier>
					<system value="https://tools.ietf.org/html/rfc4122"/>
					<value value="197987da-97a7-49c2-9657-dac1aea2a461"/>
				</identifier>
				<status value="current"/>
				<mode value="snapshot"/>
				<code>
					<coding>
						<system value="http://snomed.info/sct"/>
						<code value="163541000000107"/>
						<display value="Dispensed Medication"/>
					</coding>
				</code>
				<subject>
					<reference value="urn:uuid:1e2b5223-1cd8-43ff-8a67-55dec3edb9b0"/>
					<display value="SMITH, William (Mr)"/>
				</subject>
				<encounter>
					<reference value="urn:uuid:adb353f9-0953-4fb4-a4ab-f0ab04a44dbc"/>
				</encounter>
				<date value="2018-05-09"/>
				<entry>
					<item>
						<reference value="urn:uuid:0885779a-82e7-11ea-bc55-0242ac130003"/>
					</item>
				</entry>
				<entry>
					<item>
						<reference value="urn:uuid:42ac049c-87ca-4e33-93ad-987167422b01"/>
					</item>
				</entry>
			</List>
		</resource>
	</entry>
	<!--Record of the Medication dispense-->
	<entry>
		<fullUrl value="urn:uuid:0885779a-82e7-11ea-bc55-0242ac130003"/>
		<resource>
			<MedicationDispense>
				<id value="0885779a-82e7-11ea-bc55-0242ac130003"/>
				<meta>
					<profile value="https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-MedicationDispense-1"/>
				</meta>
				<status value="completed"/>
				<medicationReference>
					<reference value="urn:uuid:f315872e-82e6-11ea-bc55-0242ac130003"/>
					<display value="Humulin M3 100units/ml suspension for injection 3ml cartridges (CST Pharma Ltd)"/>
				</medicationReference>
				<subject>
					<reference value="urn:uuid:1e2b5223-1cd8-43ff-8a67-55dec3edb9b0"/>
					<display value="SMITH, William (Mr)"/>
				</subject>
				<context>
					<reference value="urn:uuid:adb353f9-0953-4fb4-a4ab-f0ab04a44dbc"/>
				</context>
				<performer>
					<actor>
						<reference value="urn:uuid:0e4c13d4-e61f-48f2-89ee-7cf8f5f3dbb3"/>
					</actor>
					<onBehalfOf>
						<reference value="urn:uuid:1226082b-315e-40be-83cf-5d21a964219e"/>
					</onBehalfOf>
				</performer>
				<type>
					<coding>
						<system value="http://snomed.info/sct"/>
						<code value="1218611000000102"/>
						<display value="Urgent supply of prescription items by community pharmacy"/>
					</coding>
				</type>
				<quantity>
					<extension url="https://fhir.hl7.org.uk/STU3/StructureDefinition/Extension-CareConnect-MedicationQuantityText-1">
						<valueString value="2 cartridge"/>
					</extension>
					<value value="2"/>
					<unit value="cartridge"/>
					<system value="http://snomed.info/sct"/>
					<code value="732988008"/>
				</quantity>
				<daysSupply>
					<value value="14"/>
					<unit value="day"/>
					<system value="http://unitsofmeasure.org"/>
					<code value="d"/>
				</daysSupply>
				<whenPrepared value="2018-05-09"/>
				<whenHandedOver value="2018-05-09"/>
				<dosageInstruction>
					<asNeededBoolean value="true"/>
				</dosageInstruction>
			</MedicationDispense>
		</resource>
	</entry>
	<!--Record of the Medication dispense-->
	<entry>
		<fullUrl value="urn:uuid:42ac049c-87ca-4e33-93ad-987167422b01"/>
		<resource>
			<MedicationDispense>
				<id value="42ac049c-87ca-4e33-93ad-987167422b01"/>
				<meta>
					<profile value="https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-MedicationDispense-1"/>
				</meta>
				<status value="completed"/>
				<medicationReference>
					<reference value="urn:uuid:9c7e61c3-5b92-4828-9ebc-21e74bcdbc96"/>
					<display value="BD Viva hypodermic insulin needles for pre-filled / reusable pen injectors screw on 5mm/31gauge (Becton, Dickinson UK Ltd)"/>
				</medicationReference>
				<subject>
					<reference value="urn:uuid:1e2b5223-1cd8-43ff-8a67-55dec3edb9b0"/>
					<display value="SMITH, William (Mr)"/>
				</subject>
				<context>
					<reference value="urn:uuid:adb353f9-0953-4fb4-a4ab-f0ab04a44dbc"/>
				</context>
				<performer>
					<actor>
						<reference value="urn:uuid:0e4c13d4-e61f-48f2-89ee-7cf8f5f3dbb3"/>
					</actor>
					<onBehalfOf>
						<reference value="urn:uuid:1226082b-315e-40be-83cf-5d21a964219e"/>
					</onBehalfOf>
				</performer>
				<type>
					<coding>
						<system value="http://snomed.info/sct"/>
						<code value="1218611000000102"/>
						<display value="Urgent supply of prescription items by community pharmacy"/>
					</coding>
				</type>
				<quantity>
					<extension url="https://fhir.hl7.org.uk/STU3/StructureDefinition/Extension-CareConnect-MedicationQuantityText-1">
						<valueString value="90 needle"/>
					</extension>
					<value value="90"/>
					<unit value="needle"/>
					<system value="http://snomed.info/sct"/>
					<code value="3318111000001106"/>
				</quantity>
				<daysSupply>
					<value value="14"/>
					<unit value="day"/>
					<system value="http://unitsofmeasure.org"/>
					<code value="d"/>
				</daysSupply>
				<whenPrepared value="2018-05-09"/>
				<whenHandedOver value="2018-05-09"/>
				<dosageInstruction>
					<asNeededBoolean value="true"/>
				</dosageInstruction>
			</MedicationDispense>
		</resource>
	</entry>
	<!--Medication prescribed-->
	<entry>
		<fullUrl value="urn:uuid:f315872e-82e6-11ea-bc55-0242ac130003"/>
		<resource>
			<Medication>
				<id value="f315872e-82e6-11ea-bc55-0242ac130003"/>
				<meta>
					<profile value="https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Medication-1"/>
				</meta>
				<code>
					<coding>
						<system value="http://snomed.info/sct"/>
						<code value="37417211000001103"/>
						<display value="Humulin M3 100units/ml suspension for injection 3ml cartridges (CST Pharma Ltd)"/>
					</coding>
				</code>
				<status value="active"/>
			</Medication>
		</resource>
	</entry>
	<!--Medication prescribed-->
	<entry>
		<fullUrl value="urn:uuid:9c7e61c3-5b92-4828-9ebc-21e74bcdbc96"/>
		<resource>
			<Medication>
				<id value="9c7e61c3-5b92-4828-9ebc-21e74bcdbc96"/>
				<meta>
					<profile value="https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Medication-1"/>
				</meta>
				<code>
					<coding>
						<system value="http://snomed.info/sct"/>
						<code value="31771611000001107"/>
						<display value="BD Viva hypodermic insulin needles for pre-filled / reusable pen injectors screw on 5mm/31gauge (Becton, Dickinson UK Ltd)"/>
					</coding>
				</code>
				<status value="active"/>
			</Medication>
		</resource>
	</entry>
</Bundle>
</xml>
```

## Example Instance of Scenario - ITK Wrapper ##

{% include note.html content="These examples have not been clinically assured against Digital Medicines use cases.<br/>Examples are illustrative only." %}

```
<?xml version="1.0" encoding="UTF-8"?>
<Bundle
	xmlns="http://hl7.org/fhir">
	<id value="e6492db3-3788-4519-bebd-2bdf7d7236d9"/>
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
							<reference value="https://fhir.nhs.uk/STU3/MessageDefinition/ITK-DM-EmergencySupply-MessageDefinition-1"/>
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
					<code value="ITK010D"/>
					<display value="ITK Digital Medicine Emergency Supply Document"/>
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
	<!--Organization (sender.reference) -->
	<entry>
		<fullUrl value="urn:uuid:b86216fe-6a51-4687-af97-4b7d58154c39"/>
		<resource>
			<Organization>
				<id value="b86216fe-6a51-4687-af97-4b7d58154c39"/>
				<meta>
					<profile value="https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Header-Organization-1"/>
				</meta>
				<identifier>
					<system value="https://fhir.nhs.uk/Id/ods-organization-code"/>
					<value value="FA000"/>
				</identifier>
			</Organization>
		</resource>
	</entry>
	<!--Organization (receiver.reference)-->
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
					<value value="GP123456"/>
				</identifier>
			</Organization>
		</resource>
	</entry>
	<entry>
		<fullUrl value="urn:uuid:289f9d42-6f97-40d2-890a-d3d0af397ac7"/>
		<resource>
		
<!-- INSERT THE ROOT <Bundle> FROM THE ABOVE EXAMLE -->	
			
		</resource>
	</entry>
</Bundle>
</xml>
```
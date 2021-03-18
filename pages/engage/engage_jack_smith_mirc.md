---
title: Jack Smith Minor Illness Referral Consultation (MIRC) Scenario
keywords: workflow
tags: [development,fhir,profiles]
sidebar: overview_sidebar
permalink: engage_jack_smith_mirc.html
summary: "Example scenario - Jack Smith Minor Illness Referral Consultation (MIRC) Scenario"
---

## Background ##

Jack Smith is a 14 year old who has called NHS 111 because his eye is sore. The NHS 111 call-handler reviews Jack's symptoms. Jack appears to have conjunctivitis, and is referred to the community pharmacist for treatment.

Catherine Jones, the community pharmacist receives the referral.

The pharmacist has a consultation with Jack, examines his eye and asks him about his symptoms.

The pharmacist supplies Jack with some chloramphenicol eye drops and advises him about treatment.

She records details of the consultation and supply on the pharmacy computer system.

Details of Jack's pharmacy referral from NHS 111 are transferred to Jack's GP.

## The Minor Illness Referral Consultation (MIRC) Encounter ##

The MIRC encounter is documented in the [Encounter Resource](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Encounter-1)

## Named Participants ##

- Patient - **Jack Smith** - [Patient Resource](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1)
- Pharmacist - **Catherine Jones** - [Practitioner Resource](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1)

## Named Organisations ##

- NHS 111 Call Centre - **HAMPSHIRE NHS 111 CALL CENTRE** - [Organization Resource](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1)
- Pharmacy - **Andover Pharmacy** - [Organization Resource](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1)
- Patient's GP Practice - **ANDOVER Medical Centre** - [Organization Resource](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1)

## Example Instance of Scenario ##

{% include note.html content="These examples have not been clinically assured against Digital Medicines use cases.<br/>Examples are illustrative only. They do not imply business requirements in terms of the ITK Wrapper population, or clinical requirements for SNOMED CT representations." %}

```
<!--<xml>-->
<!--This xml example is for illustrative purposes only and has not been clinically verified.-->
<Bundle xmlns="http://hl7.org/fhir">
	<id value="2fe7a417-20f8-4b47-a869-6a3dc72c9ff4"/>
	<meta>
		<lastUpdated value="2021-03-09T10:00:00+00:00"/>
		<profile value="https://fhir.nhs.uk/STU3/StructureDefinition/ITK-Document-Bundle-1"/>
	</meta>
	<identifier>
		<system value="https://tools.ietf.org/html/rfc4122"/>
		<value value="d6e3638c-80f1-11eb-8dcd-0242ac130003"/>
	</identifier>
	<type value="document"/>
	<!--Minor Illness Referral Consultation Document-->
	<entry>
		<fullUrl value="urn:uuid:19bc2bf3-abd0-4da8-b9f1-60e36554489b"/>
		<resource>
			<!--A resource carrying a set of healthcare-related information about the patient-->
			<Composition xmlns="http://hl7.org/fhir">
				<id value="19bc2bf3-abd0-4da8-b9f1-60e36554489b"/>
				<meta>
					<profile value="https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-DM-DMIRS-Composition-1"/>
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
					<value value="4dd3b461-83be-41e4-99eb-0d8d04fb5508"/>
				</identifier>
				<!--The workflow/clinical status of this composition. The status is a marker for the clinical standing of the document.-->
				<status value="final"/>
				<type>
					<!--Digital Medicines document type-->
					<coding>
						<system value="http://snomed.info/sct"/>
						<code value="1321521000000101"/>
						<display value="Supply of medication for minor illness by community pharmacy"/>
					</coding>
				</type>
				<!--Reference to the patient subject of the Composition-->
				<subject>
					<reference value="urn:uuid:9af701f7-5eb2-4402-bb3c-8ef8c8190082"/>
				</subject>
				<!--Reference to the clinical encounter or type of care this documentation is associated with.-->
				<encounter>
					<reference value="urn:uuid:d96ac9ee-208d-487b-8321-25eb895a3d31"/>
				</encounter>
				<!--The composition editing time, when the composition was last logically changed by the author.-->
				<date value="2021-03-09T09:34:00+00:00"/>
				<!--Identifies who is responsible for the information in the composition, 
not necessarily who typed it in-->
				<author>
					<reference value="urn:uuid:185e4d61-be11-4bd9-81ab-07a9e489566d"/>
				</author>
				<title value="ANDOVER PHARMACY Community Pharmacist Minor Illness Referral Consultation Service"/>
				<!--Identifies the organization responsible for ongoing maintenance of and access 
to the composition/document information.-->
				<custodian>
					<reference value="urn:uuid:f038775b-64a6-4afa-8de3-ae9266b11408"/>
				</custodian>
				<!--Referrer details-->
				<section>
					<title value="Referrer Details"/>
					<code>
						<coding>
							<system value="http://snomed.info/sct"/>
							<code value="1052891000000108"/>
							<display value="Referrer details"/>
						</coding>
					</code>
					<text>
						<status value="additional"/>
						<div xmlns="http://www.w3.org/1999/xhtml">
							<table width="100%">
								<tbody>
									<tr>
										<th>Referral record</th>
										<td>Active</td>
									</tr>
									<tr>
										<th>Referrer provider name</th>
										<td>HAMPSHIRE NHS 111 CALL CENTRE</td>
									</tr>
									<tr>
										<th>Referrer provider address</th>
										<td>
											<p>Name: THE LIGHT HOUSE</p>
											<p>Address: 1 HIGH STREET, BASINGSTOKE, HAMPSHIRE</p>
											<p>Postcode: HA56 9AM</p>
										</td>
									</tr>
									<tr>
										<th>Referrer provider ODS code</th>
										<td>ABC12</td>
									</tr>
									<tr>
										<th>Provision date time</th>
										<td>2021-03-09T08:23:00Z00:00</td>
									</tr>
									<tr>
										<th>Patient initials</th>
										<td>JS</td>
									</tr>
									<tr>
										<th>Referrer case ID</th>
										<td>ABC1234567</td>
									</tr>
									<tr>
										<th>Referrer case reference</th>
										<td>ABC7654321</td>
									</tr>
									<tr>
										<th>Referrer name</th>
										<td>JONES, Mike</td>
									</tr>
									<tr>
										<th>Referrer role</th>
										<td>Call Handler</td>
									</tr>
									<tr>
										<th>Disposition</th>
										<td>Dx56 - refer to pharmacy</td>
									</tr>
									<tr>
										<th>Referral status</th>
										<td>Active</td>
									</tr>
									<tr>
										<th>Signposting reason</th>
										<td>Conjunctivitis</td>
									</tr>
									<tr>
										<th>Escalation reason</th>
										<td>Treatment required in 24 hours</td>
									</tr>
								</tbody>
							</table>
						</div>
					</text>
					<!--Reference to ReferralRequest resource as the source of information for this section-->
					<entry>
						<reference value="urn:uuid:5f96391c-9948-47c0-a1f1-70881dc62f9f"/>
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
											<p>Given Name: Jack</p>
											<p>Family Name: SMITH</p>
										</td>
									</tr>
									<tr>
										<th>Age</th>
										<td>14</td>
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
										<th>Patient postcode</th>
										<td>	HA17 4NK</td>
									</tr>
								</tbody>
							</table>
						</div>
					</text>
					<!--reference to further information carried in the patient resource-->
					<entry>
						<reference value="urn:uuid:9af701f7-5eb2-4402-bb3c-8ef8c8190082"/>
					</entry>
				</section>
				<!--Consent-->
				<section>
					<title value="Consent"/>
					<code>
						<coding>
							<system value="http://snomed.info/sct"/>
							<code value="61861000000100"/>
							<display value="Consent"/>
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
											<p>Family Name: RASTALL</p>
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
											<p>Name: ANDOVER Medical Centre</p>
											<p>Address:</p>
											<p>Address: 1 The Practice House, ANDOVER</p>
											<p>Post Code: HA21 7PA</p>
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
				<!--Attendance details-->
				<section>
					<title value="Attendance Details"/>
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
										<th>Followup Provider</th>
										<td>
											<p>ANDOVER PHARMACY (FQ123)</p>
											<p>2 SEASIDE COURT</p>
											<p>ANDOVER</p>
											<p>HAMPSHIRE</p>
											<p>HA45 6TP</p>
										</td>
									</tr>
									<tr>
										<th>Enrolled Practitioner</th>
										<td>
											<p>Name: JONES, Catherine (Ms)</p>
											<p>Role: Pharmacist</p>
											<p>Registration No: 2145879</p>
										</td>
									</tr>
									<tr>
										<th>Consultation Type</th>
										<td>Community Pharmacist Consultation Service</td>
									</tr>
									<tr>
										<th>Patient Accompanied</th>
										<td>Yes</td>
									</tr>
									<tr>
										<th>Relationship</th>
										<td>Mother</td>
									</tr>
									<tr>
										<th>Consent for 3rd Party</th>
										<td>Consent for third party obtained from patient</td>
									</tr>
								</tbody>
							</table>
						</div>
					</text>
					<!--Reference to Encounter resource as the source of information for this section-->
					<entry>
						<reference value="urn:uuid:d96ac9ee-208d-487b-8321-25eb895a3d31"/>
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
										<th>Medical history</th>
										<td>
											<p>Patient has history of panic attacks</p>
										</td>
									</tr>
									<tr>
										<th>Relevant information</th>
										<td>
											<p>Patient has recently recovered from common cold</p>
										</td>
									</tr>
									<tr>
										<th>Other details</th>
										<td>
											<p>No previous record of Conjunctivitis</p>
										</td>
									</tr>
									<tr>
										<th>Prescribed medications already taken</th>
										<td>
											<p>Takes St John's Wort Capsules Capsules (284mg) once a day</p>
										</td>
									</tr>
									<tr>
										<th>Over the counter remedies to date</th>
										<td>
											<p>Patient recently been taking paracetamol and ibuprofen</p>
										</td>
									</tr>
									<tr>
										<th>Associated symptoms</th>
										<td>
											<p>Patient has yellow discharge from left eye</p>
										</td>
									</tr>
									<tr>
										<th>Other symptoms</th>
										<td>
											<p>Patient also complaining of headache</p>
										</td>
									</tr>
								</tbody>
							</table>
						</div>
					</text>
				</section>
				<!--Clinical narrative-->
				<section>
					<title value="Clinical narrative"/>
					<code>
						<coding>
							<system value="http://snomed.info/sct"/>
							<code value="1077901000000108 "/>
							<display value="Clinical narrative"/>
						</coding>
					</code>
					<text>
						<status value="additional"/>
						<div xmlns="http://www.w3.org/1999/xhtml">
							<table width="100%">
								<tbody>
									<tr>
										<th>CKS Checked</th>
										<td>	No</td>
									</tr>
									<tr>
										<th>Red flags</th>
										<td>
											<p>Checked: Yes</p>
											<p>No red flags found</p>
										</td>
									</tr>
									<tr>
										<th>Consultation pharmacist notes</th>
										<td>	The patient was in slight distress when consultation started</td>
									</tr>
									<tr>
										<th>Consultation outcome</th>
										<td>	Patient treated for Conjunctivitis with Chloramphenicol eye drops (first dose administered in pharmacy). Advised over the counter paracetamol for headaches </td>
									</tr>
									<tr>
										<th>Consultation for onward referral</th>
										<td>	Yes</td>
									</tr>
									<tr>
										<th>GP notification form</th>
										<td>	Yes</td>
									</tr>
									<tr>
										<th>Incident</th>
										<td>	No</td>
									</tr>
									<tr>
										<th>Survey consent</th>
										<td>	No</td>
									</tr>
									<tr>
										<th>Patient Survey information: notification status</th>
										<td>	Not applicable</td>
									</tr>
								</tbody>
							</table>
						</div>
					</text>
				</section>
				<!--Presenting complaints or issues-->
				<section>
					<title value="Presenting complaints or issues"/>
					<code>
						<coding>
							<system value="http://snomed.info/sct"/>
							<code value="886891000000102"/>
							<display value="Presenting complaints or issues"/>
						</coding>
					</code>
					<text>
						<status value="additional"/>
						<div xmlns="http://www.w3.org/1999/xhtml">
							<table width="100%">
								<tbody>
									<tr>
										<th>Presenting complaint</th>
										<td>
											<p>Conjunctivitis (left eye)</p>
										</td>
									</tr>
									<tr>
										<th>Symptom duuration</th>
										<td>
											<p>3 days prior to contacting NHS111</p>
										</td>
									</tr>
								</tbody>
							</table>
						</div>
					</text>
					<!--Reference to Condition resource for coded complaint-->
					<entry>
						<reference value="urn:uuid:880b62cd-b2d6-43b0-b2c8-d6b6f04af496"/>
					</entry>
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
										<th>Supply appropriate</th>
										<td>Yes</td>
									</tr>
									<tr>
										<th>Medication supplied</th>
										<td>Chloramphenicol eye drops</td>
									</tr>
									<tr>
										<th>Medication quantity</th>
										<td/>
									</tr>
									<tr>
										<th>Medication dose</th>
										<td>Take 2 drops, 4 times a day as needed</td>
									</tr>
									<tr>
										<th>Medication supplied</th>
										<td>Paracetamol 500mg</td>
									</tr>
									<tr>
										<th>Medication cost</th>
										<td>0.45 GBP</td>
									</tr>
									<tr>
										<th>Medication quantity</th>
										<td>24 tablets</td>
									</tr>
									<tr>
										<th>Medication dose</th>
										<td>Take 2, 4 times a day as needed</td>
									</tr>
									<tr>
										<th>Advice provided with medication</th>
										<td>Do not exceed recommended dose of Paracetamol</td>
									</tr>
									<tr>
										<th>Advice provided only</th>
										<td>No</td>
									</tr>
									<tr>
										<th>Additional instructions</th>
										<td>If symptoms persist for more than 3 days, book a GP appointment.</td>
									</tr>
									<tr>
										<th>Person advised</th>
										<td>Patient: SMITH Jack</td>
									</tr>
									<tr>
										<th>Symptom advice given</th>
										<td>Avoid hand contact with infested eye. Clean eye at least 2 times a day.</td>
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
				<!--Observations-->
				<section>
					<title value="Observations"/>
					<code>
						<coding>
							<system value="http://snomed.info/sct"/>
							<code value="1102421000000108"/>
							<display value="Observations"/>
						</coding>
					</code>
					<text>
						<status value="generated"/>
						<div xmlns="http://www.w3.org/1999/xhtml">
							<table width="100%">
								<tbody>
									<tr>
										<th>Observation</th>
										<th>Date Performed</th>
										<th>Reading</th>
									</tr>
									<tr>
										<td>Blood pressure</td>
										<td>2021-03-09</td>
										<td>136/93</td>
									</tr>
									<tr>
										<td>Pulse rate</td>
										<td>2021-03-09</td>
										<td>82 bpm</td>
									</tr>
								</tbody>
							</table>
						</div>
					</text>
					<!--link to BP-->
					<entry>
						<reference value="urn:uuid:f08fb19d-4e80-4394-a56a-01794414562d"/>
					</entry>
					<!--link to pulse rate-->
					<entry>
						<reference value="urn:uuid:fe15bbb9-db3f-4269-a8e2-bb034445b065"/>
					</entry>
				</section>
			</Composition>
		</resource>
	</entry>
	<!--Referral Request-->
	<entry>
		<fullUrl value="urn:uuid:5f96391c-9948-47c0-a1f1-70881dc62f9f"/>
		<resource>
			<!--Encounter resource providing context for the pharmacy visit-->
			<ReferralRequest>
				<id value="5f96391c-9948-47c0-a1f1-70881dc62f9f"/>
				<meta>
					<profile value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-ReferralRequest-1"/>
				</meta>
				<identifier>
					<system value="https://ABC12/CaseID"/>
					<value value="ABC1234567"/>
				</identifier>
				<identifier>
					<system value="https://ABC12/CaseRef"/>
					<value value="ABC7654321"/>
				</identifier>
				<status value="completed"/>
				<intent value="proposal"/>
				<priority value="routine"/>
				<subject>
					<reference value="urn:uuid:9af701f7-5eb2-4402-bb3c-8ef8c8190082"/>
					<display value="SMITH, Jack"/>
				</subject>
				<authoredOn value="2021-03-09T08:23:00+00:00"/>
				<requester>
					<agent>
						<reference value="urn:uuid:98bef14c-e492-4858-8f42-d850ea1b2f49"/>
						<display value="Jones, Mike"/>
					</agent>
					<onBehalfOf>
						<reference value="urn:uuid:9fd86119-3502-47a9-a7a9-3088c4ee3527"/>
						<display value="HAMPSHIRE NHS 111 CALL CENTRE"/>
					</onBehalfOf>
				</requester>
				<reasonCode>
					<coding>
						<code value="Dx56"/>
						<system value="https://ABC12/Dx"/>
						<display value="Refer to pharmacy"/>
					</coding>
				</reasonCode>
				<reasonCode>
					<coding>
						<code value="9826008"/>
						<system value="http://snomed.info/sct"/>
						<display value="Conjunctivitis "/>
					</coding>
				</reasonCode>
			</ReferralRequest>
		</resource>
	</entry>
	<!--111 call operator-->
	<entry>
		<fullUrl value="urn:uuid:98bef14c-e492-4858-8f42-d850ea1b2f49"/>
		<resource>
			<PractitionerRole>
				<id value="98bef14c-e492-4858-8f42-d850ea1b2f49"/>
				<meta>
					<profile value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-PractitionerRole-1"/>
				</meta>
				<practitioner>
					<reference value="urn:uuid:e683f36a-864d-4637-b9ca-1644a1377347"/>
				</practitioner>
				<code>
					<coding>
						<code value="R1690"/>
						<system value="https://fhir.hl7.org.uk/STU3/ValueSet/CareConnect-SDSJobRoleName-1"/>
						<display value="Call Operator"/>
					</coding>
				</code>
			</PractitionerRole>
		</resource>
	</entry>
	<!--111 call operator name-->
	<entry>
		<fullUrl value="urn:uuid:e683f36a-864d-4637-b9ca-1644a1377347"/>
		<resource>
			<Practitioner>
				<id value="e683f36a-864d-4637-b9ca-1644a1377347"/>
				<meta>
					<profile value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1"/>
				</meta>
				<name>
					<family value="Jones"/>
					<given value="Mike"/>
				</name>
			</Practitioner>
		</resource>
	</entry>
	<!--111 Org-->
	<entry>
		<fullUrl value="urn:uuid:9fd86119-3502-47a9-a7a9-3088c4ee3527"/>
		<resource>
			<Organization>
				<id value="9fd86119-3502-47a9-a7a9-3088c4ee3527"/>
				<meta>
					<profile value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1"/>
				</meta>
				<identifier>
					<system value="https://fhir.nhs.uk/Id/ods-organization-code"/>
					<value value="ABC12"/>
				</identifier>
				<name value="HAMPSHIRE NHS 111 CALL CENTRE"/>
				<address>
					<line value="1 HIGH STREET"/>
					<line value="BASINGSTOKE"/>
					<line value="HAMPSHIRE"/>
					<postalCode value="HA56 9AM"/>
				</address>
			</Organization>
		</resource>
	</entry>
	<!--Patient-->
	<entry>
		<fullUrl value="urn:uuid:9af701f7-5eb2-4402-bb3c-8ef8c8190082"/>
		<resource>
			<Patient>
				<id value="9af701f7-5eb2-4402-bb3c-8ef8c8190082"/>
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
					<family value="SMITH"/>
					<given value="Jack"/>
				</name>
				<gender value="male"/>
				<birthDate value="2006-02-04"/>
				<address>
					<postalCode value="HA17 4NK"/>
				</address>
				<managingOrganization>
					<reference value="urn:uuid:e46d86bf-1720-4c55-878f-a034d8349bbd"/>
				</managingOrganization>
			</Patient>
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
				<name value="ANDOVER Medical Centre"/>
				<address>
					<line value="1 The Practice House"/>
					<city value="ANDOVER"/>
					<postalCode value="HA21 7PA"/>
				</address>
			</Organization>
		</resource>
	</entry>
	<!--Pharmacy Encounter-->
	<entry>
		<fullUrl value="urn:uuid:d96ac9ee-208d-487b-8321-25eb895a3d31"/>
		<resource>
			<!--Encounter resource providing context for the pharmacy visit-->
			<Encounter>
				<id value="d96ac9ee-208d-487b-8321-25eb895a3d31"/>
				<meta>
					<profile value="https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Encounter-1"/>
				</meta>
				<status value="finished"/>
				<subject>
					<reference value="urn:uuid:9af701f7-5eb2-4402-bb3c-8ef8c8190082"/>
					<display value="SMITH, Jack"/>
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
						<reference value="urn:uuid:185e4d61-be11-4bd9-81ab-07a9e489566d"/>
						<display value="JONES Catherine (Ms)"/>
					</individual>
				</participant>
				<period>
					<start value="2021-03-09T08:59:00+00:00"/>
				</period>
				<serviceProvider>
					<reference value="urn:uuid:f038775b-64a6-4afa-8de3-ae9266b11408"/>
					<display value="Overtown Pharmacy"/>
				</serviceProvider>
			</Encounter>
		</resource>
	</entry>
	<!--Pharmacy associated with the encounter. -->
	<entry>
		<fullUrl value="urn:uuid:f038775b-64a6-4afa-8de3-ae9266b11408"/>
		<resource>
			<Organization>
				<id value="f038775b-64a6-4afa-8de3-ae9266b11408"/>
				<meta>
					<profile value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1"/>
				</meta>
				<identifier>
					<system value="https://fhir.nhs.uk/Id/ods-organization-code"/>
					<value value="FQ123"/>
				</identifier>
				<name value="ANDOVER PHAMACY"/>
				<telecom>
					<system value="phone"/>
					<value value="01534875516"/>
				</telecom>
				<address>
					<line value="2 SEASIDE COURT"/>
					<line value="ANDOVER"/>
					<line value="HAMPSHIRE"/>
					<postalCode value="HA45 6TP"/>
				</address>
			</Organization>
		</resource>
	</entry>
	<!--Pharmacist associated with the encounter. -->
	<entry>
		<fullUrl value="urn:uuid:185e4d61-be11-4bd9-81ab-07a9e489566d"/>
		<resource>
			<Practitioner>
				<id value="185e4d61-be11-4bd9-81ab-07a9e489566d"/>
				<meta>
					<profile value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1"/>
				</meta>
				<identifier>
					<system value="https://fhir.hl7.org.uk/Id/gphc-number"/>
					<value value="2145879"/>
				</identifier>
				<name>
					<family value="JONES"/>
					<given value="Catherine"/>
					<prefix value="Ms"/>
				</name>
				<telecom>
					<system value="phone"/>
					<value value="0113895123"/>
					<use value="work"/>
				</telecom>
				<gender value="female"/>
			</Practitioner>
		</resource>
	</entry>
	<!--Presenting Condition-->
	<entry>
		<fullUrl value="urn:uuid:880b62cd-b2d6-43b0-b2c8-d6b6f04af496"/>
		<resource>
			<Condition>
				<meta>
					<profile value="https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Condition-1"/>
				</meta>
				<clinicalStatus value="active"/>
				<code>
					<coding>
						<code value="9826008"/>
						<system value="http://snomed.info/sct"/>
						<display value="Conjunctivitis"/>
					</coding>
				</code>
				<bodySite>
					<coding>
						<code value="8966001"/>
						<system value="http://snomed.info/sct"/>
						<display value="Left eye"/>
					</coding>
				</bodySite>
				<subject>
					<reference value="urn:uuid:9af701f7-5eb2-4402-bb3c-8ef8c8190082"/>
				</subject>
				<onsetString value="3 days prior to being seen"/>
			</Condition>
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
					<reference value="urn:uuid:9af701f7-5eb2-4402-bb3c-8ef8c8190082"/>
					<display value="SMITH, William (Mr)"/>
				</subject>
				<encounter>
					<reference value="urn:uuid:d96ac9ee-208d-487b-8321-25eb895a3d31"/>
				</encounter>
				<date value="2021-03-09"/>
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
					<display value="Chloramphenicol 5 mg/mL eye drops"/>
				</medicationReference>
				<subject>
					<reference value="urn:uuid:9af701f7-5eb2-4402-bb3c-8ef8c8190082"/>
					<display value="SMITH, Jack"/>
				</subject>
				<context>
					<reference value="urn:uuid:d96ac9ee-208d-487b-8321-25eb895a3d31"/>
				</context>
				<performer>
					<actor>
						<reference value="urn:uuid:185e4d61-be11-4bd9-81ab-07a9e489566d"/>
					</actor>
					<onBehalfOf>
						<reference value="urn:uuid:f038775b-64a6-4afa-8de3-ae9266b11408"/>
					</onBehalfOf>
				</performer>
				<quantity>
					<extension url="https://fhir.hl7.org.uk/STU3/StructureDefinition/Extension-CareConnect-MedicationQuantityText-1">
						<valueString value="20 ml"/>
					</extension>
					<value value="1"/>
					<unit value="unit"/>
				</quantity>
				<whenHandedOver value="2021-03-09"/>
				<dosageInstruction>
					<text value="Take 2 drops, 4 times a day"/>
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
					<display value="Paracetamol 500 mg oral tablet"/>
				</medicationReference>
				<subject>
					<reference value="urn:uuid:9af701f7-5eb2-4402-bb3c-8ef8c8190082"/>
					<display value="SMITH, Jack"/>
				</subject>
				<context>
					<reference value="urn:uuid:d96ac9ee-208d-487b-8321-25eb895a3d31"/>
				</context>
				<performer>
					<actor>
						<reference value="urn:uuid:185e4d61-be11-4bd9-81ab-07a9e489566d"/>
					</actor>
					<onBehalfOf>
						<reference value="urn:uuid:f038775b-64a6-4afa-8de3-ae9266b11408"/>
					</onBehalfOf>
				</performer>
				<quantity>
					<value value="24"/>
					<unit value="tablet"/>
				</quantity>
				<whenHandedOver value="2021-03-09"/>
				<dosageInstruction>
					<text value="Take 2 tables, 4 times a day"/>
				</dosageInstruction>
			</MedicationDispense>
		</resource>
	</entry>
	<!--Medication prescribed (Chloramphenicol)-->
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
						<code value="330286001"/>
						<display value="Chloramphenicol 5 mg/mL eye drops"/>
					</coding>
				</code>
				<status value="active"/>
			</Medication>
		</resource>
	</entry>
	<!--Medication prescribed (paracetamol)-->
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
						<code value="322236009"/>
						<display value="Paracetamol 500 mg oral tablet"/>
					</coding>
				</code>
				<status value="active"/>
			</Medication>
		</resource>
	</entry>
	<!--BP Observation-->
	<entry>
		<fullUrl value="urn:uuid:f08fb19d-4e80-4394-a56a-01794414562d"/>
		<resource>
			<Observation>
				<id value="f08fb19d-4e80-4394-a56a-01794414562d"/>
				<meta>
					<profile value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-BloodPressure-Observation-1"/>
				</meta>
				<!--a fixed value for status-->
				<status value="final"/>
				<!--fixed value for category-->
				<category>
					<coding>
						<system value="http://hl7.org/fhir/observation-category"/>
						<code value="vital-signs"/>
						<display value="Vital Signs"/>
					</coding>
				</category>
				<!--fixed values for code-->
				<code>
					<coding>
						<system value="http://loinc.org"/>
						<code value="85354-9"/>
						<display value="Blood pressure panel with all children optional"/>
					</coding>
					<coding>
						<system value="http://snomed.info/sct"/>
						<code value="75367002"/>
						<display value="Blood pressure"/>
					</coding>
				</code>
				<!--a link to the Patient-->
				<subject>
					<reference value="urn:uuid:9af701f7-5eb2-4402-bb3c-8ef8c8190082"/>
				</subject>
				<!--the date and time of the reading-->
				<effectiveDateTime value="2021-03-09T09:01:59+00:00"/>
				<!--example of a link to a Practitioner-->
				<performer>
					<reference value="urn:uuid:185e4d61-be11-4bd9-81ab-07a9e489566d"/>
				</performer>
				<!--body site of reading-->
				<bodySite>
					<coding>
						<system value="http://snomed.info/sct"/>
						<code value="368209003"/>
						<display value="Right arm"/>
					</coding>
				</bodySite>
				<!--systolic-->
				<component>
					<!--fixed values for code-->
					<code>
						<coding>
							<system value="http://loinc.org"/>
							<code value="8480-6"/>
							<display value="Systolic blood pressure"/>
						</coding>
						<coding>
							<system value="http://snomed.info/sct"/>
							<code value="72313002"/>
							<display value="Systolic blood pressure"/>
						</coding>
					</code>
					<!--the systolic reading-->
					<valueQuantity>
						<value value="136"/>
						<unit value="mmHg"/>
						<system value="http://unitsofmeasure.org"/>
					</valueQuantity>
				</component>
				<!--diastolic-->
				<component>
					<!--fixed values for code-->
					<code>
						<coding>
							<system value="http://loinc.org"/>
							<code value="8462-4"/>
							<display value="Diastolic blood pressure"/>
						</coding>
						<coding>
							<system value="http://snomed.info/sct"/>
							<code value="1091811000000102"/>
							<display value="Diastolic arterial pressure"/>
						</coding>
					</code>
					<!--the diastolic reading-->
					<valueQuantity>
						<value value="93"/>
						<unit value="mmHg"/>
						<system value="http://unitsofmeasure.org"/>
					</valueQuantity>
				</component>
			</Observation>
		</resource>
	</entry>
	<!--Pulse rate Observation-->
	<entry>
		<fullUrl value="urn:uuid:fe15bbb9-db3f-4269-a8e2-bb034445b065"/>
		<resource>
			<Observation xmlns="http://hl7.org/fhir">
				<id value="fe15bbb9-db3f-4269-a8e2-bb034445b065"/>
				<meta>
					<!--claims conformance to CareConnect-HeartRate-Observation-1-->
					<profile value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-HeartRate-Observation-1"/>
				</meta>
				<!--fixed value for status-->
				<status value="final"/>
				<!--fixed value for category-->
				<category>
					<coding>
						<system value="http://hl7.org/fhir/observation-category"/>
						<code value="vital-signs"/>
						<display value="Vital Signs"/>
					</coding>
				</category>
				<!--fixed values for code, plus an extra SNOMED code for pulse rate-->
				<code>
					<coding>
						<system value="http://loinc.org"/>
						<code value="8867-4"/>
						<display value="Heart rate"/>
					</coding>
					<coding>
						<system value="http://snomed.info/sct"/>
						<code value="364075005"/>
						<display value="Heart rate"/>
					</coding>
				</code>
				<!--link to patient-->
				<subject>
					<reference value="urn:uuid:9af701f7-5eb2-4402-bb3c-8ef8c8190082"/>
				</subject>
				<!--the date and time of the reading-->
				<effectiveDateTime value="2018-10-04T14:17:59+01:00"/>
				<!--example of a link to a Practitioner-->
				<performer>
					<reference value="urn:uuid:185e4d61-be11-4bd9-81ab-07a9e489566d"/>
				</performer>
				<!--the pulse rate reading-->
				<valueQuantity>
					<value value="82"/>
					<unit value="bpm"/>
					<system value="http://unitsofmeasure.org"/>
				</valueQuantity>
			</Observation>
		</resource>
	</entry>
</Bundle>
<!--</xml>-->
```
## Example Instance of Scenario - ITK Wrapper ##

{% include note.html content="These examples have not been clinically assured against Digital Medicines use cases.<br/>Examples are illustrative only." %}

```
<!--<xml>-->
<!-- This xml example is for illustrative purposes only and has not been clinically verified. -->
<Bundle xmlns="http://hl7.org/fhir">
	<id value="716f0081-2794-4662-af76-506a9f9f6914"/>
	<meta>
		<profile value="https://fhir.nhs.uk/STU3/StructureDefinition/ITK-Message-Bundle-1"/>
	</meta>
	<identifier>
		<value value="716f0081-2794-4662-af76-506a9f9f6914"/>
	</identifier>
	<type value="message"/>
	<entry>
		<fullUrl value="urn:uuid:c8ecc1ed-ed39-457e-9571-cd9911d26f84"/>
		<resource>
			<MessageHeader>
				<id value="c8ecc1ed-ed39-457e-9571-cd9911d26f84"/>
				<meta>
					<profile value="https://fhir.nhs.uk/STU3/StructureDefinition/ITK-MessageHeader-2"/>
				</meta>
				<extension url="https://fhir.nhs.uk/STU3/StructureDefinition/Extension-ITK-MessageHandling-2">
					<!-- The value of this handling specification is dependant on the response pattern. -->
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
							<reference value="https://fhir.nhs.uk/STU3/MessageDefinition/ITK-DM-MIRC-MessageDefinition-1"/>
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
					<code value="ITK013D"/>
					<display value="ITK Digital Medicine Minor Illness Referral Consultation Document"/>
				</event>
				<receiver>
					<reference value="urn:uuid:ede9fc58-2d81-11eb-adc1-0242ac120002"/>
				</receiver>
				<sender>
					<reference value="urn:uuid:61cf13e6-9972-4e9a-a7ee-54c96f066842"/>
				</sender>
				<timestamp value="2020-12-10T10:10:16+00:00"/>
				<source>
					<endpoint value="NOROT003"/>
				</source>
				<focus>
					<reference value="urn:uuid:ede9fe38-2d81-11eb-adc1-0242ac120002"/>
				</focus>
			</MessageHeader>
		</resource>
	</entry>
	<!-- Reveiver Organisation -->
	<entry>
		<fullUrl value="urn:uuid:ede9fd5c-2d81-11eb-adc1-0242ac120002"/>
		<resource>
			<Organization>
				<id value="ede9fd5c-2d81-11eb-adc1-0242ac120002"/>
				<meta>
					<profile value="https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Header-Organization-1"/>
				</meta>
				<identifier>
					<system value="https://fhir.nhs.uk/Id/ods-organization-code"/>
					<value value="A8797979"/>
				</identifier>
			</Organization>
		</resource>
	</entry>
	<!-- Sender Organization -->
	<entry>
		<fullUrl value="urn:uuid:61cf13e6-9972-4e9a-a7ee-54c96f066842"/>
		<resource>
			<Organization>
				<id value="61cf13e6-9972-4e9a-a7ee-54c96f066842"/>
				<meta>
					<profile value="https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Header-Organization-1"/>
				</meta>
				<identifier>
					<system value="https://fhir.nhs.uk/Id/ods-organization-code"/>
					<value value="FQ123"/>
				</identifier>
			</Organization>
		</resource>
	</entry>
	<entry>
		<fullUrl value="urn:uuid:2fe7a417-20f8-4b47-a869-6a3dc72c9ff4"/>
		<resource>
			<!--This xml example is for illustrative purposes only and has not been clinically verified.-->
			<Bundle xmlns="http://hl7.org/fhir">
				<id value="2fe7a417-20f8-4b47-a869-6a3dc72c9ff4"/>
				<meta>
					<lastUpdated value="2021-03-09T10:00:00+00:00"/>
					<profile value="https://fhir.nhs.uk/STU3/StructureDefinition/ITK-Document-Bundle-1"/>
				</meta>
				<identifier>
					<system value="https://tools.ietf.org/html/rfc4122"/>
					<value value="d6e3638c-80f1-11eb-8dcd-0242ac130003"/>
				</identifier>
				<type value="document"/>
				<!--Minor Illness Referral Consultation Document-->
				<entry>
					<fullUrl value="urn:uuid:19bc2bf3-abd0-4da8-b9f1-60e36554489b"/>
					<resource>
						<!--A resource carrying a set of healthcare-related information about the patient-->
						<Composition xmlns="http://hl7.org/fhir">
							<id value="19bc2bf3-abd0-4da8-b9f1-60e36554489b"/>
							<meta>
								<profile value="https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-DM-DMIRS-Composition-1"/>
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
								<value value="4dd3b461-83be-41e4-99eb-0d8d04fb5508"/>
							</identifier>
							<!--The workflow/clinical status of this composition. The status is a marker for the clinical standing of the document.-->
							<status value="final"/>
							<type>
								<!--Digital Medicines document type-->
								<coding>
									<system value="http://snomed.info/sct"/>
									<code value="1321521000000101"/>
									<display value="Supply of medication for minor illness by community pharmacy"/>
								</coding>
							</type>
							<!--Reference to the patient subject of the Composition-->
							<subject>
								<reference value="urn:uuid:9af701f7-5eb2-4402-bb3c-8ef8c8190082"/>
							</subject>
							<!--Reference to the clinical encounter or type of care this documentation is associated with.-->
							<encounter>
								<reference value="urn:uuid:d96ac9ee-208d-487b-8321-25eb895a3d31"/>
							</encounter>
							<!--The composition editing time, when the composition was last logically changed by the author.-->
							<date value="2021-03-09T09:34:00+00:00"/>
							<!--Identifies who is responsible for the information in the composition, 
not necessarily who typed it in-->
							<author>
								<reference value="urn:uuid:185e4d61-be11-4bd9-81ab-07a9e489566d"/>
							</author>
							<title value="ANDOVER PHARMACY Community Pharmacist Minor Illness Referral Consultation Service"/>
							<!--Identifies the organization responsible for ongoing maintenance of and access 
to the composition/document information.-->
							<custodian>
								<reference value="urn:uuid:f038775b-64a6-4afa-8de3-ae9266b11408"/>
							</custodian>
							<!--Referrer details-->
							<section>
								<title value="Referrer Details"/>
								<code>
									<coding>
										<system value="http://snomed.info/sct"/>
										<code value="1052891000000108"/>
										<display value="Referrer details"/>
									</coding>
								</code>
								<text>
									<status value="additional"/>
									<div xmlns="http://www.w3.org/1999/xhtml">
										<table width="100%">
											<tbody>
												<tr>
													<th>Referral record</th>
													<td>Active</td>
												</tr>
												<tr>
													<th>Referrer provider name</th>
													<td>HAMPSHIRE NHS 111 CALL CENTRE</td>
												</tr>
												<tr>
													<th>Referrer provider address</th>
													<td>
														<p>Name: THE LIGHT HOUSE</p>
														<p>Address: 1 HIGH STREET, BASINGSTOKE, HAMPSHIRE</p>
														<p>Postcode: HA56 9AM</p>
													</td>
												</tr>
												<tr>
													<th>Referrer provider ODS code</th>
													<td>ABC12</td>
												</tr>
												<tr>
													<th>Provision date time</th>
													<td>2021-03-09T08:23:00Z00:00</td>
												</tr>
												<tr>
													<th>Patient initials</th>
													<td>JS</td>
												</tr>
												<tr>
													<th>Referrer case ID</th>
													<td>ABC1234567</td>
												</tr>
												<tr>
													<th>Referrer case reference</th>
													<td>ABC7654321</td>
												</tr>
												<tr>
													<th>Referrer name</th>
													<td>JONES, Mike</td>
												</tr>
												<tr>
													<th>Referrer role</th>
													<td>Call Handler</td>
												</tr>
												<tr>
													<th>Disposition</th>
													<td>Dx56 - refer to pharmacy</td>
												</tr>
												<tr>
													<th>Referral status</th>
													<td>Active</td>
												</tr>
												<tr>
													<th>Signposting reason</th>
													<td>Conjunctivitis</td>
												</tr>
												<tr>
													<th>Escalation reason</th>
													<td>Treatment required in 24 hours</td>
												</tr>
											</tbody>
										</table>
									</div>
								</text>
								<!--Reference to ReferralRequest resource as the source of information for this section-->
								<entry>
									<reference value="urn:uuid:5f96391c-9948-47c0-a1f1-70881dc62f9f"/>
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
														<p>Given Name: Jack</p>
														<p>Family Name: SMITH</p>
													</td>
												</tr>
												<tr>
													<th>Age</th>
													<td>14</td>
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
													<th>Patient postcode</th>
													<td>	HA17 4NK</td>
												</tr>
											</tbody>
										</table>
									</div>
								</text>
								<!--reference to further information carried in the patient resource-->
								<entry>
									<reference value="urn:uuid:9af701f7-5eb2-4402-bb3c-8ef8c8190082"/>
								</entry>
							</section>
							<!--Consent-->
							<section>
								<title value="Consent"/>
								<code>
									<coding>
										<system value="http://snomed.info/sct"/>
										<code value="61861000000100"/>
										<display value="Consent"/>
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
														<p>Family Name: RASTALL</p>
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
														<p>Name: ANDOVER Medical Centre</p>
														<p>Address:</p>
														<p>Address: 1 The Practice House, ANDOVER</p>
														<p>Post Code: HA21 7PA</p>
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
							<!--Attendance details-->
							<section>
								<title value="Attendance Details"/>
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
													<th>Followup Provider</th>
													<td>
														<p>ANDOVER PHARMACY (FQ123)</p>
														<p>2 SEASIDE COURT</p>
														<p>ANDOVER</p>
														<p>HAMPSHIRE</p>
														<p>HA45 6TP</p>
													</td>
												</tr>
												<tr>
													<th>Enrolled Practitioner</th>
													<td>
														<p>Name: JONES, Catherine (Ms)</p>
														<p>Role: Pharmacist</p>
														<p>Registration No: 2145879</p>
													</td>
												</tr>
												<tr>
													<th>Consultation Type</th>
													<td>Community Pharmacist Consultation Service</td>
												</tr>
												<tr>
													<th>Patient Accompanied</th>
													<td>Yes</td>
												</tr>
												<tr>
													<th>Relationship</th>
													<td>Mother</td>
												</tr>
												<tr>
													<th>Consent for 3rd Party</th>
													<td>Consent for third party obtained from patient</td>
												</tr>
											</tbody>
										</table>
									</div>
								</text>
								<!--Reference to Encounter resource as the source of information for this section-->
								<entry>
									<reference value="urn:uuid:d96ac9ee-208d-487b-8321-25eb895a3d31"/>
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
													<th>Medical history</th>
													<td>
														<p>Patient has history of panic attacks</p>
													</td>
												</tr>
												<tr>
													<th>Relevant information</th>
													<td>
														<p>Patient has recently recovered from common cold</p>
													</td>
												</tr>
												<tr>
													<th>Other details</th>
													<td>
														<p>No previous record of Conjunctivitis</p>
													</td>
												</tr>
												<tr>
													<th>Prescribed medications already taken</th>
													<td>
														<p>Takes St John's Wort Capsules Capsules (284mg) once a day</p>
													</td>
												</tr>
												<tr>
													<th>Over the counter remedies to date</th>
													<td>
														<p>Patient recently been taking paracetamol and ibuprofen</p>
													</td>
												</tr>
												<tr>
													<th>Associated symptoms</th>
													<td>
														<p>Patient has yellow discharge from left eye</p>
													</td>
												</tr>
												<tr>
													<th>Other symptoms</th>
													<td>
														<p>Patient also complaining of headache</p>
													</td>
												</tr>
											</tbody>
										</table>
									</div>
								</text>
							</section>
							<!--Clinical narrative-->
							<section>
								<title value="Clinical narrative"/>
								<code>
									<coding>
										<system value="http://snomed.info/sct"/>
										<code value="1077901000000108 "/>
										<display value="Clinical narrative"/>
									</coding>
								</code>
								<text>
									<status value="additional"/>
									<div xmlns="http://www.w3.org/1999/xhtml">
										<table width="100%">
											<tbody>
												<tr>
													<th>CKS Checked</th>
													<td>	No</td>
												</tr>
												<tr>
													<th>Red flags</th>
													<td>
														<p>Checked: Yes</p>
														<p>No red flags found</p>
													</td>
												</tr>
												<tr>
													<th>Consultation pharmacist notes</th>
													<td>	The patient was in slight distress when consultation started</td>
												</tr>
												<tr>
													<th>Consultation outcome</th>
													<td>	Patient treated for Conjunctivitis with Chloramphenicol eye drops (first dose administered in pharmacy). Advised over the counter paracetamol for headaches </td>
												</tr>
												<tr>
													<th>Consultation for onward referral</th>
													<td>	Yes</td>
												</tr>
												<tr>
													<th>GP notification form</th>
													<td>	Yes</td>
												</tr>
												<tr>
													<th>Incident</th>
													<td>	No</td>
												</tr>
												<tr>
													<th>Survey consent</th>
													<td>	No</td>
												</tr>
												<tr>
													<th>Patient Survey information: notification status</th>
													<td>	Not applicable</td>
												</tr>
											</tbody>
										</table>
									</div>
								</text>
							</section>
							<!--Presenting complaints or issues-->
							<section>
								<title value="Presenting complaints or issues"/>
								<code>
									<coding>
										<system value="http://snomed.info/sct"/>
										<code value="886891000000102"/>
										<display value="Presenting complaints or issues"/>
									</coding>
								</code>
								<text>
									<status value="additional"/>
									<div xmlns="http://www.w3.org/1999/xhtml">
										<table width="100%">
											<tbody>
												<tr>
													<th>Presenting complaint</th>
													<td>
														<p>Conjunctivitis (left eye)</p>
													</td>
												</tr>
												<tr>
													<th>Symptom duuration</th>
													<td>
														<p>3 days prior to contacting NHS111</p>
													</td>
												</tr>
											</tbody>
										</table>
									</div>
								</text>
								<!--Reference to Condition resource for coded complaint-->
								<entry>
									<reference value="urn:uuid:880b62cd-b2d6-43b0-b2c8-d6b6f04af496"/>
								</entry>
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
													<th>Supply appropriate</th>
													<td>Yes</td>
												</tr>
												<tr>
													<th>Medication supplied</th>
													<td>Chloramphenicol eye drops</td>
												</tr>
												<tr>
													<th>Medication quantity</th>
													<td/>
												</tr>
												<tr>
													<th>Medication dose</th>
													<td>Take 2 drops, 4 times a day as needed</td>
												</tr>
												<tr>
													<th>Medication supplied</th>
													<td>Paracetamol 500mg</td>
												</tr>
												<tr>
													<th>Medication cost</th>
													<td>0.45 GBP</td>
												</tr>
												<tr>
													<th>Medication quantity</th>
													<td>24 tablets</td>
												</tr>
												<tr>
													<th>Medication dose</th>
													<td>Take 2, 4 times a day as needed</td>
												</tr>
												<tr>
													<th>Advice provided with medication</th>
													<td>Do not exceed recommended dose of Paracetamol</td>
												</tr>
												<tr>
													<th>Advice provided only</th>
													<td>No</td>
												</tr>
												<tr>
													<th>Additional instructions</th>
													<td>If symptoms persist for more than 3 days, book a GP appointment.</td>
												</tr>
												<tr>
													<th>Person advised</th>
													<td>Patient: SMITH Jack</td>
												</tr>
												<tr>
													<th>Symptom advice given</th>
													<td>Avoid hand contact with infested eye. Clean eye at least 2 times a day.</td>
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
							<!--Observations-->
							<section>
								<title value="Observations"/>
								<code>
									<coding>
										<system value="http://snomed.info/sct"/>
										<code value="1102421000000108"/>
										<display value="Observations"/>
									</coding>
								</code>
								<text>
									<status value="generated"/>
									<div xmlns="http://www.w3.org/1999/xhtml">
										<table width="100%">
											<tbody>
												<tr>
													<th>Observation</th>
													<th>Date Performed</th>
													<th>Reading</th>
												</tr>
												<tr>
													<td>Blood pressure</td>
													<td>2021-03-09</td>
													<td>136/93</td>
												</tr>
												<tr>
													<td>Pulse rate</td>
													<td>2021-03-09</td>
													<td>82 bpm</td>
												</tr>
											</tbody>
										</table>
									</div>
								</text>
								<!--link to BP-->
								<entry>
									<reference value="urn:uuid:f08fb19d-4e80-4394-a56a-01794414562d"/>
								</entry>
								<!--link to pulse rate-->
								<entry>
									<reference value="urn:uuid:fe15bbb9-db3f-4269-a8e2-bb034445b065"/>
								</entry>
							</section>
						</Composition>
					</resource>
				</entry>
				<!--Referral Request-->
				<entry>
					<fullUrl value="urn:uuid:5f96391c-9948-47c0-a1f1-70881dc62f9f"/>
					<resource>
						<!--Encounter resource providing context for the pharmacy visit-->
						<ReferralRequest>
							<id value="5f96391c-9948-47c0-a1f1-70881dc62f9f"/>
							<meta>
								<profile value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-ReferralRequest-1"/>
							</meta>
							<identifier>
								<system value="https://ABC12/CaseID"/>
								<value value="ABC1234567"/>
							</identifier>
							<identifier>
								<system value="https://ABC12/CaseRef"/>
								<value value="ABC7654321"/>
							</identifier>
							<status value="completed"/>
							<intent value="proposal"/>
							<priority value="routine"/>
							<subject>
								<reference value="urn:uuid:9af701f7-5eb2-4402-bb3c-8ef8c8190082"/>
								<display value="SMITH, Jack"/>
							</subject>
							<authoredOn value="2021-03-09T08:23:00+00:00"/>
							<requester>
								<agent>
									<reference value="urn:uuid:98bef14c-e492-4858-8f42-d850ea1b2f49"/>
									<display value="Jones, Mike"/>
								</agent>
								<onBehalfOf>
									<reference value="urn:uuid:9fd86119-3502-47a9-a7a9-3088c4ee3527"/>
									<display value="HAMPSHIRE NHS 111 CALL CENTRE"/>
								</onBehalfOf>
							</requester>
							<reasonCode>
								<coding>
									<code value="Dx56"/>
									<system value="https://ABC12/Dx"/>
									<display value="Refer to pharmacy"/>
								</coding>
							</reasonCode>
							<reasonCode>
								<coding>
									<code value="9826008"/>
									<system value="http://snomed.info/sct"/>
									<display value="Conjunctivitis "/>
								</coding>
							</reasonCode>
						</ReferralRequest>
					</resource>
				</entry>
				<!--111 call operator-->
				<entry>
					<fullUrl value="urn:uuid:98bef14c-e492-4858-8f42-d850ea1b2f49"/>
					<resource>
						<PractitionerRole>
							<id value="98bef14c-e492-4858-8f42-d850ea1b2f49"/>
							<meta>
								<profile value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-PractitionerRole-1"/>
							</meta>
							<practitioner>
								<reference value="urn:uuid:e683f36a-864d-4637-b9ca-1644a1377347"/>
							</practitioner>
							<code>
								<coding>
									<code value="R1690"/>
									<system value="https://fhir.hl7.org.uk/STU3/ValueSet/CareConnect-SDSJobRoleName-1"/>
									<display value="Call Operator"/>
								</coding>
							</code>
						</PractitionerRole>
					</resource>
				</entry>
				<!--111 call operator name-->
				<entry>
					<fullUrl value="urn:uuid:e683f36a-864d-4637-b9ca-1644a1377347"/>
					<resource>
						<Practitioner>
							<id value="e683f36a-864d-4637-b9ca-1644a1377347"/>
							<meta>
								<profile value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1"/>
							</meta>
							<name>
								<family value="Jones"/>
								<given value="Mike"/>
							</name>
						</Practitioner>
					</resource>
				</entry>
				<!--111 Org-->
				<entry>
					<fullUrl value="urn:uuid:9fd86119-3502-47a9-a7a9-3088c4ee3527"/>
					<resource>
						<Organization>
							<id value="9fd86119-3502-47a9-a7a9-3088c4ee3527"/>
							<meta>
								<profile value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1"/>
							</meta>
							<identifier>
								<system value="https://fhir.nhs.uk/Id/ods-organization-code"/>
								<value value="ABC12"/>
							</identifier>
							<name value="HAMPSHIRE NHS 111 CALL CENTRE"/>
							<address>
								<line value="1 HIGH STREET"/>
								<line value="BASINGSTOKE"/>
								<line value="HAMPSHIRE"/>
								<postalCode value="HA56 9AM"/>
							</address>
						</Organization>
					</resource>
				</entry>
				<!--Patient-->
				<entry>
					<fullUrl value="urn:uuid:9af701f7-5eb2-4402-bb3c-8ef8c8190082"/>
					<resource>
						<Patient>
							<id value="9af701f7-5eb2-4402-bb3c-8ef8c8190082"/>
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
								<family value="SMITH"/>
								<given value="Jack"/>
							</name>
							<gender value="male"/>
							<birthDate value="2006-02-04"/>
							<address>
								<postalCode value="HA17 4NK"/>
							</address>
							<managingOrganization>
								<reference value="urn:uuid:e46d86bf-1720-4c55-878f-a034d8349bbd"/>
							</managingOrganization>
						</Patient>
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
							<name value="ANDOVER Medical Centre"/>
							<address>
								<line value="1 The Practice House"/>
								<city value="ANDOVER"/>
								<postalCode value="HA21 7PA"/>
							</address>
						</Organization>
					</resource>
				</entry>
				<!--Pharmacy Encounter-->
				<entry>
					<fullUrl value="urn:uuid:d96ac9ee-208d-487b-8321-25eb895a3d31"/>
					<resource>
						<!--Encounter resource providing context for the pharmacy visit-->
						<Encounter>
							<id value="d96ac9ee-208d-487b-8321-25eb895a3d31"/>
							<meta>
								<profile value="https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Encounter-1"/>
							</meta>
							<status value="finished"/>
							<subject>
								<reference value="urn:uuid:9af701f7-5eb2-4402-bb3c-8ef8c8190082"/>
								<display value="SMITH, Jack"/>
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
									<reference value="urn:uuid:185e4d61-be11-4bd9-81ab-07a9e489566d"/>
									<display value="JONES Catherine (Ms)"/>
								</individual>
							</participant>
							<period>
								<start value="2021-03-09T08:59:00+00:00"/>
							</period>
							<serviceProvider>
								<reference value="urn:uuid:f038775b-64a6-4afa-8de3-ae9266b11408"/>
								<display value="Overtown Pharmacy"/>
							</serviceProvider>
						</Encounter>
					</resource>
				</entry>
				<!--Pharmacy associated with the encounter. -->
				<entry>
					<fullUrl value="urn:uuid:f038775b-64a6-4afa-8de3-ae9266b11408"/>
					<resource>
						<Organization>
							<id value="f038775b-64a6-4afa-8de3-ae9266b11408"/>
							<meta>
								<profile value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1"/>
							</meta>
							<identifier>
								<system value="https://fhir.nhs.uk/Id/ods-organization-code"/>
								<value value="FQ123"/>
							</identifier>
							<name value="ANDOVER PHAMACY"/>
							<telecom>
								<system value="phone"/>
								<value value="01534875516"/>
							</telecom>
							<address>
								<line value="2 SEASIDE COURT"/>
								<line value="ANDOVER"/>
								<line value="HAMPSHIRE"/>
								<postalCode value="HA45 6TP"/>
							</address>
						</Organization>
					</resource>
				</entry>
				<!--Pharmacist associated with the encounter. -->
				<entry>
					<fullUrl value="urn:uuid:185e4d61-be11-4bd9-81ab-07a9e489566d"/>
					<resource>
						<Practitioner>
							<id value="185e4d61-be11-4bd9-81ab-07a9e489566d"/>
							<meta>
								<profile value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1"/>
							</meta>
							<identifier>
								<system value="https://fhir.hl7.org.uk/Id/gphc-number"/>
								<value value="2145879"/>
							</identifier>
							<name>
								<family value="JONES"/>
								<given value="Catherine"/>
								<prefix value="Ms"/>
							</name>
							<telecom>
								<system value="phone"/>
								<value value="0113895123"/>
								<use value="work"/>
							</telecom>
							<gender value="female"/>
						</Practitioner>
					</resource>
				</entry>
				<!--Presenting Condition-->
				<entry>
					<fullUrl value="urn:uuid:880b62cd-b2d6-43b0-b2c8-d6b6f04af496"/>
					<resource>
						<Condition>
							<meta>
								<profile value="https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Condition-1"/>
							</meta>
							<clinicalStatus value="active"/>
							<code>
								<coding>
									<code value="9826008"/>
									<system value="http://snomed.info/sct"/>
									<display value="Conjunctivitis"/>
								</coding>
							</code>
							<bodySite>
								<coding>
									<code value="8966001"/>
									<system value="http://snomed.info/sct"/>
									<display value="Left eye"/>
								</coding>
							</bodySite>
							<subject>
								<reference value="urn:uuid:9af701f7-5eb2-4402-bb3c-8ef8c8190082"/>
							</subject>
							<onsetString value="3 days prior to being seen"/>
						</Condition>
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
								<reference value="urn:uuid:9af701f7-5eb2-4402-bb3c-8ef8c8190082"/>
								<display value="SMITH, William (Mr)"/>
							</subject>
							<encounter>
								<reference value="urn:uuid:d96ac9ee-208d-487b-8321-25eb895a3d31"/>
							</encounter>
							<date value="2021-03-09"/>
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
								<display value="Chloramphenicol 5 mg/mL eye drops"/>
							</medicationReference>
							<subject>
								<reference value="urn:uuid:9af701f7-5eb2-4402-bb3c-8ef8c8190082"/>
								<display value="SMITH, Jack"/>
							</subject>
							<context>
								<reference value="urn:uuid:d96ac9ee-208d-487b-8321-25eb895a3d31"/>
							</context>
							<performer>
								<actor>
									<reference value="urn:uuid:185e4d61-be11-4bd9-81ab-07a9e489566d"/>
								</actor>
								<onBehalfOf>
									<reference value="urn:uuid:f038775b-64a6-4afa-8de3-ae9266b11408"/>
								</onBehalfOf>
							</performer>
							<quantity>
								<extension url="https://fhir.hl7.org.uk/STU3/StructureDefinition/Extension-CareConnect-MedicationQuantityText-1">
									<valueString value="20 ml"/>
								</extension>
								<value value="1"/>
								<unit value="unit"/>
							</quantity>
							<whenHandedOver value="2021-03-09"/>
							<dosageInstruction>
								<text value="Take 2 drops, 4 times a day"/>
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
								<display value="Paracetamol 500 mg oral tablet"/>
							</medicationReference>
							<subject>
								<reference value="urn:uuid:9af701f7-5eb2-4402-bb3c-8ef8c8190082"/>
								<display value="SMITH, Jack"/>
							</subject>
							<context>
								<reference value="urn:uuid:d96ac9ee-208d-487b-8321-25eb895a3d31"/>
							</context>
							<performer>
								<actor>
									<reference value="urn:uuid:185e4d61-be11-4bd9-81ab-07a9e489566d"/>
								</actor>
								<onBehalfOf>
									<reference value="urn:uuid:f038775b-64a6-4afa-8de3-ae9266b11408"/>
								</onBehalfOf>
							</performer>
							<quantity>
								<value value="24"/>
								<unit value="tablet"/>
							</quantity>
							<whenHandedOver value="2021-03-09"/>
							<dosageInstruction>
								<text value="Take 2 tables, 4 times a day"/>
							</dosageInstruction>
						</MedicationDispense>
					</resource>
				</entry>
				<!--Medication prescribed (Chloramphenicol)-->
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
									<code value="330286001"/>
									<display value="Chloramphenicol 5 mg/mL eye drops"/>
								</coding>
							</code>
							<status value="active"/>
						</Medication>
					</resource>
				</entry>
				<!--Medication prescribed (paracetamol)-->
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
									<code value="322236009"/>
									<display value="Paracetamol 500 mg oral tablet"/>
								</coding>
							</code>
							<status value="active"/>
						</Medication>
					</resource>
				</entry>
				<!--BP Observation-->
				<entry>
					<fullUrl value="urn:uuid:f08fb19d-4e80-4394-a56a-01794414562d"/>
					<resource>
						<Observation>
							<id value="f08fb19d-4e80-4394-a56a-01794414562d"/>
							<meta>
								<profile value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-BloodPressure-Observation-1"/>
							</meta>
							<!--a fixed value for status-->
							<status value="final"/>
							<!--fixed value for category-->
							<category>
								<coding>
									<system value="http://hl7.org/fhir/observation-category"/>
									<code value="vital-signs"/>
									<display value="Vital Signs"/>
								</coding>
							</category>
							<!--fixed values for code-->
							<code>
								<coding>
									<system value="http://loinc.org"/>
									<code value="85354-9"/>
									<display value="Blood pressure panel with all children optional"/>
								</coding>
								<coding>
									<system value="http://snomed.info/sct"/>
									<code value="75367002"/>
									<display value="Blood pressure"/>
								</coding>
							</code>
							<!--a link to the Patient-->
							<subject>
								<reference value="urn:uuid:9af701f7-5eb2-4402-bb3c-8ef8c8190082"/>
							</subject>
							<!--the date and time of the reading-->
							<effectiveDateTime value="2021-03-09T09:01:59+00:00"/>
							<!--example of a link to a Practitioner-->
							<performer>
								<reference value="urn:uuid:185e4d61-be11-4bd9-81ab-07a9e489566d"/>
							</performer>
							<!--body site of reading-->
							<bodySite>
								<coding>
									<system value="http://snomed.info/sct"/>
									<code value="368209003"/>
									<display value="Right arm"/>
								</coding>
							</bodySite>
							<!--systolic-->
							<component>
								<!--fixed values for code-->
								<code>
									<coding>
										<system value="http://loinc.org"/>
										<code value="8480-6"/>
										<display value="Systolic blood pressure"/>
									</coding>
									<coding>
										<system value="http://snomed.info/sct"/>
										<code value="72313002"/>
										<display value="Systolic blood pressure"/>
									</coding>
								</code>
								<!--the systolic reading-->
								<valueQuantity>
									<value value="136"/>
									<unit value="mmHg"/>
									<system value="http://unitsofmeasure.org"/>
								</valueQuantity>
							</component>
							<!--diastolic-->
							<component>
								<!--fixed values for code-->
								<code>
									<coding>
										<system value="http://loinc.org"/>
										<code value="8462-4"/>
										<display value="Diastolic blood pressure"/>
									</coding>
									<coding>
										<system value="http://snomed.info/sct"/>
										<code value="1091811000000102"/>
										<display value="Diastolic arterial pressure"/>
									</coding>
								</code>
								<!--the diastolic reading-->
								<valueQuantity>
									<value value="93"/>
									<unit value="mmHg"/>
									<system value="http://unitsofmeasure.org"/>
								</valueQuantity>
							</component>
						</Observation>
					</resource>
				</entry>
				<!--Pulse rate Observation-->
				<entry>
					<fullUrl value="urn:uuid:fe15bbb9-db3f-4269-a8e2-bb034445b065"/>
					<resource>
						<Observation xmlns="http://hl7.org/fhir">
							<id value="fe15bbb9-db3f-4269-a8e2-bb034445b065"/>
							<meta>
								<!--claims conformance to CareConnect-HeartRate-Observation-1-->
								<profile value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-HeartRate-Observation-1"/>
							</meta>
							<!--fixed value for status-->
							<status value="final"/>
							<!--fixed value for category-->
							<category>
								<coding>
									<system value="http://hl7.org/fhir/observation-category"/>
									<code value="vital-signs"/>
									<display value="Vital Signs"/>
								</coding>
							</category>
							<!--fixed values for code, plus an extra SNOMED code for pulse rate-->
							<code>
								<coding>
									<system value="http://loinc.org"/>
									<code value="8867-4"/>
									<display value="Heart rate"/>
								</coding>
								<coding>
									<system value="http://snomed.info/sct"/>
									<code value="364075005"/>
									<display value="Heart rate"/>
								</coding>
							</code>
							<!--link to patient-->
							<subject>
								<reference value="urn:uuid:9af701f7-5eb2-4402-bb3c-8ef8c8190082"/>
							</subject>
							<!--the date and time of the reading-->
							<effectiveDateTime value="2018-10-04T14:17:59+01:00"/>
							<!--example of a link to a Practitioner-->
							<performer>
								<reference value="urn:uuid:185e4d61-be11-4bd9-81ab-07a9e489566d"/>
							</performer>
							<!--the pulse rate reading-->
							<valueQuantity>
								<value value="82"/>
								<unit value="bpm"/>
								<system value="http://unitsofmeasure.org"/>
							</valueQuantity>
						</Observation>
					</resource>
				</entry>
			</Bundle>
		</resource>
	</entry>
</Bundle>
<!--</xml>-->
```

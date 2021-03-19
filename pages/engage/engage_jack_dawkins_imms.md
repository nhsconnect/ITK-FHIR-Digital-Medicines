---
title: Jack Dawkins COVID Vaccination Scenario
keywords: workflow
tags: [development,fhir,profiles]
sidebar: overview_sidebar
permalink: engage_jack_dawkins_imms.html
summary: "Example scenario - Jack Dawkins COVID Vaccination Scenario"
---

## Background ##

Mr Jack Dawkins is a 58 year old male healthcare worker. As a healthcare worker he is offered a COVID vaccination by his employer.

Mr Dawkins agrees to have the vaccination. The nurse completes the first dose COVID vaccination and sends the relevant information captured from Mr Dawkins to his GP.

## The Vaccination Encounter ##

The Vaccination Encounter is documented in the [Encounter Resource](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Encounter-1)

## Named Participants ##

- Patient - **Jack Dawkins** - [Patient Resource](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1)
- Nurse - **Mr Rafferty Holding** - [Practitioner Resource](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1)


## Named Organisations ##

- Patient's GP Practice - **MGP Medical Centre** - [Organization Resource](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)

## Example Instance of Scenario ##

{% include note.html content="These examples have not been clinically assured against Digital Medicines use cases.<br/>Examples are illustrative only. They do not imply business requirements in terms of the ITK Wrapper population, or clinical requirements for SNOMED CT representations used in the Immunization.vaccinationProtocol.targetDisease element." %}

```
<!--<xml>-->
<!--This xml example is for illustrative purposes only and has not been clinically verified.-->
<Bundle xmlns="http://hl7.org/fhir">
	<id value="ede9fe38-2d81-11eb-adc1-0242ac120002"/>
	<meta>
		<lastUpdated value="2020-12-10T10:00:00+00:00"/>
		<profile value="https://fhir.nhs.uk/STU3/StructureDefinition/ITK-Document-Bundle-1"/>
	</meta>
	<identifier>
		<value value="ede9ff0a-2d81-11eb-adc1-0242ac120002"/>
	</identifier>
	<type value="document"/>
	<!-- Pharmacy Vaccinations Notification Document -->
	<entry>
		<fullUrl value="urn:uuid:ede9ffc8-2d81-11eb-adc1-0242ac120002"/>
		<resource>
			<!-- A resource carrying a set of vaccination related information about the patient -->
			<Composition>
				<id value="ede9ffc8-2d81-11eb-adc1-0242ac120002"/>
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
					<value value="edea0158-2d81-11eb-adc1-0242ac120002"/>
				</identifier>
				<!-- The workflow/clinical status of this composition. The status is a marker for the clinical standing of the document. -->
				<status value="final"/>
				<type>
					<!-- Digital Medicines document type -->
					<coding>
						<system value="http://snomed.info/sct"/>
						<code value="41000179103"/>
						<display value="Immunisation record"/>
					</coding>
				</type>
				<!-- Reference to the patient subject of the Composition -->
				<subject>
					<reference value="urn:uuid:edea022a-2d81-11eb-adc1-0242ac120002"/>
				</subject>
				<!-- Reference to the clinical encounter or type of care this documentation is associated with. -->
				<encounter>
					<reference value="urn:uuid:857ad538-2fc1-11eb-adc1-0242ac120002"/>
				</encounter>
				<!-- The composition editing time, when the composition was last logically changed by the author. -->
				<date value="2020-12-01T10:00:00+00:00"/>
				<!-- Identifies who is responsible for the information in the composition, not necessarily who typed it in -->
				<author>
					<reference value="urn:uuid:edea02f2-2d81-11eb-adc1-0242ac120002"/>
				</author>
				<title value="COVID-19 Immunization Record"/>
				<!-- Identifies the organization responsible for ongoing maintenance of and access to the composition/document information. -->
				<custodian>
					<reference value="urn:uuid:edea03b0-2d81-11eb-adc1-0242ac120002"/>
				</custodian>
				<!-- Attendance details section -->
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
										<td>01-Dec-2020 10:08</td>
									</tr>
								</tbody>
							</table>
						</div>
					</text>
					<!--Reference to Encounter resource as the source of information for this section-->
					<entry>
						<reference value="urn:uuid:857ad538-2fc1-11eb-adc1-0242ac120002"/>
					</entry>
				</section>
				<!-- Consent -->
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
										<td>Immunization consent given</td>
									</tr>
								</tbody>
							</table>
						</div>
					</text>
				</section>
				<!-- GP Practice -->
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
										<th>GP practice identifier</th>
										<td>
											<p>ODS Organization Code: A83627</p>
										</td>
									</tr>
									<tr>
										<th>GP practice details</th>
										<td>
											<p>Name: MGP Medical Centre</p>
										</td>
									</tr>
								</tbody>
							</table>
						</div>
					</text>
					<!-- Reference to the GP Practice Organisation entry -->
					<entry>
						<reference value="urn:uuid:edea03b0-2d81-11eb-adc1-0242ac120002"/>
					</entry>
				</section>
				<!-- Vaccinations -->
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
										<td>Vaccine product: Talent 0.5ml dose solution for injection multidose vials (Secretary of State for Health)</td>
										<td>Vaccine procedure: Administration of first dose of SARS-CoV-2 (severe acute respiratory syndrome coronavirus 2) vaccine.</td>
										<td>Route: Intramuscular route</td>
										<td>Indication: Disease outbreak (event)</td>
									</tr>
									<tr>
										<td>Administered by: Rafferty Holding</td>
										<td>NMC identifier: 95B0242E</td>
										<td>Date Time: 01-Dec-2020 10:08</td>
									</tr>
								</tbody>
							</table>
						</div>
					</text>
					<!-- Reference to the Immunization resource entry -->
					<entry>
						<reference value="urn:uuid:631ec8d3-6341-4c9e-b2a1-131af62718f2"/>
					</entry>
				</section>
				<!-- Patient demographics -->
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
											<p>Given Name: Jack</p>
											<p>Family Name: Dawkins</p>
										</td>
									</tr>
									<tr>
										<th>Date of birth</th>
										<td>22 August 1962</td>
									</tr>
									<tr>
										<th>Sex</th>
										<td>Male</td>
									</tr>
									<tr>
										<th>NHS number</th>
										<td>99120038885</td>
									</tr>
									<tr>
										<th>Patient address</th>
										<td>
											<p>Post Code: LA19 5YN</p>
										</td>
									</tr>
								</tbody>
							</table>
						</div>
					</text>
					<!-- Reference to the Patient resource entry -->
					<entry>
						<reference value="urn:uuid:edea022a-2d81-11eb-adc1-0242ac120002"/>
					</entry>
				</section>
			</Composition>
		</resource>
	</entry>
	<!-- Encounter resource entry -->
	<entry>
		<fullUrl value="urn:uuid:857ad538-2fc1-11eb-adc1-0242ac120002"/>
		<resource>
			<!-- Encounter resource providing context for the immunisation -->
			<Encounter xmlns="http://hl7.org/fhir">
				<id value="857ad538-2fc1-11eb-adc1-0242ac120002"/>
				<meta>
					<profile value="https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Encounter-1"/>
				</meta>
				<status value="finished"/>
				<subject>
					<reference value="urn:uuid:edea022a-2d81-11eb-adc1-0242ac120002"/>
					<display value="DAWKINS, Jack"/>
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
						<reference value="urn:uuid:edea02f2-2d81-11eb-adc1-0242ac120002"/>
						<display value="HOLDING, Rafferty"/>
					</individual>
				</participant>
				<period>
					<start value="2020-01-20T10:08:15+01:00"/>
				</period>
				<serviceProvider>
					<reference value="urn:uuid:edea05c2-2d81-11eb-adc1-0242ac120002"/>
				</serviceProvider>
			</Encounter>
		</resource>
	</entry>
	<!-- Patient's registered GP Practice. -->
	<entry>
		<fullUrl value="urn:uuid:edea03b0-2d81-11eb-adc1-0242ac120002"/>
		<resource>
			<Organization>
				<id value="edea03b0-2d81-11eb-adc1-0242ac120002"/>
				<meta>
					<profile value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1"/>
				</meta>
				<identifier>
					<system value="https://fhir.nhs.uk/Id/ods-organization-code"/>
					<value value="A83627"/>
				</identifier>
				<name value="MGP Medical Centre"/>
			</Organization>
		</resource>
	</entry>
	<!-- Immunization resource entry-->
	<entry>
		<fullUrl value="urn:uuid:631ec8d3-6341-4c9e-b2a1-131af62718f2"/>
		<resource>
			<Immunization>
				<id value="631ec8d3-6341-4c9e-b2a1-131af62718f2"/>
				<meta>
					<profile value="https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-DM-Immunization-1"/>
				</meta>
				<extension url="https://fhir.hl7.org.uk/STU3/StructureDefinition/Extension-CareConnect-DateRecorded-1">
					<valueDateTime value="2020-12-01"/>
				</extension>
				<extension url="https://fhir.hl7.org.uk/STU3/StructureDefinition/Extension-CareConnect-VaccinationProcedure-1">
					<valueCodeableConcept>
						<coding>
							<system value="http://snomed.info/sct"/>
							<code value="1324681000000101"/>
							<display value="Administration of first dose of severe acute respiratory syndrome coronavirus 2 vaccine (procedure)"/>
						</coding>
					</valueCodeableConcept>
				</extension>
				<identifier>
					<system value="https://tools.ietf.org/html/rfc4122"/>
					<value value="91df61b6-2da2-11eb-adc1-0242ac120002"/>
				</identifier>
				<status value="completed"/>
				<notGiven value="false"/>
				<vaccineCode>
					<coding>
						<system value="http://snomed.info/sct"/>
						<code value="39114911000001105"/>
						<display value="COVID-19 Vaccine AstraZeneca (ChAdOx1 S [recombinant]) 5x10,000,000,000 viral particles/0.5ml dose solution for injection multidose vials (AstraZeneca UK Ltd) (product)"/>
					</coding>
				</vaccineCode>
				<patient>
					<reference value="urn:uuid:edea022a-2d81-11eb-adc1-0242ac120002"/>
					<display value="DAWKINS, Jack"/>
				</patient>
				<!-- Encounter reference for Immunization -->
				<encounter>
					<reference value="urn:uuid:857ad538-2fc1-11eb-adc1-0242ac120002"/>
				</encounter>
				<date value="2020-01-20T10:08:15+01:00"/>
				<primarySource value="true"/>
				<manufacturer>
					<reference value="urn:uuid:edea068a-2d81-11eb-adc1-0242ac120002"/>
					<display value="DREAMLAND Pharmaceuticals Ltd"/>
				</manufacturer>
				<lotNumber value="R04X"/>
				<expirationDate value="2021-04-15"/>
				<site>
					<coding>
						<system value="http://snomed.info/sct"/>
						<code value="368208006"/>
						<display value="Left upper arm structure (body structure)"/>
					</coding>
				</site>
				<route>
					<coding>
						<system value="http://snomed.info/sct"/>
						<code value="78421000"/>
						<display value="Intramuscular route (qualifier value)"/>
					</coding>
				</route>
				<doseQuantity>
					<value value="1"/>
					<unit value="pre-filled disposable injection"/>
					<system value="http://snomed.info/sct"/>
					<code value="3318611000001103"/>
				</doseQuantity>
				<practitioner>
					<role>
						<coding>
							<system value="http://hl7.org/fhir/v2/0443"/>
							<code value="AP"/>
							<display value="Administering Provider"/>
						</coding>
					</role>
					<actor>
						<reference value="urn:uuid:edea02f2-2d81-11eb-adc1-0242ac120002"/>
						<display value="HOLDING, Rafferty"/>
					</actor>
				</practitioner>
				<explanation>
					<reason>
						<coding>
							<system value="http://snomed.info/sct"/>
							<code value="443684005"/>
							<display value="Disease outbreak (event)"/>
						</coding>
					</reason>
				</explanation>
				<vaccinationProtocol>
					<doseSequence value="1"/>
					<targetDisease>
						<coding>
							<system value="http://snomed.info/sct"/>
							<code value="1240751000000100"/>
							<display value="Coronavirus disease 19 caused by severe acute respiratory syndrome coronavirus 2 (disorder)"/>
						</coding>
					</targetDisease>
					<doseStatus>
						<coding>
							<system value="http://hl7.org/fhir/vaccination-protocol-dose-status"/>
							<code value="count"/>
							<display value="Counts"/>
						</coding>
					</doseStatus>
				</vaccinationProtocol>
			</Immunization>
		</resource>
	</entry>
	<!-- Patient associated with the Immunization. -->
	<entry>
		<fullUrl value="urn:uuid:edea022a-2d81-11eb-adc1-0242ac120002"/>
		<resource>
			<Patient>
				<id value="edea022a-2d81-11eb-adc1-0242ac120002"/>
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
					<value value="9912003888"/>
				</identifier>
				<name>
					<use value="official"/>
					<family value="DAWKINS"/>
					<given value="Jack"/>
				</name>
				<gender value="male"/>
				<birthDate value="1962-08-22"/>
				<address>
					<use value="home"/>
					<type value="both"/>
					<postalCode value="LA19 5YN"/>
				</address>
				<generalPractitioner>
					<reference value="urn:uuid:edea03b0-2d81-11eb-adc1-0242ac120002"/>
				</generalPractitioner>
			</Patient>
		</resource>
	</entry>
	<!-- Practitioner performing the Immunization -->
	<entry>
		<fullUrl value="urn:uuid:edea02f2-2d81-11eb-adc1-0242ac120002"/>
		<resource>
			<Practitioner>
				<id value="edea02f2-2d81-11eb-adc1-0242ac120002"/>
				<meta>
					<profile value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1"/>
				</meta>
				<identifier>
					<system value="https://fhir.hl7.org.uk/Id/nmc-number"/>
					<value value="95B0242E"/>
				</identifier>
				<name>
					<family value="HOLDING"/>
					<given value="Rafferty"/>
				</name>
			</Practitioner>
		</resource>
	</entry>
	<!-- Encounter and Immunization serviceProvider -->
	<entry>
		<fullUrl value="urn:uuid:edea05c2-2d81-11eb-adc1-0242ac120002"/>
		<resource>
			<Organization>
				<id value="edea05c2-2d81-11eb-adc1-0242ac120002"/>
				<meta>
					<profile value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1"/>
				</meta>
				<identifier>
					<system value="https://fhir.nhs.uk/Id/ods-site-code"/>
					<value value="RCD52"/>
				</identifier>
			</Organization>
		</resource>
	</entry>
	<entry>
		<fullUrl value="urn:uuid:edea068a-2d81-11eb-adc1-0242ac120002"/>
		<resource>
			<Organization>
				<id value="edea068a-2d81-11eb-adc1-0242ac120002"/>
				<meta>
					<profile value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1"/>
				</meta>
				<name value="DREAMLAND Pharmaceuticals Ltd"/>
			</Organization>
		</resource>
	</entry>
	<!-- Practitioner Role -->
	<entry>
		<fullUrl value="urn:uuid:edea0748-2d81-11eb-adc1-0242ac120002"/>
		<resource>
			<PractitionerRole>
				<id value="edea0748-2d81-11eb-adc1-0242ac120002"/>
				<meta>
					<profile value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-PractitionerRole-1"/>
				</meta>
				<practitioner>
					<reference value="urn:uuid:edea02f2-2d81-11eb-adc1-0242ac120002"/>
				</practitioner>
				<code>
					<coding>
						<system value="https://fhir.hl7.org.uk/STU3/CodeSystem/CareConnect-SDSJobRoleName-1"/>
						<code value="R0410"/>
						<display value="Student Practice Nurse"/>
					</coding>
				</code>
			</PractitionerRole>
		</resource>
	</entry>
</Bundle>
<!--</xml>-->
```
<a href="engage_jack_dawkins_imms.html">Back to top of page</a>
## Example Instance of Scenario - ITK Wrapper ##

{% include note.html content="These examples have not been clinically assured against Digital Medicines use cases.<br/>Examples are illustrative only." %}

```
<!--<xml>-->
<!-- This xml example is for illustrative purposes only and has not been clinically verified. -->
<Bundle xmlns="http://hl7.org/fhir">
	<id value="ede9f046-2d81-11eb-adc1-0242ac120002"/>
	<meta>
		<profile value="https://fhir.nhs.uk/STU3/StructureDefinition/ITK-Message-Bundle-1"/>
	</meta>
	<identifier>
		<value value="ede9f366-2d81-11eb-adc1-0242ac120002"/>
	</identifier>
	<type value="message"/>
	<entry>
		<fullUrl value="urn:uuid:ede9f97e-2d81-11eb-adc1-0242ac120002"/>
		<resource>
			<MessageHeader>
				<id value="ede9f97e-2d81-11eb-adc1-0242ac120002"/>
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
					<reference value="urn:uuid:d1cdde66-77e1-4180-902c-ffe542fe6b12"/>
				</receiver>
				<sender>
					<reference value="urn:uuid:ede9fd5c-2d81-11eb-adc1-0242ac120002"/>
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
	<!-- Sender Organisation -->
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
					<value value="X26"/>
				</identifier>
			</Organization>
		</resource>
	</entry>
	<!-- Receiver Organization -->
	<entry>
		<fullUrl value="urn:uuid:d1cdde66-77e1-4180-902c-ffe542fe6b12"/>
		<resource>
			<Organization>
				<id value="d1cdde66-77e1-4180-902c-ffe542fe6b12"/>
				<meta>
					<profile value="https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Header-Organization-1"/>
				</meta>
				<identifier>
					<system value="https://fhir.nhs.uk/Id/ods-organization-code"/>
					<value value="A83627"/>
				</identifier>
			</Organization>
		</resource>
	</entry>
	<entry>
		<fullUrl value="urn:uuid:ede9fe38-2d81-11eb-adc1-0242ac120002"/>
		<resource>
			<!-- This xml example is for illustrative purposes only and has not been clinically verified. -->
			<Bundle>
				<id value="ede9fe38-2d81-11eb-adc1-0242ac120002"/>
				<meta>
					<lastUpdated value="2020-12-10T10:00:00+00:00"/>
					<profile value="https://fhir.nhs.uk/STU3/StructureDefinition/ITK-Document-Bundle-1"/>
				</meta>
				<identifier>
					<value value="ede9ff0a-2d81-11eb-adc1-0242ac120002"/>
				</identifier>
				<type value="document"/>
				<!-- Pharmacy Vaccinations Notification Document -->
				<entry>
					<fullUrl value="urn:uuid:ede9ffc8-2d81-11eb-adc1-0242ac120002"/>
					<resource>
						<!-- A resource carrying a set of vaccination related information about the patient -->
						<Composition>
							<id value="ede9ffc8-2d81-11eb-adc1-0242ac120002"/>
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
								<value value="edea0158-2d81-11eb-adc1-0242ac120002"/>
							</identifier>
							<!-- The workflow/clinical status of this composition. The status is a marker for the clinical standing of the document. -->
							<status value="final"/>
							<type>
								<!-- Digital Medicines document type -->
								<coding>
									<system value="http://snomed.info/sct"/>
									<code value="41000179103"/>
									<display value="Immunisation record"/>
								</coding>
							</type>
							<!-- Reference to the patient subject of the Composition -->
							<subject>
								<reference value="urn:uuid:edea022a-2d81-11eb-adc1-0242ac120002"/>
							</subject>
							<!-- Reference to the clinical encounter or type of care this documentation is associated with. -->
							<encounter>
								<reference value="urn:uuid:857ad538-2fc1-11eb-adc1-0242ac120002"/>
							</encounter>
							<!-- The composition editing time, when the composition was last logically changed by the author. -->
							<date value="2020-12-01T10:00:00+00:00"/>
							<!-- Identifies who is responsible for the information in the composition, not necessarily who typed it in -->
							<author>
								<reference value="urn:uuid:edea02f2-2d81-11eb-adc1-0242ac120002"/>
							</author>
							<title value="COVID-19 Immunization Record"/>
							<!-- Identifies the organization responsible for ongoing maintenance of and access to the composition/document information. -->
							<custodian>
								<reference value="urn:uuid:edea03b0-2d81-11eb-adc1-0242ac120002"/>
							</custodian>
							<!-- Attendance details section -->
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
													<td>01-Dec-2020 10:08</td>
												</tr>
											</tbody>
										</table>
									</div>
								</text>
								<!--Reference to Encounter resource as the source of information for this section-->
								<entry>
									<reference value="urn:uuid:857ad538-2fc1-11eb-adc1-0242ac120002"/>
								</entry>
							</section>
							<!-- Consent -->
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
													<td>Immunization consent given</td>
												</tr>
											</tbody>
										</table>
									</div>
								</text>
							</section>
							<!-- GP Practice -->
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
													<th>GP practice identifier</th>
													<td>
														<p>ODS Organization Code: A83627</p>
													</td>
												</tr>
												<tr>
													<th>GP practice details</th>
													<td>
														<p>Name: MGP Medical Centre</p>
													</td>
												</tr>
											</tbody>
										</table>
									</div>
								</text>
								<!-- Reference to the GP Practice Organisation entry -->
								<entry>
									<reference value="urn:uuid:edea03b0-2d81-11eb-adc1-0242ac120002"/>
								</entry>
							</section>
							<!-- Vaccinations -->
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
													<td>Vaccine product: Talent 0.5ml dose solution for injection multidose vials (Secretary of State for Health)</td>
													<td>Vaccine procedure: Administration of first dose of SARS-CoV-2 (severe acute respiratory syndrome coronavirus 2) vaccine.</td>
													<td>Route: Intramuscular route</td>
													<td>Indication: Disease outbreak (event)</td>
												</tr>
												<tr>
													<td>Administered by: Rafferty Holding</td>
													<td>NMC identifier: 95B0242E</td>
													<td>Date Time: 01-Dec-2020 10:08</td>
												</tr>
											</tbody>
										</table>
									</div>
								</text>
								<!-- Reference to the Immunization resource entry -->
								<entry>
									<reference value="urn:uuid:631ec8d3-6341-4c9e-b2a1-131af62718f2"/>
								</entry>
							</section>
							<!-- Patient demographics -->
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
														<p>Given Name: Jack</p>
														<p>Family Name: Dawkins</p>
													</td>
												</tr>
												<tr>
													<th>Date of birth</th>
													<td>22 August 1962</td>
												</tr>
												<tr>
													<th>Sex</th>
													<td>Male</td>
												</tr>
												<tr>
													<th>NHS number</th>
													<td>99120038885</td>
												</tr>
												<tr>
													<th>Patient address</th>
													<td>
														<p>Post Code: LA19 5YN</p>
													</td>
												</tr>
											</tbody>
										</table>
									</div>
								</text>
								<!-- Reference to the Patient resource entry -->
								<entry>
									<reference value="urn:uuid:edea022a-2d81-11eb-adc1-0242ac120002"/>
								</entry>
							</section>
						</Composition>
					</resource>
				</entry>
				<!-- Encounter resource entry -->
				<entry>
					<fullUrl value="urn:uuid:857ad538-2fc1-11eb-adc1-0242ac120002"/>
					<resource>
						<!-- Encounter resource providing context for the immunisation -->
						<Encounter xmlns="http://hl7.org/fhir">
							<id value="857ad538-2fc1-11eb-adc1-0242ac120002"/>
							<meta>
								<profile value="https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Encounter-1"/>
							</meta>
							<status value="finished"/>
							<subject>
								<reference value="urn:uuid:edea022a-2d81-11eb-adc1-0242ac120002"/>
								<display value="DAWKINS, Jack"/>
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
									<reference value="urn:uuid:edea02f2-2d81-11eb-adc1-0242ac120002"/>
									<display value="HOLDING, Rafferty"/>
								</individual>
							</participant>
							<period>
								<start value="2020-01-20T10:08:15+01:00"/>
							</period>
							<serviceProvider>
								<reference value="urn:uuid:edea05c2-2d81-11eb-adc1-0242ac120002"/>
							</serviceProvider>
						</Encounter>
					</resource>
				</entry>
				<!-- Patient's registered GP Practice. -->
				<entry>
					<fullUrl value="urn:uuid:edea03b0-2d81-11eb-adc1-0242ac120002"/>
					<resource>
						<Organization>
							<id value="edea03b0-2d81-11eb-adc1-0242ac120002"/>
							<meta>
								<profile value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1"/>
							</meta>
							<identifier>
								<system value="https://fhir.nhs.uk/Id/ods-organization-code"/>
								<value value="A83627"/>
							</identifier>
							<name value="MGP Medical Centre"/>
						</Organization>
					</resource>
				</entry>
				<!-- Immunization resource entry-->
				<entry>
					<fullUrl value="urn:uuid:631ec8d3-6341-4c9e-b2a1-131af62718f2"/>
					<resource>
						<Immunization>
							<id value="631ec8d3-6341-4c9e-b2a1-131af62718f2"/>
							<meta>
								<profile value="https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-DM-Immunization-1"/>
							</meta>
							<extension url="https://fhir.hl7.org.uk/STU3/StructureDefinition/Extension-CareConnect-DateRecorded-1">
								<valueDateTime value="2020-12-01"/>
							</extension>
							<extension url="https://fhir.hl7.org.uk/STU3/StructureDefinition/Extension-CareConnect-VaccinationProcedure-1">
								<valueCodeableConcept>
									<coding>
										<system value="http://snomed.info/sct"/>
										<code value="1324681000000101"/>
										<display value="Administration of first dose of severe acute respiratory syndrome coronavirus 2 vaccine (procedure)"/>
									</coding>
								</valueCodeableConcept>
							</extension>
							<identifier>
								<system value="https://tools.ietf.org/html/rfc4122"/>
								<value value="91df61b6-2da2-11eb-adc1-0242ac120002"/>
							</identifier>
							<status value="completed"/>
							<notGiven value="false"/>
							<vaccineCode>
								<coding>
									<system value="http://snomed.info/sct"/>
									<code value="39114911000001105"/>
									<display value="Talent 0.5ml dose solution for injection multidose vials (Secretary of State for Health)"/>
								</coding>
							</vaccineCode>
							<patient>
								<reference value="urn:uuid:edea022a-2d81-11eb-adc1-0242ac120002"/>
								<display value="DAWKINS, Jack"/>
							</patient>
							<!-- Encounter reference for Immunization -->
							<encounter>
								<reference value="urn:uuid:857ad538-2fc1-11eb-adc1-0242ac120002"/>
							</encounter>
							<date value="2020-01-20T10:08:15+01:00"/>
							<primarySource value="true"/>
							<manufacturer>
								<reference value="urn:uuid:edea068a-2d81-11eb-adc1-0242ac120002"/>
								<display value="DREAMLAND Pharmaceuticals Ltd"/>
							</manufacturer>
							<lotNumber value="R04X"/>
							<expirationDate value="2021-04-15"/>
							<site>
								<coding>
									<system value="http://snomed.info/sct"/>
									<code value="368208006"/>
									<display value="Left upper arm structure (body structure)"/>
								</coding>
							</site>
							<route>
								<coding>
									<system value="http://snomed.info/sct"/>
									<code value="78421000"/>
									<display value="Intramuscular route (qualifier value)"/>
								</coding>
							</route>
							<doseQuantity>
								<value value="1"/>
								<unit value="pre-filled disposable injection"/>
								<system value="http://snomed.info/sct"/>
								<code value="3318611000001100"/>
							</doseQuantity>
							<practitioner>
								<role>
									<coding>
										<system value="http://hl7.org/fhir/v2/0443"/>
										<code value="AP"/>
										<display value="Administering Provider"/>
									</coding>
								</role>
								<actor>
									<reference value="urn:uuid:edea02f2-2d81-11eb-adc1-0242ac120002"/>
									<display value="HOLDING, Rafferty"/>
								</actor>
							</practitioner>
							<explanation>
								<reason>
									<coding>
										<system value="http://snomed.info/sct"/>
										<code value="443684005"/>
										<display value="Disease outbreak (event)"/>
									</coding>
								</reason>
							</explanation>
							<vaccinationProtocol>
								<doseSequence value="1"/>
								<targetDisease>
									<coding>
										<system value="http://snomed.info/sct"/>
										<code value="1240751000000100"/>
										<display value="Coronavirus disease 19 caused by severe acute respiratory syndrome coronavirus 2 (disorder)"/>
									</coding>
								</targetDisease>
								<doseStatus>
									<coding>
										<system value="http://hl7.org/fhir/vaccination-protocol-dose-status"/>
										<code value="count"/>
										<display value="Counts"/>
									</coding>
								</doseStatus>
							</vaccinationProtocol>
						</Immunization>
					</resource>
				</entry>
				<!-- Patient associated with the Immunization. -->
				<entry>
					<fullUrl value="urn:uuid:edea022a-2d81-11eb-adc1-0242ac120002"/>
					<resource>
						<Patient>
							<id value="edea022a-2d81-11eb-adc1-0242ac120002"/>
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
								<value value="9912003888"/>
							</identifier>
							<name>
								<use value="official"/>
								<family value="DAWKINS"/>
								<given value="Jack"/>
							</name>
							<gender value="male"/>
							<birthDate value="1962-08-22"/>
							<address>
								<use value="home"/>
								<type value="both"/>
								<postalCode value="LA19 5YN"/>
							</address>
							<generalPractitioner>
								<reference value="urn:uuid:edea03b0-2d81-11eb-adc1-0242ac120002"/>
							</generalPractitioner>
						</Patient>
					</resource>
				</entry>
				<!-- Practitioner performing the Immunization -->
				<entry>
					<fullUrl value="urn:uuid:edea02f2-2d81-11eb-adc1-0242ac120002"/>
					<resource>
						<Practitioner>
							<id value="edea02f2-2d81-11eb-adc1-0242ac120002"/>
							<meta>
								<profile value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1"/>
							</meta>
							<identifier>
								<system value="https://fhir.hl7.org.uk/Id/nmc-number"/>
								<value value="95B0242E"/>
							</identifier>
							<name>
								<family value="HOLDING"/>
								<given value="Rafferty"/>
							</name>
						</Practitioner>
					</resource>
				</entry>
				<!-- Encounter and Immunization serviceProvider -->
				<entry>
					<fullUrl value="urn:uuid:edea05c2-2d81-11eb-adc1-0242ac120002"/>
					<resource>
						<Organization>
							<id value="edea05c2-2d81-11eb-adc1-0242ac120002"/>
							<meta>
								<profile value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1"/>
							</meta>
							<identifier>
								<system value="https://fhir.nhs.uk/Id/ods-site-code"/>
								<value value="RCD52"/>
							</identifier>
						</Organization>
					</resource>
				</entry>
				<entry>
					<fullUrl value="urn:uuid:edea068a-2d81-11eb-adc1-0242ac120002"/>
					<resource>
						<Organization>
							<id value="edea068a-2d81-11eb-adc1-0242ac120002"/>
							<meta>
								<profile value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1"/>
							</meta>
							<name value="DREAMLAND Pharmaceuticals Ltd"/>
						</Organization>
					</resource>
				</entry>
				<!-- Practitioner Role -->
				<entry>
					<fullUrl value="urn:uuid:edea0748-2d81-11eb-adc1-0242ac120002"/>
					<resource>
						<PractitionerRole>
							<id value="edea0748-2d81-11eb-adc1-0242ac120002"/>
							<meta>
								<profile value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-PractitionerRole-1"/>
							</meta>
							<practitioner>
								<reference value="urn:uuid:edea02f2-2d81-11eb-adc1-0242ac120002"/>
							</practitioner>
							<code>
								<coding>
									<system value="https://fhir.hl7.org.uk/STU3/CodeSystem/CareConnect-SDSJobRoleName-1"/>
									<code value="R0410"/>
									<display value="Student Practice Nurse"/>
								</coding>
							</code>
						</PractitionerRole>
					</resource>
				</entry>
			</Bundle>
		</resource>
	</entry>
</Bundle>
<!--</xml>-->
```
<a href="engage_jack_dawkins_imms.html">Back to top of page</a>
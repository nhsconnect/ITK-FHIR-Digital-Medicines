---
title: Hettie Winters COVID Vaccination Scenario
keywords: workflow
tags: [development,fhir,profiles]
sidebar: overview_sidebar
permalink: engage_hettie_winters_imms.html
summary: "Example scenario - Hettie Winters COVID Vaccination Scenario"
---

## Background ##

Mrs Hettie Winters is a 57 year old female healthcare worker. As a healthcare worker she is offered a COVID vaccination by her employer. 

Mrs Hettie Winters agrees to have the vaccination. She successfully had the first dose of the vaccine. The Practitioner cannot give the second dose of the vaccination as it is contraindicated. The Practitioner records this and sends the relevant information captured from Mrs Winters to her GP.

## The Vaccination Encounter ##

The Vaccination Encounter is documented in the [Encounter Resource](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Encounter-1)

## Named Participants ##

- Patient - **Hettie Winters** - [Patient Resource](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1)
- Practitioner - **Kester Yates** - [Practitioner Resource](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1)


## Named Organisations ##

- Patient's GP Practice - **MGP Medical Centre** - [Organization Resource](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)

## Example Instance of Scenario ##

{% include note.html content="These examples have not been clinically assured against Digital Medicines use cases. <br/>Examples are illustrative only. They do not imply business requirements in terms of the ITK Wrapper population, or clinical requirements for SNOMED CT representations used in the Immunization.vaccinationProtocol.targetDisease element." %}

```
<!--<xml>-->
<!--This xml example is for illustrative purposes only and has not been clinically verified.-->
<Bundle>
	<id value="cd8371de-2e34-11eb-adc1-0242ac120002"/>
	<meta>
		<lastUpdated value="2020-12-10T16:00:00+00:00"/>
		<profile value="https://fhir.nhs.uk/STU3/StructureDefinition/ITK-Document-Bundle-1"/>
	</meta>
	<identifier>
		<value value="cd83729c-2e34-11eb-adc1-0242ac120002"/>
	</identifier>
	<type value="document"/>
	<!-- Pharmacy Vaccinations Notification Document -->
	<entry>
		<fullUrl value="urn:uuid:cd837364-2e34-11eb-adc1-0242ac120002"/>
		<resource>
			<!-- A resource carrying a set of vaccination related information about the patient -->
			<Composition>
				<id value="cd837364-2e34-11eb-adc1-0242ac120002"/>
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
					<value value="cd837422-2e34-11eb-adc1-0242ac120002"/>
				</identifier>
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
					<reference value="urn:uuid:cd8374e0-2e34-11eb-adc1-0242ac120002"/>
				</subject>
				<!-- Reference to the clinical encounter or type of care this documentation is associated with. -->
				<encounter>
					<reference value="urn:uuid:857ad2f4-2fc1-11eb-adc1-0242ac120002"/>
				</encounter>
				<!-- The composition editing time, when the composition was last logically changed by the author. -->
				<date value="2020-12-01T16:00:00+00:00"/>
				<!-- Identifies who is responsible for the information in the composition, not necessarily who typed it in -->
				<author>
					<reference value="urn:uuid:cd838160-2e34-11eb-adc1-0242ac120002"/>
				</author>
				<title value="COVID-19 Immunization Record"/>
				<!-- Identifies the organization responsible for ongoing maintenance of and access to the composition/document information. -->
				<custodian>
					<reference value="urn:uuid:cd838296-2e34-11eb-adc1-0242ac120002"/>
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
										<td>01-Dec-2020 15:37</td>
									</tr>
								</tbody>
							</table>
						</div>
					</text>
					<!-- Reference to Encounter resource as the source of information for this section -->
					<entry>
						<reference value="urn:uuid:857ad2f4-2fc1-11eb-adc1-0242ac120002"/>
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
						<reference value="urn:uuid:cd838296-2e34-11eb-adc1-0242ac120002"/>
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
										<td>Vaccine procedure: SARS-CoV-2 (severe acute respiratory syndrome coronavirus 2) vaccination first dose not given.</td>
										<td>Reason not given: SARS-CoV-2 (severe acute respiratory syndrome coronavirus 2) immunisation course contraindicated</td>
									</tr>
									<tr>
										<td>Practitioner: Kester Yates</td>
										<td>GPhC identifier: 2036622</td>
										<td>Date Time: 01-Dec-2020 15:37</td>
									</tr>
								</tbody>
							</table>
						</div>
					</text>
					<!-- Reference to the Immunization resource entry -->
					<entry>
						<reference value="urn:uuid:cd838368-2e34-11eb-adc1-0242ac120002"/>
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
											<p>Given Name: Hettie</p>
											<p>Family Name: Winters</p>
										</td>
									</tr>
									<tr>
										<th>Date of birth</th>
										<td>23 March 1963</td>
									</tr>
									<tr>
										<th>Sex</th>
										<td>Female</td>
									</tr>
									<tr>
										<th>NHS number</th>
										<td>9046556581</td>
									</tr>
									<tr>
										<th>Patient address</th>
										<td>
											<p>Post Code: HX2 6LF</p>
										</td>
									</tr>
								</tbody>
							</table>
						</div>
					</text>
					<!-- Reference to the Patient resource entry -->
					<entry>
						<reference value="urn:uuid:cd8374e0-2e34-11eb-adc1-0242ac120002"/>
					</entry>
				</section>
			</Composition>
		</resource>
	</entry>
	<!-- Encounter resource entry -->
	<entry>
		<fullUrl value="urn:uuid:857ad2f4-2fc1-11eb-adc1-0242ac120002"/>
		<resource>
			<!-- Encounter resource providing context for the Immunization -->
			<Encounter>
				<id value="857ad2f4-2fc1-11eb-adc1-0242ac120002"/>
				<meta>
					<profile value="https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Encounter-1"/>
				</meta>
				<status value="finished"/>
				<subject>
					<reference value="urn:uuid:cd8374e0-2e34-11eb-adc1-0242ac120002"/>
					<display value="WINTERS, Hettie"/>
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
						<reference value="urn:uuid:cd838160-2e34-11eb-adc1-0242ac120002"/>
						<display value="YATES, Kester"/>
					</individual>
				</participant>
				<period>
					<start value="2020-01-20T15:37:10+01:00"/>
				</period>
				<serviceProvider>
					<reference value="urn:uuid:cd8386ce-2e34-11eb-adc1-0242ac120002"/>
				</serviceProvider>
			</Encounter>
		</resource>
	</entry>
	<!-- Patient's registered GP Practice. -->
	<entry>
		<fullUrl value="urn:uuid:cd838296-2e34-11eb-adc1-0242ac120002"/>
		<resource>
			<Organization>
				<id value="cd838296-2e34-11eb-adc1-0242ac120002"/>
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
		<fullUrl value="urn:uuid:cd838368-2e34-11eb-adc1-0242ac120002"/>
		<resource>
			<Immunization>
				<id value="cd838368-2e34-11eb-adc1-0242ac120002"/>
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
							<code value="1324781000000109"/>
							<display value="Severe acute respiratory syndrome coronavirus 2 vaccination first dose not given (situation)"/>
						</coding>
					</valueCodeableConcept>
				</extension>
				<identifier>
					<system value="https://tools.ietf.org/html/rfc4122"/>
					<value value="91df61b6-2da2-11eb-adc1-0242ac120002"/>
				</identifier>
				<status value="completed"/>
				<notGiven value="true"/>
				<vaccineCode>
					<coding>
						<system value="http://snomed.info/sct"/>
						<code value="39114911000001105"/>
						<display value="Talent 0.5ml dose solution for injection multidose vials (Secretary of State for Health)"/>
					</coding>
				</vaccineCode>
				<patient>
					<reference value="urn:uuid:cd8374e0-2e34-11eb-adc1-0242ac120002"/>
					<display value="WINTERS, Hettie"/>
				</patient>
				<!-- Encounter reference for Immunization -->
				<encounter>
					<reference value="urn:uuid:857ad2f4-2fc1-11eb-adc1-0242ac120002"/>
				</encounter>
				<date value="2020-01-20T15:37:10+01:00"/>
				<primarySource value="true"/>
				<practitioner>
					<role>
						<coding>
							<system value="http://hl7.org/fhir/v2/0443"/>
							<code value="AP"/>
							<display value="Administering Provider"/>
						</coding>
					</role>
					<actor>
						<reference value="urn:uuid:cd838160-2e34-11eb-adc1-0242ac120002"/>
						<display value="YATES, Kester"/>
					</actor>
				</practitioner>
				<explanation>
					<reasonNotGiven>
						<coding>
							<system value="http://snomed.info/sct"/>
							<code value="1324761000000100"/>
							<display value="SARS-CoV-2 (severe acute respiratory syndrome coronavirus 2) immunisation course contraindicated"/>
						</coding>
					</reasonNotGiven>
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
							<code value="nocount"/>
							<display value="Does not Count"/>
						</coding>
					</doseStatus>
				</vaccinationProtocol>
			</Immunization>
		</resource>
	</entry>
	<!-- Patient associated with the Immunization. -->
	<entry>
		<fullUrl value="urn:uuid:cd8374e0-2e34-11eb-adc1-0242ac120002"/>
		<resource>
			<Patient>
				<id value="cd8374e0-2e34-11eb-adc1-0242ac120002"/>
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
					<value value="9046556581"/>
				</identifier>
				<name>
					<use value="official"/>
					<family value="WINTERS"/>
					<given value="Hettie"/>
				</name>
				<gender value="female"/>
				<birthDate value="1963-08-22"/>
				<address>
					<use value="home"/>
					<type value="both"/>
					<postalCode value="HX2 6LF"/>
				</address>
				<generalPractitioner>
					<reference value="urn:uuid:cd838296-2e34-11eb-adc1-0242ac120002"/>
				</generalPractitioner>
			</Patient>
		</resource>
	</entry>
	<!-- Practitioner performing the Immunization -->
	<entry>
		<fullUrl value="urn:uuid:cd838160-2e34-11eb-adc1-0242ac120002"/>
		<resource>
			<Practitioner>
				<id value="cd838160-2e34-11eb-adc1-0242ac120002"/>
				<meta>
					<profile value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1"/>
				</meta>
				<identifier>
					<system value="https://fhir.hl7.org.uk/Id/gphc-number"/>
					<value value="2036622"/>
				</identifier>
				<name>
					<family value="YATES"/>
					<given value="Kester"/>
				</name>
			</Practitioner>
		</resource>
	</entry>
	<!-- Encounter and Immunization serviceProvider -->
	<entry>
		<fullUrl value="urn:uuid:cd8386ce-2e34-11eb-adc1-0242ac120002"/>
		<resource>
			<Organization>
				<id value="cd8386ce-2e34-11eb-adc1-0242ac120002"/>
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
	<!-- Practitioner Role -->
	<entry>
		<fullUrl value="urn:uuid:cd838426-2e34-11eb-adc1-0242ac120002"/>
		<resource>
			<PractitionerRole>
				<id value="cd838426-2e34-11eb-adc1-0242ac120002"/>
				<meta>
					<profile value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-PractitionerRole-1"/>
				</meta>
				<practitioner>
					<reference value="urn:uuid:cd838160-2e34-11eb-adc1-0242ac120002"/>
				</practitioner>
				<code>
					<coding>
						<system value="https://fhir.hl7.org.uk/STU3/CodeSystem/CareConnect-SDSJobRoleName-1"/>
						<code value="R1290"/>
						<display value="Pharmacist"/>
					</coding>
				</code>
			</PractitionerRole>
		</resource>
	</entry>
</Bundle>
<!--</xml>-->
```
<a href="engage_hettie_winters_imms.html">Back to top of page</a>
## Example Instance of Scenario - ITK Wrapper ##

{% include note.html content="These examples have not been clinically assured against Digital Medicines use cases.<br/>Examples are illustrative only." %}

```
<!--<xml>-->
<!-- This xml example is for illustrative purposes only and has not been clinically verified. -->
<Bundle xmlns="http://hl7.org/fhir">
	<id value="cd836a72-2e34-11eb-adc1-0242ac120002"/>
	<meta>
		<profile value="https://fhir.nhs.uk/STU3/StructureDefinition/ITK-Message-Bundle-1"/>
	</meta>
	<identifier>
		<value value="cd836cca-2e34-11eb-adc1-0242ac120002"/>
	</identifier>
	<type value="message"/>
	<entry>
		<fullUrl value="urn:uuid:cd836dc4-2e34-11eb-adc1-0242ac120002"/>
		<resource>
			<MessageHeader>
				<id value="cd836dc4-2e34-11eb-adc1-0242ac120002"/>
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
					<reference value="urn:uuid:cd83710c-2e34-11eb-adc1-0242ac120002"/>
				</sender>
				<timestamp value="2020-12-01T20:00:00+00:00"/>
				<source>
					<endpoint value="NOROT003"/>
				</source>
				<focus>
					<reference value="urn:uuid:cd8371de-2e34-11eb-adc1-0242ac120002"/>
				</focus>
			</MessageHeader>
		</resource>
	</entry>
	<!-- Sender Organisation -->
	<entry>
		<fullUrl value="urn:uuid:cd83710c-2e34-11eb-adc1-0242ac120002"/>
		<resource>
			<Organization>
				<id value="cd83710c-2e34-11eb-adc1-0242ac120002"/>
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
		<fullUrl value="urn:uuid:cd8371de-2e34-11eb-adc1-0242ac120002"/>
		<resource>
			<!-- This xml example is for illustrative purposes only and has not been clinically verified. -->
			<Bundle>
				<id value="cd8371de-2e34-11eb-adc1-0242ac120002"/>
				<meta>
					<lastUpdated value="2020-12-10T16:00:00+00:00"/>
					<profile value="https://fhir.nhs.uk/STU3/StructureDefinition/ITK-Document-Bundle-1"/>
				</meta>
				<identifier>
					<value value="cd83729c-2e34-11eb-adc1-0242ac120002"/>
				</identifier>
				<type value="document"/>
				<!-- Pharmacy Vaccinations Notification Document -->
				<entry>
					<fullUrl value="urn:uuid:cd837364-2e34-11eb-adc1-0242ac120002"/>
					<resource>
						<!-- A resource carrying a set of vaccination related information about the patient -->
						<Composition>
							<id value="cd837364-2e34-11eb-adc1-0242ac120002"/>
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
								<value value="cd837422-2e34-11eb-adc1-0242ac120002"/>
							</identifier>
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
								<reference value="urn:uuid:cd8374e0-2e34-11eb-adc1-0242ac120002"/>
							</subject>
							<!-- Reference to the clinical encounter or type of care this documentation is associated with. -->
							<encounter>
								<reference value="urn:uuid:857ad2f4-2fc1-11eb-adc1-0242ac120002"/>
							</encounter>
							<!-- The composition editing time, when the composition was last logically changed by the author. -->
							<date value="2020-12-01T16:00:00+00:00"/>
							<!-- Identifies who is responsible for the information in the composition, not necessarily who typed it in -->
							<author>
								<reference value="urn:uuid:cd838160-2e34-11eb-adc1-0242ac120002"/>
							</author>
							<title value="COVID-19 Immunization Record"/>
							<!-- Identifies the organization responsible for ongoing maintenance of and access to the composition/document information. -->
							<custodian>
								<reference value="urn:uuid:cd838296-2e34-11eb-adc1-0242ac120002"/>
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
													<td>01-Dec-2020 15:37</td>
												</tr>
											</tbody>
										</table>
									</div>
								</text>
								<!-- Reference to Encounter resource as the source of information for this section -->
								<entry>
									<reference value="urn:uuid:857ad2f4-2fc1-11eb-adc1-0242ac120002"/>
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
									<reference value="urn:uuid:cd838296-2e34-11eb-adc1-0242ac120002"/>
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
													<td>Vaccine procedure: SARS-CoV-2 (severe acute respiratory syndrome coronavirus 2) vaccination first dose not given.</td>
													<td>Reason not given: SARS-CoV-2 (severe acute respiratory syndrome coronavirus 2) immunisation course contraindicated</td>
												</tr>
												<tr>
													<td>Practitioner: Kester Yates</td>
													<td>GPhC identifier: 2036622</td>
													<td>Date Time: 01-Dec-2020 15:37</td>
												</tr>
											</tbody>
										</table>
									</div>
								</text>
								<!-- Reference to the Immunization resource entry -->
								<entry>
									<reference value="urn:uuid:cd838368-2e34-11eb-adc1-0242ac120002"/>
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
														<p>Given Name: Hettie</p>
														<p>Family Name: Winters</p>
													</td>
												</tr>
												<tr>
													<th>Date of birth</th>
													<td>23 March 1963</td>
												</tr>
												<tr>
													<th>Sex</th>
													<td>Female</td>
												</tr>
												<tr>
													<th>NHS number</th>
													<td>9046556581</td>
												</tr>
												<tr>
													<th>Patient address</th>
													<td>
														<p>Post Code: HX2 6LF</p>
													</td>
												</tr>
											</tbody>
										</table>
									</div>
								</text>
								<!-- Reference to the Patient resource entry -->
								<entry>
									<reference value="urn:uuid:cd8374e0-2e34-11eb-adc1-0242ac120002"/>
								</entry>
							</section>
						</Composition>
					</resource>
				</entry>
				<!-- Encounter resource entry -->
				<entry>
					<fullUrl value="urn:uuid:857ad2f4-2fc1-11eb-adc1-0242ac120002"/>
					<resource>
						<!-- Encounter resource providing context for the Immunization -->
						<Encounter>
							<id value="857ad2f4-2fc1-11eb-adc1-0242ac120002"/>
							<meta>
								<profile value="https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Encounter-1"/>
							</meta>
							<status value="finished"/>
							<subject>
								<reference value="urn:uuid:cd8374e0-2e34-11eb-adc1-0242ac120002"/>
								<display value="WINTERS, Hettie"/>
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
									<reference value="urn:uuid:cd838160-2e34-11eb-adc1-0242ac120002"/>
									<display value="YATES, Kester"/>
								</individual>
							</participant>
							<period>
								<start value="2020-01-20T15:37:10+01:00"/>
							</period>
							<serviceProvider>
								<reference value="urn:uuid:cd8386ce-2e34-11eb-adc1-0242ac120002"/>
							</serviceProvider>
						</Encounter>
					</resource>
				</entry>
				<!-- Patient's registered GP Practice. -->
				<entry>
					<fullUrl value="urn:uuid:cd838296-2e34-11eb-adc1-0242ac120002"/>
					<resource>
						<Organization>
							<id value="cd838296-2e34-11eb-adc1-0242ac120002"/>
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
					<fullUrl value="urn:uuid:cd838368-2e34-11eb-adc1-0242ac120002"/>
					<resource>
						<Immunization>
							<id value="cd838368-2e34-11eb-adc1-0242ac120002"/>
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
										<code value="1324781000000109"/>
										<display value="Severe acute respiratory syndrome coronavirus 2 vaccination first dose not given (situation)"/>
									</coding>
								</valueCodeableConcept>
							</extension>
							<identifier>
								<system value="https://tools.ietf.org/html/rfc4122"/>
								<value value="91df61b6-2da2-11eb-adc1-0242ac120002"/>
							</identifier>
							<status value="completed"/>
							<notGiven value="true"/>
							<vaccineCode>
								<coding>
									<system value="http://snomed.info/sct"/>
									<code value="39114911000001105"/>
									<display value="Talent 0.5ml dose solution for injection multidose vials (Secretary of State for Health)"/>
								</coding>
							</vaccineCode>
							<patient>
								<reference value="urn:uuid:cd8374e0-2e34-11eb-adc1-0242ac120002"/>
								<display value="WINTERS, Hettie"/>
							</patient>
							<!-- Encounter reference for Immunization -->
							<encounter>
								<reference value="urn:uuid:857ad2f4-2fc1-11eb-adc1-0242ac120002"/>
							</encounter>
							<date value="2020-01-20T15:37:10+01:00"/>
							<primarySource value="true"/>
							<practitioner>
								<role>
									<coding>
										<system value="http://hl7.org/fhir/v2/0443"/>
										<code value="AP"/>
										<display value="Administering Provider"/>
									</coding>
								</role>
								<actor>
									<reference value="urn:uuid:cd838160-2e34-11eb-adc1-0242ac120002"/>
									<display value="YATES, Kester"/>
								</actor>
							</practitioner>
							<explanation>
								<reasonNotGiven>
									<coding>
										<system value="http://snomed.info/sct"/>
										<code value="1324761000000100"/>
										<display value="SARS-CoV-2 (severe acute respiratory syndrome coronavirus 2) immunisation course contraindicated"/>
									</coding>
								</reasonNotGiven>
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
										<code value="nocount"/>
										<display value="Does not Count"/>
									</coding>
								</doseStatus>
							</vaccinationProtocol>
						</Immunization>
					</resource>
				</entry>
				<!-- Patient associated with the Immunization. -->
				<entry>
					<fullUrl value="urn:uuid:cd8374e0-2e34-11eb-adc1-0242ac120002"/>
					<resource>
						<Patient>
							<id value="cd8374e0-2e34-11eb-adc1-0242ac120002"/>
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
								<value value="9046556581"/>
							</identifier>
							<name>
								<use value="official"/>
								<family value="WINTERS"/>
								<given value="Hettie"/>
							</name>
							<gender value="female"/>
							<birthDate value="1963-08-22"/>
							<address>
								<use value="home"/>
								<type value="both"/>
								<postalCode value="HX2 6LF"/>
							</address>
							<generalPractitioner>
								<reference value="urn:uuid:cd838296-2e34-11eb-adc1-0242ac120002"/>
							</generalPractitioner>
						</Patient>
					</resource>
				</entry>
				<!-- Practitioner performing the Immunization -->
				<entry>
					<fullUrl value="urn:uuid:cd838160-2e34-11eb-adc1-0242ac120002"/>
					<resource>
						<Practitioner>
							<id value="cd838160-2e34-11eb-adc1-0242ac120002"/>
							<meta>
								<profile value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1"/>
							</meta>
							<identifier>
								<system value="https://fhir.hl7.org.uk/Id/gphc-number"/>
								<value value="2036622"/>
							</identifier>
							<name>
								<family value="YATES"/>
								<given value="Kester"/>
							</name>
						</Practitioner>
					</resource>
				</entry>
				<!-- Encounter and Immunization serviceProvider -->
				<entry>
					<fullUrl value="urn:uuid:cd8386ce-2e34-11eb-adc1-0242ac120002"/>
					<resource>
						<Organization>
							<id value="cd8386ce-2e34-11eb-adc1-0242ac120002"/>
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
				<!-- Practitioner Role -->
				<entry>
					<fullUrl value="urn:uuid:cd838426-2e34-11eb-adc1-0242ac120002"/>
					<resource>
						<PractitionerRole>
							<id value="cd838426-2e34-11eb-adc1-0242ac120002"/>
							<meta>
								<profile value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-PractitionerRole-1"/>
							</meta>
							<practitioner>
								<reference value="urn:uuid:cd838160-2e34-11eb-adc1-0242ac120002"/>
							</practitioner>
							<code>
								<coding>
									<system value="https://fhir.hl7.org.uk/STU3/CodeSystem/CareConnect-SDSJobRoleName-1"/>
									<code value="R1290"/>
									<display value="Pharmacist"/>
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
<a href="engage_hettie_winters_imms.html">Back to top of page</a>
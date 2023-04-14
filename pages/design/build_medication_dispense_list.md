---
title: Medication Dispense List
keywords: design, build,
tags: [design]
sidebar: foundations_sidebar
permalink: build_medication_dispense_list.html
summary: "Constructing a medication dispense list"
---

## Overview ##

This section details the design approach using FHIR Resources to support the PRSB heading model for Medications and medical devices.

## Resources Used for Profile Design ##

The FHIR Resources are profiled to create the medication list as below:

- **[CareConnect-ITK-MedicationDispense-List-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-MedicationDispense-List-1)** - An NHS Digital Profile for recording a snapshot of the list of Medications dispensed for the patient.
- **[CareConnect-ITK-MedicationDispense-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-MedicationDispense-1)** - An NHS Digital Profile derived from the CareConnect MedicationDispense Profile. Indicates that a medication product is to be or has been dispensed for a named person/patient. This includes a description of the medication product (supply) provided and the instructions for administering the medication. 
- **[CareConnect-ITK-Medication-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Medication-1)** - An NHS Digital Profile for medication. The Medication Resource is primarily used for the identification and definition of a medication.

### List ###

This Resource acts as a container for the medication dispense items. The following is an example of the elements which can be used:

- identifier - uniquely identifies this list of medication (UUID)
- code - the type of list (SNOMED CT concept)
- status - should only be "current"
- mode - should only be "snapshot"
- title - descriptive name for the list
- subject - a reference to the patient whose medication list this is
- encounter - a reference to the context in which the list was created (the pharmacy visit)
- date - when the list was prepared
- source - who or what defined the list
- entry - a reference to the MedicationDispense Resource entry or entries

### MedicationDispense ###

The main purpose of the MedicationDispense resource is to record that a medication product is to be or has been dispensed for a named patient by a named Practitioner. The following elements are business required or optional but recommended for a successful implementation.

- identifier - REQUIRED - uniquely identifies this medication dispense (UUID)
- status - REQUIRED - should always be completed
- medicationReference (name) - MANDATORY - a reference to the medication which was dispensed
- medicationReference.Medication.form - REQUIRED - the form of the medication e.g. capsule, drops, tablet, lotion etc.
- subject - REQUIRED - a reference to the patient
- context - OPTIONAL - reference to the encounter in which the medication was dispensed (the pharmacy visit)
- performer - REQUIRED - who / what dispensed the medication
- type - REQUIRED - the type dispense/supply (SNOMED CT concept)
- quantity - MANDATORY - amount dispensed expressed as it's unit form dose, e.g. tablet, ml, gram
- daysSupply - MANDATORY - amount supplied expressed as a number of days
- whenHandedOver - REQUIRED - the date/time on which the medication was supplied to the patient
- dosageInstruction.route - REQUIRED - the route by which the medication is administered e.g. oral, IM, IV
- dosageInstruction.site - REQUIRED - the anatomical site at which the medication is to be administered
- dosageInstruction.doseQuantity - REQUIRED - a structural representation of dose amount, e.g. 20mg or 2 tablets
- dosageInstruction.timing - REQUIRED - a structural, computable representation of dose timing
- dosageInstruction.text - MANDATORY - the entire medication dosage and administration directions including dose quantity and medication frequency and optionally duration e.g. "1 tablet at night" or "2mg at 10pm"
- dosageInstruction.additionalInstructions - REQUIRED - additional instructions, requirements for adherence support, e.g. compliance aids, prompts and packaging requirements
Note: any matters identified during discussion should be documented in the Composition.section.text
Note: Indication should be recorded as free text in the Composition.section.text

### Medication ###

The Medication Resource allows for medications to be characterized by the form of the drug and the ingredient (or ingredients), as well as how it is packaged. The medication will include the ingredient(s) and their strength(s) and the package can include the amount (for example, number of tablets, volume, etc.) that is contained in a particular container (for example, 100 capsules of Amoxicillin 500mg per bottle). The following is an example of the elements that can be used:

- code - a SNOMED CT Concept that identifies this medication
- form - powder, tablets, capsule etc SNOMED CT form concepts 
 
## How the Medication Dispense List is Constructed ##
The diagram below shows the Resources used and the relationship between the Resources.

<img src="images/build/medicationdispense_basic_structure.png" style="width:100%;max-width: 100%;">

## MedicationDispense Resource ##

Provides further details of bindings and references used in the medication dispense to the patient.

### status ###

Should contain the value "completed".

### type ###

This should be a SNOMED CT Concept to identify the nature of the dispensing or supply event:
- 1218611000000102 Urgent supply of prescription items by community pharmacy
- 1577041000000109 Community Pharmacist Consultation Service for minor illness

### quantity ###

The FHIR element <b>Extension-CareConnect-MedicationQuantityText-1</b> is used to carry the quantity dispensed as a text string. This should be a concatenation of the numeric quantity dispensed and the unit of measure, separated by a single whitespace, for example "14 tablet".

The quantity should also be structured using the SimpleQuantity structure. By default use UCUM units of measure (system uri “http://unitsofmeasure.org”), for example “gram” or “milliliter”.

Where a UCUM unit of measure is not defined, use a SNOMED CT Concept unit of measure (system uri “http://snomed.info/sct”). Examples of when a SNOMED CT unit of measure would be required include “tablet”, “capsule” or “ampule”. 
 
Units of measure, where UCUM is not available, are contained within the hierarchy as descendants of [767524001 Unit of measure](https://termbrowser.nhs.uk/?perspective=full&conceptId1=767524001&edition=uk-edition).  

All units of measure should be expressed in the singular, for example "tablet" and not "tablets".

### daysSupply ###

The quantity supplied expressed as a number of days using the SimpleQuantity structure.

The `daysSupply.value` shall be the number of days.

The `daysSupply.unit` of measure shall be `day`.

The `daysSupply.system` uri shall be `http://unitsofmeasure.org`.

The `daysSupply.code` shall be `d`.

### performer ###

Who dispensed the medication if available to the sender.

### references ###

The references to the following must be carried:
- medicationReference
- subject (patient)
- context (encounter) 

The reference "display" element should be included and populated as follows;
- for medicationReference.display, the description of the medication
- for subject.display, the full name of the patient
- for context, display should be omitted

## Medication Resource ##

This section gives guidance of the bindings used in the Medication Resource

### medication.code ###

This FHIR element is mapped to the PRSB medication name.

Constraint: MedicationName. An AMP or AMPP code from the dm+d terminology. 

<table style="width:100%;max-width: 100%;">
<tr><td>AMP NHS dm+d actual medicinal product (DD4C) 999000541000001108</td></tr> 
<tr><td>AMPP NHS dm+d actual medicinal product pack (DD4C) 999000551000001106</td></tr>
</table> 

The above as a SNOMED CT expression. 

<table style="width:100%;max-width: 100%;">
<tr><td>OR ^999000541000001108</td></tr> 
<tr><td>OR ^999000551000001106)</td></tr> 
<tr><td></td></tr> 
<tr><td>OR with preferred terms</td></tr> 
<tr><td>(^999000541000001108 |National Health Service dictionary of medicines and devices actual medicinal product simple reference set|</td></tr> 
<tr><td>OR ^999000551000001106 |National Health Service dictionary of medicines and devices actual medicinal product pack simple reference set|</td></tr> 
</table>

### medication.form ###

The medication form is included on the Medication profile. 

AMP and AMPP concepts are pre-coordinated and include a form so do not need to be repeated in this element (but may be sent).

Constraint: DrugDoseForm. SNOMED CT CfH DoseForm termset. Constraint binding: [SNOMED CT]subset=CfH  DoseForm (refset 999000781000001107)

The above as a SNOMED CT expression

<table style="width:100%;max-width: 100%;">
<tr><td>^999000781000001107 |NHS dm+d (dictionary of medicines and devices) dose form simple reference set|</td></tr>
</table>

## Medication Dispense List Examples ##

**Medication Dispense List**

{% include note.html content="These examples have not been clinically assured against Digital Medicines use cases.<br/>Examples are illustrative only." %}

```
<!--<xml>-->
<List xmlns="http://hl7.org/fhir">
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
			<reference value="urn:uuid:42ac049c-87ca-4e33-93ad-987167422b01"/>
		</item>
	</entry>
</List>
<!--</xml>-->
```

**Medication Dispense**

{% include note.html content="These examples have not been clinically assured against Digital Medicines use cases.<br/>Examples are illustrative only." %}

```
<!--<xml>-->
<MedicationDispense xmlns="http://hl7.org/fhir">
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
			<systemvalue="http://snomed.info/sct"/>   
			<codevalue="1218611000000102"/>   
			<displayvalue="Urgent supply of prescription items by community pharmacy"/>
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
		<text value="As previously advised"/>
	</dosageInstruction>
</MedicationDispense>
<!--</xml>-->
```

**Medication**


{% include note.html content="These examples have not been clinically assured against Digital Medicines use cases.<br/>Examples are illustrative only." %}

```
<!--<xml>-->
<Medication xmlns="http://hl7.org/fhir">
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
<!--</xml>-->
```

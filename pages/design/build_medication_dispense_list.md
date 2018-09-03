---
title: Medication Dispense List
keywords: design, build,
tags: [design]
sidebar: foundations_sidebar
permalink: build_medication_dispense_list.html
summary: "Constructing a medication dispense list"
---

{% include important.html content="The resources referenced in this section are the FHIR base resources which will be constrained by the profiles used by Digital Medicines, the profiles should be referred to for the actual allowable structure and content." %}

## Overview ##
This section details the design approach using FHIR Resources to support the PRSB heading model for Medications and medical devices.

## Resources Used for Profile Design ##
The FHIR Resources are profiled to create the medication list as below:

- **[CareConnect-ITK-MedicationDispense-List-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-MedicationDispense-List-1)** - An NHS Digital Profile for recording a snapshot of the list of Medications dispensed for the patient.
- **[CareConnect-ITK-MedicationDispense-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-MedicationDispense-1)** - An NHS Digital Profile derived from the CareConnect MedicationDispense Profile. Indicates that a medication product is to be or has been dispensed for a named person/patient. This includes a description of the medication product (supply) provided and the instructions for administering the medication. 
- **[CareConnect-ITK-Medication-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Medication-1)** - An NHS Digital Profile for medication. The Medication Resource is primarily used for the identification and definition of a medication.

## List ##
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

## MedicationDispense ##
The main purpose of the MedicationDispense resource is to record that a medication product is to be or has been dispensed for a named patient by a named Practitioner. The following is an example of the elements can be used:

- identifier - uniquely identifies this medication dispense (UUID)
- status - should always be completed
- medication - a reference to the medication which was dispensed
- subject - a reference to the patient
- context - a reference to the encounter in which the medication was dispensed (the pharmacy visit)
- performer - who / what dispensed the medication
- type - should always be "emergency-supply"
- quantity - how much was dispensed 
- whenHandedOver - the date/time on which the medication was supplied to the patient
- dosageInstruction - how the medication is to be used by the patient or administered by the caregiver

## Medication ##
The Medication Resource allows for medications to be characterized by the form of the drug and the ingredient (or ingredients), as well as how it is packaged. The medication will include the ingredient(s) and their strength(s) and the package can include the amount (for example, number of tablets, volume, etc.) that is contained in a particular container (for example, 100 capsules of Amoxicillin 500mg per bottle). The following is an example of the elements that can be used:

- code - a SNOMED CT Concept that identifies this medication
- form - powder, tablets, capsule etc SNOMED CT form concepts 

 
## How the Medication Dispense List is Constructed ##
The diagram below shows the Resources used and the relationship between the Resources.

<img src="images/build/medicationdispense_basic_structure.png" style="width:100%;max-width: 100%;">


## MedicationDispense Resource ##

This Resource provides details of medication that has been dispensed to the patient.

## status ##

This should contain the value "completed".

## type ##

This should contain the value "emergency-supply".

## quantity ##

This is mandated when the dispense resource is used. The FHIR element <b>Extension-CareConnect-MedicationQuantityText-1</b> is used to carry the amount dispensed as a text string. Where supported the quantity may be structured, but there is no guidance at this time.

## performer ##

Who dispensed the medication if available to the sender.

## References ##
The references to the following must be carried:

- medication
- subject (patient)
- context (encounter) 


## Medication Resource ##
This section gives guidance of the use of the Medication Resource

## medication.code ##
This FHIR element is mapped to the PRSB medication name

constraint: MedicationName.   Any AMP/VMP/VTM/AMPP/VMPP subsets from the dm+d terminology. 

<table style="width:100%;max-width: 100%;">
<tr><td>VTM NHS dm+d virtual therapeutic moiety (DD4C) 999000581000001102</td></tr> 
<tr><td>VMP NHS dm+d virtual medicinal product (DD4C) 999000561000001109</td></tr> 
<tr><td>VMPP NHS dm+d virtual medicinal product pack (DD4C) 999000571000001104</td></tr> 
<tr><td>AMP NHS dm+d actual medicinal product (DD4C) 999000541000001108</td></tr> 
<tr><td>AMPP NHS dm+d actual medicinal product pack (DD4C) 999000551000001106</td></tr>
</table> 

The above as a SNOMED CT expression. 

<table style="width:100%;max-width: 100%;">
<tr><td>(^999000581000001102</td></tr> 
<tr><td>OR ^999000561000001109</td></tr> 
<tr><td>OR ^999000571000001104</td></tr> 
<tr><td>OR ^999000541000001108</td></tr> 
<tr><td>OR ^999000551000001106)</td></tr> 
<tr><td></td></tr> 
<tr><td>OR with preferred terms</td></tr> 
<tr><td>(^999000541000001108 |National Health Service dictionary of medicines and devices actual medicinal product simple reference set|</td></tr> 
<tr><td>OR ^999000551000001106 |National Health Service dictionary of medicines and devices actual medicinal product pack simple reference set|</td></tr> 
<tr><td>OR ^999000561000001109 |National Health Service dictionary of medicines and devices virtual medicinal product simple reference set|</td></tr> 
<tr><td>OR ^999000571000001104 |National Health Service dictionary of medicines and devices virtual medicinal product pack simple reference set|</td></tr> 
<tr><td>OR ^999000581000001102 |National Health Service dictionary of medicines and devices virtual therapeutic moiety simple reference set|)</td></tr> 
</table>


## medication.form ##
This form is on the medication profile. Where VTM has form specified (coded) it goes here.
AMP & VMP don't need separate Form (it is optional to populate). For VTM the form could be in MedicationStatement.dosage.text (as it would be part of a dosage string) i.e. not a separately specified code.

Constraint: DrugDoseForm. SNOMED CT CfH DoseForm termset. Constraint binding: [SNOMED CT]subset=CfH  DoseForm (refset 999000781000001107)

The above as a SNOMED CT expression

<table style="width:100%;max-width: 100%;">
<tr><td>^999000781000001107 |NHS dm+d (dictionary of medicines and devices) dose form simple reference set|</td></tr>
</table>



## Medication Dispense List Examples ##

**Medication Dispense List**

<script src="https://gist.github.com/IOPS-DEV/7ca6ef33a6fb2a6b72eae6532655ec88.js"></script>

**Medication Dispense**

<script src="https://gist.github.com/IOPS-DEV/c697d4d5c06f3419147190361e0cd951.js"></script>

**Medication**

<script src="https://gist.github.com/IOPS-DEV/f7f62f5d5f116efc17a130c044e0a792.js"></script>




 




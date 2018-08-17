---
title: Medication List
keywords: design, build,
tags: [design]
sidebar: foundations_sidebar
permalink: build_medication_lists.html
summary: "Constructing a medication list"
---

{% include important.html content="The resources referenced in this section are the FHIR base resources which will be constrained by the profiles used by eDischarge, the profiles should be referred to for the actual allowable structure and content." %}

## Overview ##
This section details the design approach using FHIR Resources to support the PRSB heading model for medication and devices.


## Medication Snapshot ##
The medication list is a “Snapshot” of the medication at a point in time (for example on discharge from hospital). It is not a master list of the patient’s medications. Other lists of medications for the patient may exist on other systems. For Transfer of Care Documents there will a potentially be two lists one for active medication and one for discontinued medication. There are two entries in the FHIR Composition.section.text element:

- medication item entries which map to the Medication Statements in the active list 
- Medication discontinued entries which map to the Medication Statements in the discontinued list

## Resources Used for Profile Design ##
The FHIR Resources are profiled to create the medication list as below:

- **[CareConnect-ITK-Medication-List-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Medication-List-1)** - An NHS Digital Profile for recording a snapshot of the list of Medications for the patient.
- **[CareConnect-ITK-MedicationStatement-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-MedicationStatement-1)** - An NHS Digital Profile for medication statements. The MedicationStatement Resource is a record of a medication that is being consumed by a patient.
- **[CareConnect-ITK-Medication-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Medication-1)** - An NHS Digital Profile for medication. The Medication Resource is primarily used for the identification and definition of a medication.
- **[CareConnect-ITK-MedicationDispense-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-MedicationDispense-1)** - An NHS Digital Profile derived from the CareConnect MedicationDispense Profile. Indicates that a medication product is to be or has been dispensed for a named person/patient. This includes a description of the medication product (supply) provided and the instructions for administering the medication. 

## List ##
This Resource acts as a container for the medication items. The following is an example of the elements which can be used:

- identifier - uniquely identifies this list of medication (UUID)
- code - the type of list (SNOMED CT concept for "active medication" or "discontinued medication")
- status - should only be "current"
- mode - should only be "snapshot"
- title - descriptive name for the list
- subject - a reference to the patient whose medication list this is
- encounter - a reference to the context in which the list was created (the inpatient stay)
- date - when the list was prepared
- source - who or what defined the list
- entry - a reference to the MedicationStatement Resource entry or entries
- flag - **MUST  NOT be used for Transfer of Care**
- emptyReason - **MUST  NOT be used for Transfer of Care** if list is empty do not send a List.


## MedicationStatement ##
A record of a medication that is being consumed or has been consumed by a patient. The following is an example of the elements that can be used:

- identifier - uniquely identifies this medication statement (UUID)
- clinicalStatus - should always be active
- category - should be inpatient
- partOf - A reference to the MedicationDispense Resource used to carry the quantity that was dispensed (for example TTO after a hospital provider spell) 
- medication - the medication coded (a SNOMED CT Concept that identifies this medication), this is done by reference to the Medication Resource which details the medication. 
- effective - the date/time or interval when the medication was taken
- dateAsserted - When the statement was asserted defaults to composition date
- informationSource - Person or organization that provided the information about the taking of this medication, assumed to be composition author
- reasonCode - Reason for why the medication is being/was taken
- subject - The Patient
- reasonReference - a reference to the Condition Resource that supports why the medication is being/was taken
- medicationReference - a reference to the Medication Resource
- taken - default to "unknown" or "na" if the taken element is not applicable for the medication or device
- reasonNotTaken - **MUST NOT be used for Transfer of Care** 
- dosage - Details of how medication is/was taken or should be taken

## Medication ##
The Medication Resource allows for medications to be characterized by the form of the drug and the ingredient (or ingredients), as well as how it is packaged. The medication will include the ingredient(s) and their strength(s) and the package can include the amount (for example, number of tablets, volume, etc.) that is contained in a particular container (for example, 100 capsules of Amoxicillin 500mg per bottle). The following is an example of the elements that can be used:

- code - a SNOMED CT Concept that identifies this medication
- form - powder, tablets, capsule etc SNOMED CT form concepts 

## MedicationDispense ##
The main purpose of the MedicationDispense resource is for Medication that is to record the amount of medication which has supplied to the patient. For example TTOs(to take outs). The following is an example of the elements can be used:

- identifier - uniquely identifies this medication dispense (UUID)
- status - for ToC should always be completed
- category - inpatient or outpatient 
- medication - a reference to the medication which was dispensed
- subject - a reference to the patient
- performer - who / what dispensed the medication
- quantity - How much was dispensed
 
## How the Medication List is Constructed ##
The medication record is constructed as two lists. The diagram below shows the Resources used and the relationship between the Resources.

<img src="images/build/medication_basic_structure.png" style="width:100%;max-width: 100%;">



## MedicationStatement Resource ##

This section gives guidance of the use of the MedicationStatement Resource. Sending Systems should send as much details as they can. 

## MedicationStatement.partOf ##

This uses a reference to the MedicationDispense.quantity to indicate the amount of medication that was dispensed, for example TTO after a hospital provider spell.

## MedicationStatement.dosage.route ##
Constraint: NHS e-Prescribing route of administration subset refset 999000051000001100.
The route can be any route, and not constrained to a dm+d route for the medication. Separate products are different MedicationStatements in Primary Care if the same product have multiple route options then the routes go in the FHIR element <b>MedicationStatement.dosage.text</b>. When using routes outside the stated ValueSet, then use FHIR element <b>MedicationStatement.dosage.text</b>.

## MedicationStatement.dosage.site ##
Constraint: As per the FHIR ValueSet <a href="http://hl7.org/fhir/stu3/valueset-approach-site-codes.html">approach-site-codes</a>. Site may have similar content as Route - There may be some overlap with Route (e.g. intra ocular left eye). If no code, then use the FHIR element <b>MedicationStatement.dosage.text</b>

## MedicationStatement.dosage.method ##
This <b>MUST NOT</b> be used in Transfer of Care, carry in the FHIR element <b>Composition.section.text</b> use the FHIR <b>MedicationStatement.dosage.text</b>
Short term this should be deprecated to a text string & concatenated with the dose direction (above).

## MedicationStatement.dosage.timing ##

**MUST NOT** be used in Transfer of Care, but is captured as part of the FHIR element <b>MedicationStatement.dosage.additionalInstruction</b> string. 

## MedicationStatement.dosage.text ##
A single plain text phrase describing the entire medication dosage and administration directions, including dose quantity and medication frequency. e.g. "1 tablet at night" or "20mg at 10pm" This is the form of dosage direction text normally available from UK GP systems.

## MedicationStatement.effective[x].effectivePeriod ##

If available may be carried in the FHIR element <b>MedicationStatement.effective[x].effectivePeriod</b>.

## MedicationStatement.dosage.patientInstruction ##

Specific patient instruction may use <b>MedicationStatement.dosage.patientInstruction</b>

## MedicationStatement.status ##

The FHIR element <b>MedicationStatement.status</b> is fixed to "active" for active medication lists and "stopped" for discontinued medication lists.

## MedicationStatement.reasonCode ##
**MUST NOT** be used in Transfer of Care.

## MedicationStatement.effectiveDateTime ##
Used to indicate when the medication was discontinued or became active.

## MedicationStatement.category ##
This FHIR element should carried the value "inpatient" for Discharge Documents and "outpatient" for Outpatient Letters.

## MedicationStatement.taken ##

This FHIR element should contain a value from the FHIR ValueSet <a href="http://hl7.org/fhir/ValueSet/medication-statement-taken"> medication-statement-taken</a> to indicate whether the patient has taken the medication. For Transfer of Care the default is unk - unknown or if a value is not applicable then na - not applicable. 

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

## MedicationDispense Resource ##

This Resource provides details of medication that has been dispensed to the patient, for example TTO(To Take Outs).
For Transfer of Care only a small subset of the elements should be used.

## status ##

This should contain the value "completed".

## category ##

This should the value "inpatient" or "outpatient" as appropriate.

## quantity ##

This is mandated when the dispense resource is used. The FHIR element <b>Extension-CareConnect-MedicationQuantityText-1</b> is used to carry the amount dispensed as a text string. Where supported the quantity may be structured, but there is no guidance at this time.

## performer ##

Who dispensed the medication if available to the sender.

## References ##
The references to the following must be carried:

- medication
- subject (patient)
- context (encounter) 

## Medication List Examples ##


**The Active List** 

<script src="https://gist.github.com/IOPS-DEV/396128c150948b3de78014ad7f2b8e4e.js"></script>

**The Active MedicationStatement**

Note: example only shows one item in the list.

<script src="https://gist.github.com/IOPS-DEV/eaf5f7159b9925448d8b479177c244f3.js"></script>

**The Active Medication.**

Note: example only shows one item in the list.

<script src="https://gist.github.com/IOPS-DEV/5141e4cfc8480c8b4638d30ad03c564b.js"></script>

**Medication Dispense**

<script src="https://gist.github.com/IOPS-DEV/99af046bcbf44b43f5b675eaa9864b02.js"></script>

**Discontinued List**

<script src="https://gist.github.com/IOPS-DEV/37cb3b0cb467ea6f714cc391f990ce33.js"></script>

**The Discontinued MedicationStatement**

Note: example only shows one item in the list.

<script src="https://gist.github.com/IOPS-DEV/3c5abe367cf39391c6611a0d58952fee.js"></script>

**The Discontinued Medication** 

Note: example only shows one item in the list.

<script src="https://gist.github.com/IOPS-DEV/608bf5c9d3e200ef19f10ff1bf33244c.js"></script>




 




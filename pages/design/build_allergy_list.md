---
title: Allergy List
keywords: design, build,
tags: [design]
sidebar: foundations_sidebar
permalink: build_allergy_lists.html
summary: "Constructing an allergy list"
---

## Overview ##
This section details the design approach using FHIR Resources to support the PRSB heading model for allergies.
It is important to distinguish between two kinds of allergic reaction / adverse reaction entry in the medical record.
## Allergic Response or Adverse Reaction Event and Propensity ##
<ol>
<li>Recording an Allergic Response or Adverse Reaction to an item of medication or a substance</li>
<li>Recording a clinician’s opinion about future risk of (or propensity to) an Allergy or other Adverse Reaction if the patient is exposed to a substance.</li></ol> 

Transfer of Care only records the first type of Allergic Response or Adverse Reaction i.e. the allergic event not the propensity.

## Resources Used for Profile Design ##
The FHIR Resources are profiled to create the allergy list as below:

- **[CareConnect-ITK-Allergy-List-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Allergy-List-1)** - An NHS Digital Profile derived from the CareConnect Profile for recording a snapshot of the list of Allergies for the patient.
- **[CareConnect-ITK-AllergyIntolerance-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-AllergyIntolerance-1)** - A NHS Digital Profile derived from the CareConnect Profile for Allergies and adverse reactions. The AllergyIntolerance Resource records risk of harmful or undesirable, physiological response which is unique to an individual and associated with exposure to a substance.

## List ##
This Resource acts as a container for the allergies. The following is an example of the main elements used:

- identifier - uniquely identifies this list of allergies (UUIDs)
- code - the type of list (for example SNOMED CT concept for "ended allergy")
- status - should always be "current"
- mode - should always be "snapshot" 
- subject - a reference to the patient whose allergy list this is
- Encounter - a reference to the context in which the list was created (the inpatient stay)
- date - when the list was prepared
- source - who or what defined the list
- entry - a reference to the allergyIntolerance Resource entry

## AllergyIntolerance ##
This Resource details the actual allergy or adverse reaction. The following is an example of the main elements used: 

- identifier - uniquely identifies this allergy or adverse reaction (UUID)
- clinicalStatus - should always be active
- category - whether the allergy or adverse reaction is to food, medication etc
- criticality - low, high, unable-to-assess etc.
- code - identifies the allergy
- patient - a reference to the patient
- assertedDate  - date record was believed accurate
- asserter - the source of the information about the allergy (patient, related person, practitioner)
- lastOccurrence - when it last occurred if known
- reaction - details of the reaction

## Causative Agents ##

Guidance of the use of SNOMED CT for causative agents is as follows

Everything from the Product <b>(373873005|Pharmaceutical/biologic product(product)|)</b> hierarchy and everything from the substance <b>(105590001|substance|)</b> hierarchy. 

For pre-coordinated allergy terms use a degrade code - see below:

Degrade codes <b>(196461000000101|transfer-degraded drug allergy(record artifact)|&amp;196471000000108|transfer-degraded non-drug allergy(record artifact)|)</b> can be used if only a text representation of the allergy is known & pre coordinated allergy codes <b>(for example 213020009|egg protein allergy|)</b>.

As a SNOMED CT expression

<table style="width:100%;max-width: 100%;">
<tr><td>(&lt;&lt;105590001 |Substance|</td></tr>
<tr><td>(OR &lt;&lt;373873005 |Pharmaceutical / biologic product|</td></tr>
<tr><td>(OR &lt;&lt;716186003 |No known allergy|</td></tr>
<tr><td>(OR 196461000000101 |Transfer-degraded drug allergy|</td></tr>
<tr><td>(OR 196471000000108 |Transfer-degraded non-drug allergy|)</td></tr>
</table>

<table style="width:100%;max-width: 100%;">
<tr><td>(^999000801000001108 |Allergy Archetypes Drug Groups simple reference set|</td></tr>    
<tr><td>OR ^999000631000001100|National Health Service dictionary of medicines and devices trade family simple reference set|</td></tr>           
<tr><td>OR ^999000641000001107|National Health Service dictionary of medicines and devices trade family group simple reference set|</td></tr>             
<tr><td>OR ^999000771000001105|National Health Service dictionary of medicines and devices combination drug virtual therapeutic moiety simple reference set|</td></tr>              
<tr><td>OR ^999000561000001109|National Health Service dictionary of medicines and devices virtual medicinal product simple reference set|</td></tr>         
<tr><td>OR ^999000541000001108|National Health Service dictionary of medicines and devices actual medicinal product simple reference set|</td></tr>             
<tr><td>OR ^999000791000001109|NHS dm+d (dictionary of medicines and devices) ingredient simple reference set|</td></tr>
<tr><td>OR <<716186003 |No known allergy|</td></tr> 
<tr><td>OR 196461000000101 |Transfer-degraded drug allergy|</td></tr> 
<tr><td>OR 196471000000108 |Transfer-degraded non-drug allergy|)</td></tr>
</table>

## Severity ##

PRSB valueSet applicable for severity is as folllows:

<table style="width:100%;max-width: 100%;">
<tr><td>Mild [The reaction was mild.][SNOMED-CT::255604002] (Mild (qualifiervalue))</td></tr>
<tr><td>Moderate [The reaction was moderate.][SNOMED-CT::6736007] (Moderate (severity modifier) (qualifier value))</td></tr>
<tr><td>Severe [The reaction was severe.][SNOMED-CT::24484000] (Severe (severity modifier) (qualifier value))</td></tr> 
<tr><td>Life threatening [The reaction was life-threatening.][SNOMED-CT::442452003] (Life threatening severity (qualifier value))</td></tr>
<tr><td>Fatal [The reaction was fatal.][SNOMED-CT::399166001] (Fatal (qualifier value))<br/></td></tr>
</table>  

<table style="width:100%;max-width: 100%;">
<tr><td><b>Important note: reaction.severity</b> is a required terminology binding in FHIR with values (mild | moderate | severe)</td></tr>
<tr><td>"Life threatening" and "Fatal" cannot currently be mapped.</td></tr>
</table>

As SNOMED CT Expression but see note above on not using 'life threatening' or 'Fatal':

<table style="width:100%;max-width: 100%;">
<tr><td>(255604002 |Mild|</td></tr>
<tr><td>OR 6736007 |Moderate|</td></tr>
<tr><td>OR 24484000 |Severe|</td></tr>
<tr><td>OR 399166001 |Fatal|</td></tr>
<tr><td>442452003 |Life threatening severity|)</td></tr>
</Table>


## Certainty ##

PRSB valueSet applicable for certainty is as follows:

<table style="width:100%;max-width: 100%;">
<tr><td>Unlikely - [The reaction is thought unlikely to have been caused by the agent.][SNOMED-CT::1491118016]</td></tr>
<tr><td>Likely - [The reaction is thought likely to have been caused by the agent.][SNOMED-CT::5961011]</td></tr>
<tr><td>Certain - [The agent is thought to be certain to have caused the reaction but this has not been confirmed by challenge testing.][SNOMED-CT::255545003] (Definite(qualifier value))</td></tr>       
<tr><td>Confirmed by challenge testing - [The  reaction to the agent has been confirmed by challenge testing or other concrete evidence.][SNOMED-CT::410605003] Confirmed present (qualifier value))</td></tr></table>

<table style="width:100%;max-width: 100%;"><tr><td>The FHIR element <b>AllergyIntolerance.verificationStatus</b> is mandatory and the ValueSet verficationStatus has a required terminology binding and uses values (unconfirmed | confirmed | refuted | entered-in-error)</td></tr>
<tr><td> the values ( refuted | entered-in-error) <b>MUST NOT</b> be used for Transfer of Care Documents.</td></tr></table>

The values Certain and Confirmed by Challenge = FHIR value "confirmed". The values Likely and Unlikely = FHIR value "unconfirmed". If <b>AllergyIntolerance.verificationStatus</b> is not known, then set to FHIR value "unconfirmed". If extra information about certainty is known, this should reported as a note. The ValueSet guidance for implementers is to default to FHIR value of "unconfirmed" for all Transfer of Care Document types.

<table style="width:100%;max-width: 100%;"><tr><td>As SNOMED Expressions (Note that 1491118016 |unlikely| and 5961011 |likely|  above are description identifiers for synonyms of concepts below)</td></tr>
<tr><td>(385434005 |Improbable diagnosis|</td></tr>
<tr><td>OR 2931005 |Probable diagnosis|</td></tr>
<tr><td>OR 255545003 |Definite|</td></tr>
<tr><td>OR 410605003 |Confirmed present|)</td></tr>
</table>

## Reaction Details ##
<b>AllergyIntolerance.reaction.manifestation</b> is a sub-element of <b>AllergyIntolerance.reaction</b>, which is optional (0..*) - so if there is no manifestation known, then don't send a <b>AllergyIntolerance.reaction</b> FHIR element.

<table style="width:100%;max-width: 100%;"><tr><td>Anything from the clinical finding hierarchy ( 404684003 | clinical finding (finding) | ). Plus the HL7 nullFlavors documented here.</td></tr></table>

The <b>AllergyIntolerance.reaction.manifestation</b> CodeableConcept ValueSet is Extensible. If you have a code, then goes in Manifestation CodeableConcept. Where no code is known (but a manifestation needs to be recorded) then populate the <b>AllergyIntolerance.reaction.manifestation</b> CodeableConcept with the value from the HL7 FHIR NullFlavor ValueSet of "UNC" - "un-encoded" and populate text of manifestation in <b>AllergyIntolerance.reaction.description</b>. When patient is asked about reaction, but doesn't know the reaction then populate the <b>AllergyIntolerance.reaction.manifestation</b> CodeableConcept with the value from the HL7 FHIR NullFlavor ValueSet of "ASKU" - "asked but unknown". When the reaction details cannot be determined/verified, then then populate the <b>AllergyIntolerance.reaction.manifestation</b> CodeableConcept with the value from the HL7 FHIR NullFlavor ValueSet of "NI" - "No Information".

## Type of Reaction ##

For the <b>AllergyIntolerance.type</b> FHIR has a required terminology binding using the values of (allergy | intolerance) - as this is a required ValueSet these values must be used.

The values "Adverse Reaction" and "Not Known" are currently not supported However adverse reaction is closer to intolerance by the FHIR definition.
An absence of AllergyIntollerance.type implies Not Known. Advice from FHIR patient care WGM is that adverse reaction should recorded under <b>AllergyIntolerance.reaction.description</b>.

## Date first experienced ##

This is mapped to the "higher level" of the FHIR element <b>AllergyIntolerance.onset[x]</b> estimated or actual date, date-time, or age when allergy or intolerance was identified. The definition of <b>AllergyIntolerance.onset[x]</b> is: Record of the date and/or time of the onset of the Reaction. The reason for mapping to higher onset is that this is the date when the reaction was experienced by the patient for the first time, the onset under reaction could be multiple. 

## Clinicalstatus ##
The FHIR element <b>AllergyIntolerance.clinicalStatus</b> for Transfer of Care Documents should if present be set to "active".

## 	AllergyIntolerance.category ##

The category of the identified substance, this may be of use to receivers and can be populated with a value from the FHIR required ValueSet <b>AllergyIntoleranceCategory</b>. 

## AllergyIntolerance.criticality ##
This FHIR element may be used to express life threatening (high) in conjunction with <b>AllergyIntolerance.severity</b> FHIR element.

## AllergyIntolerance.lastOccurrence ##
This FHIR element may be used to represents the date and/or time of the last known occurrence of a reaction event. May be populated if known.

## AllergyIntolerance.reaction.substance ##
This FHIR element <b>SHOULD NOT</b> populated for Transfer of Care Documents. 

## AllergyIntolerance.reaction.onset ##
This FHIR element may be populated if known.

## AllergyIntolerance.exposureroute ##
This FHIR element may be populated with a value from dm+d routes refset. 
As a SNOMED Expression

<table style="width:100%;max-width: 100%;"><tr><td>^999000051000001100 |ePrescribing route of administration simple reference set|</td></tr></table>

## AllergyIntolerance.reaction.note ##
This FHIR element <b>MUST NOT</b> be used and the information must where available, always be carried in the <b>Composition.section.text</b> FHIR element.

## AllergyInterolerance.ReasonEnded
This FHIR element must be supported and is to allow for clinical content for "RESOLVED" status allergies. This is where <b>AllergyIntolerance.clinicalStatus</b> FHIR element contains the value of "resolved" - FHIR definition is "A reaction to the identified substance has been clinically reassessed by testing or re-exposure and considered to be resolved."

## Allergy Snapshot ##
The allergies list is a “Snapshot” of the known allergies at a point in time (for example on discharge from hospital). It is not a master list of the patient’s allergies. Other lists of allergies for the patient may exist on other systems. 

## How the Allergy List is Constructed ##
The allergy record is constructed as a single list for Transfer of Care Documents. The diagram below shows the Resources used and relationships between the Resources.

<img src="images/build/allergy_basic_structure.png" style="width:100%;max-width: 100%;">

## Handling Negated Codes e.g. “No Known Drug allergy” ## 

When there are negated codes which are explicitly recorded by the clinician then:

- FHIR element <b>Text.Narrative</b> MUST match text of code e.g. “No known drug allergies”, PRSB guidance to be revised.
- List is NOT empty therefore the FHIR element <b>List.EmptyReason</b> not needed.
- Place negated code in the FHIR element <b>AllergyIntolerance.code</b>.

The negated codes to use are:

- 716186003 - No known allergy
- 409137002 - No known drug allergy
- 429625007 - No known food allergy

## Handling an EMPTY Allergy list (no allergies recorded in EOR) ##

**Option 1** : Fhir element <b>Text.Narrative</b> = "Information not available" this is the PRSB preferred option.

The FHIR element <b>List.EmptyReason</b> a code from the ValueSet <a href="https://fhir.hl7.org.uk/STU3/ValueSet/CareConnect-ListEmptyReasonCode-1">Care Connect List Empty Reason Code</a> which is the code "no-content-recorded".

**Option 2** : FHIR element <b>Text.Narrative</b> = displayName of the code in <b>AllergyIntolerance.code</b> and include List Resource and AllergyIntolerance Resource. The FHIR element <b>AllergyIntolerance.code</b> contains a SNOMED CT concept for example "1631000175102:Patient not asked" . The List Resource is not empty and FHIR element <b>List.EmptyReason</b> MUST NOT be populated.



## Allergy List Item Example ##

Example to show an allergy list.

**Allergy List**

<script src="https://gist.github.com/IOPS-DEV/cc4bc6b89141b22e06abc917b327f523.js"></script>


**AllergyIntolerance**

<script src="https://gist.github.com/IOPS-DEV/baa79022e1517c5dfebe3b5f1b8f178f.js"></script>


 




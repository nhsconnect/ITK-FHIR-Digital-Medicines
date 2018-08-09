---
title: Condition List
keywords: design, build,
tags: [design]
sidebar: foundations_sidebar
permalink: build_conditions.html
summary: "Constructing a condition list"
---


## Overview ##
This section details the design approach using FHIR Resources to support the PRSB heading model for a condition list. The condition Resource is referenced via the List Resource.
Implementation guidance on diagnoses from the discharge summary PRSB standard:
The discharge summary should inform the GP of the main diagnosis / diagnoses that were important during the admission (or symptom(s) if no diagnosis), including any new diagnosis that came to light during the admission.
When a diagnosis has not yet been made, the most granular clinical concept with the highest level of certainty should be recorded.  This may be a problem, symptom, sign, or test result, and may evolve over time, as a conventional diagnosis is reached.  For example, ‘dyspepsia’ may be the diagnosis when a patient first presents with indigestion, upgraded to 'gastric ulcer' when this is found at endoscopy, and 'gastric cancer' when biopsies reveal this. 
'Co-morbidities' should be recorded as separate diagnoses.  For example, dementia may be recorded as a primary diagnosis by a psycho-geriatrician, but as a co-morbidity where a patient is admitted for a hip replacement. Unconfirmed or excluded diagnoses should not be recorded in structured code.

## Resources Used for Profile Design ##
The following FHIR Resources are profiled to create the condition list.

- **[CareConnect-ITK-Condition-List-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Condition-List-1)** - A CareConnect derived NHS Digital Profile for recording a snapshot of the list of Conditions for the patient.
- **[CareConnect-ITK-Condition-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Condition-1)** -	A CareConnect derived NHS Digital Profile for conditions. The Condition Resource records detailed information about conditions (diagnoses) recognised by a clinician.

## List ##
This Resource acts as a container for the conditions. The following is an example of the main elements used:

- identifier - uniquely identifies this list of conditions (UUIDs)
- code - the type of list (for example SNOMED CT concept for "Primary Diagnosis")
- status - should always be "current"
- mode - should always be "snapshot" 
- subject - a reference to the patient whose condition list this is
- Encounter - a reference to the context in which the list was created (the inpatient stay for example)
- date - when the list was prepared
- source - who or what defined the list
- entry - a reference to the condition Resource entry

## Condition ##
This Resource is used to record detailed information about a condition, problem, diagnosis, or other event, situation, issue, or clinical concept that has risen to a level of concern. The following is an example of the elements that can be used: 

- identifier - uniquely identifies this condition (UUIDs)
- clinicalStatus - 	active, recurrence, inactive, remission, resolved etc
- category - for eDischarge this will normally be encounter-diagnosis
- code - identification of the condition, problem or diagnosis
- subject - the patient
- onset - estimated or actual date, date-time, or age
- abatement - if/when in resolution/remission
- stage - stage/grade, usually assessed formally
- evidence - supporting evidence

## Diagnosis Code ##

Handles information entered for each individual diagnosis. Confirmed diagnosis (or symptom); active diagnosis (or symptom) being treated. Should include the stage of the disease where relevant. 
The SNOMED CT concept should be from the following ref set:

<table><tr><td>&lt; 404684003 |Clinical finding|</td></tr>
<tr><td>OR &lt; 413350009 |Finding with explicit context|</td></tr>
<tr><td>OR &lt; 272379006 |Event|</td></tr></table>

For Inpatient Discharge Summary this is used in conjunction with <b>condition.category</b> with <b>encounter-diagnosis</b> as the ValueSet. 

## Condition.severity ##
<b>MUST NOT</b> be used for Transfer of Care Documents.

## Condition.bodysite ##
<b>MUST NOT</b> be used for Transfer of Care Documents.

## Condition.subject ##
A reference to the Patient Resource.

## Condition.context ##
A reference to the Encounter Resource.

## Condition.onset ##
The estimated or actual date, date-time, or age of onset which <b>MUST</b> be populated if available using one of the following sub-elements:

-  onsetDateTime
-  onsetAge
-  onsetPeriod
-  onsetRange
-  onsetString

## Condition.abatement ##
The estimated or actual date, date-time, or age of abatement which <b>MUST</b> be populated if available using one of the following sub-elements:
  
- abatementDateTime
- abatementAge
- abatementBoolean
- abatementPeriod
- abatementRange
- abatementString


## How the Condition List is Constructed ##
The condition list is constructed as a list, there may be one or more list types. The diagram below shows the Resources used and relationships between the Resources.

<img src="images/build/condition_basic_structure.png" style="width:100%;max-width: 100%;">

## Condition List Item Example ##

Example to show a condition list.

**Condition List**

<script src="https://gist.github.com/IOPS-DEV/91086467307034d0267855f23b37c503.js"></script>

**Condition**

<script src="https://gist.github.com/IOPS-DEV/ea2e64e747535e801f2451f6fec044c3.js"></script>




 




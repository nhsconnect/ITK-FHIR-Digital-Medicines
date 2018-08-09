---
title: Procedure List
keywords: design, build,
tags: [design]
sidebar: foundations_sidebar
permalink: build_procedures.html
summary: "Constructing a procedure list"
---

## Overview ##
This section details the design approach using FHIR Resources to support the PRSB heading model which use the Procedure Resource. The Procedure Resource is referenced via the List Resource.

## Resources Used for Profile Design ##
The FHIR Resources are profiled to create the procedure list as follows:

- **[CareConnect-ITK-Procedure-List-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Procedure-List-1)** - A CareConnect derived NHS Digital Profile for recording a snapshot of the list of Procedures for the patient.
- **[CareConnect-ITK-Procedure-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Procedure-1)** - A CareConnect derived NHS Digital Profile for procedures. The Procedure Resource is used to record an action that is or was performed on a patient.

## List ##
This Resource acts as a container for the procedures. The following is an example of the main elements used:

- identifier - uniquely identifies this list of procedures (UUIDs)
- code - the type of list (for example SNOMED CT concept for "requested procedures")
- status - should always be "current"
- mode - should always be "snapshot" 
- subject - a reference to the patient whose procedure list this is
- Encounter - a reference to the context in which the list was created (the inpatient stay for example)
- date - when the list was prepared
- source - who or what defined the list
- entry - a reference to the Procedure Resource entry

## Procedure ##
This Resource is used to record detailed information about a procedure. The following is an example of the elements that can be used: 

- identifier - uniquely identifies this procedure (UUIDs)
- status - completed, aborted etc 
- category - Classification of the procedure
- code - identification of the procedure
- bodySite - the body site of the procedure
- complicationDetail - details of any intra-operative complications encountered during the procedure, arising during the patient’s stay in the recovery unit or directly attributable to the procedure
- anestheticIssues - details of any adverse reaction to any anaesthetic agents including local anaesthesia. Problematic intubation, transfusion reaction, etc.
- note - any further textual comment to clarify such as statement that information is partial or incomplete
- performed - when procedure was performed
- subject - the patient
- outcome - the result of procedure

## Procedure.code ##

<table style="width:100%;max-width: 100%;">
<tr>
<td>71388002 | Procedure (procedure) | hierarcy AND  Procedure with explicit context (situation)</td></tr>
<tr><td>SCTID: 129125009 [EXTENSIBLE]</td>
</tr>
</table>

Terminology binding as a SNOMED Expression:
<table style="width:100%;max-width: 100%;">
<tr>
<td>&lt;&lt;71388002 |Procedure|</td></tr>
<tr>
<td>&lt;&lt;129125009 |Procedure with explicit context|</td>
</tr>
</table>

Procedure.code can carry combined bodySite expression:

<table style="width:100%;max-width: 100%;">
<tr>
<td>Laterality only - 448243002 | external fixation of femur | :272741003 | laterality | = 7771000 | left |</td></tr></table>

<table style="width:100%;max-width: 100%;">
<tr>
<td>Refined site and laterality  - 448243002 | external fixation of femur | :405813007 | procedure site - Direct | = 41111004 | bone structure of shaft of femur | , 272741003 | laterality | = 7771000 | left |</td></tr></table> 

## Procedure.bodySite ##

<table style="width:100%;max-width: 100%;">
<tr>
<td>&lt;&lt;442083009 |anatomical or acquired body structure|</td></tr></table> 

Note: that this includes the following two sub-hierarchies
- 91723000 anatomical structure
- 280115004 acquired body structure

So, an alternative is only:
- 91723000 anatomical structure

## Procedure.complication ##
References the condition resource.

## Procedure.anestheticIssues ##
Uses the <b>Extension-CareConnect-AnaestheticIssues-1</b> extension to either references the condition resource or carry a SNOMED CT concept to detail the anaesthetic issues the patient had.

## Procedure.note ##
Any further textual comment to clarify such as statement that information is partial or incomplete. <b>MUST</b> be repeated in the FHIR element <b>Composition.section.text</b>.

## How the Procedure List is Constructed ##
The Procedure list is constructed as a single list. The diagram below shows the Resources used and relationships between the Resources.

<img src="images/build/procedure_basic_structure.png" style="width:100%;max-width: 100%;">

## Procedure List Item Example ##

Example to show a procedure list

**Procedure List**

<script src="https://gist.github.com/IOPS-DEV/204999ed7c143fe59fa754b8f0b49bad.js"></script>

**Procedure Example**

<script src="https://gist.github.com/IOPS-DEV/8744f772a7e09e862fbb8714c1647e0a.js"></script>

 




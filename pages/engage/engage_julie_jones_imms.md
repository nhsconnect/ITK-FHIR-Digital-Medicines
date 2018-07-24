---
title: Julie Jones Pharmacy Flu Vaccination Scenario
keywords: workflow
tags: [development,fhir,profiles]
sidebar: overview_sidebar
permalink: engage_julie_jones_imms.html
summary: "Example scenario - Julie Jones Pharmacy Flu Vaccination"
---

## Background ##

Mrs Jones is a 59 year old lady who has Chronic Obstructive Pulmonary Disease (COPD). She attends her GP practice to see the nurse practitioner for her 6 month review.
- As part of the review is advised that she has the flu vaccination as she is at greater risk from flu and its complications.
- Mrs Jones agrees to make an appointment for the vaccination at reception on her way out.
- Since reception is busy she decides she will call later on.

Mrs Jones attends her local pharmacy later that day to collect her regular medicines. She notices that her local pharmacy offers the flu vaccination.
- She asks the pharmacist if she is able to have her vaccination in the pharmacy.
- The pharmacist informs her she is eligible for the flu vaccination free of charge and that she can have it now while she is waiting for her medicines.

Mrs Jones agrees to have the vaccination at the pharmacy.
During the consultation, Mrs Jones is asked by the pharmacist if she is happy for this information to be shared with her GP. Mrs Jones agrees.
The pharmacist completes the vaccination and sends the relevant information captured from Mrs Jones to her GP.

## The Pharmacy Encounter ##

The Pharmacy Encounter is documented in the [Encounter Resource](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Encounter-1)

## Named Participants ##

- Patient - **Julie Jones** - [Patient Resource](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1)
- Pharmacist (Document Author) - **Mr Eric Smith** - [Practitioner Resource](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1)
- Patient's GP (Document Recipient) - **Dr Paul Rastall** - [Practitioner Resource](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1)

## Named Organisations ##

- Pharmacy - **Overtown Pharmacy** - [Organization Resource](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- Patient's GP Practice - **MGP Medical Centre** - [Organization Resource](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)


## Example Instance of Scenario ##

<script src="https://gist.github.com/IOPS-DEV/cdf46b36dc01dc5dc52879d342f16de0.js"></script>
---
title: William Smith Pharmacy Emergency Supply Scenario
keywords: workflow
tags: [development,fhir,profiles]
sidebar: overview_sidebar
permalink: engage_william_smith_meds.html
summary: "Example scenario - William Smith Pharmacy Emergency Supply Notification"
---

## Background ##

Mr Smith is a 62 year old gentleman who has Type 2 Diabetes and Hypertension. He is on a number of regular medicines for management of his long term conditions.
Mr Smith’s wife usually orders his medication for him each month but she has recently been unwell.

It is Easter bank holiday weekend and Mr Smith suddenly realises on the Friday morning that he only has two more doses of his insulin remaining. Mr Smith calls his daughter who advises he rings NHS111 for advice as his GP practice is closed.
- When Mr Smith rings NHS111, the call handler advises him that as his insulin is a regular, repeat medication he can obtain this as an “emergency supply” from a nearby pharmacy free of charge. 
- Mr Smith is given the option to select from 2 nearby pharmacies to collect the medication from.
- Once Mr Smith selects the pharmacy he would like to go to, the call handler completes a referral and sends this to the selected pharmacy.

Mr Smith arrives at the selected pharmacy.
- The pharmacist asks Mr Smith to confirm which insulin he is on and if Mr Smith is happy for the pharmacist to confirm this by accessing his SCR.
- The pharmacist is happy that the insulin details are correct and decides to supply the medication enough to last him at least 2 weeks.
- The pharmacist asks Mr Smith if he is happy for the details of this supply to be shared with his GP. Mr Smith agrees.
- The pharmacist sends the relevant information captured from Mr Smith to his GP. 
- The pharmacist also advises Mr Smith that he should consider discussing with his GP whether he can be set up for electronic repeat dispensing if his medication regime is stable. This will mean Mr Smith does not need to order his medicines via the GP each month. The GP can simply authorise prescriptions in a batch of for example 6 months and Mr Smith simply has to collect from his usual pharmacy each month the medicines which he needs.
- Mr Smith says he will consider this and thanks the pharmacist for the emergency supply.

## The Pharmacy Encounter ##

The Pharmacy Encounter is documented in the [Encounter Resource](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Encounter-1)

## Named Participants ##

- Patient - **William Smith** - [Patient Resource](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1)
- Pharmacist (Document Author) - **Mr Eric Smith** - [Practitioner Resource](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1)
- Patient's GP (Document Recipient) - **Dr Paul Rastall** - [Practitioner Resource](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1)

## Named Organisations ##

- Pharmacy - **Overtown Pharmacy** - [Organization Resource](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- Patient's GP Practice - **MGP Medical Centre** - [Organization Resource](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)


## Example Instance of Scenario ##

<script src="https://gist.github.com/IOPS-DEV/b52d0fb8765d41e490f252f9470dd932.js"></script>
---
title: Use of Attachments
keywords: design, build
tags: [design]
sidebar: foundations_sidebar
permalink: build_attachments.html
summary: "Use of Attachments in Digital Medicines Documents"
---

{% include important.html content="All information provided below is indicative and subject to on-going review." %}

## Background ##

The Digital Medicines documents allow for attachments to be included within a structured FHIR document.

## Use Cases ##

Senders <b>MAY</b> include attachments within the Digital Medicines documents. For example to include copies of related documents such as patient Advance Statements. 

## Format of Attachments ##

Sender <b>SHOULD</b> send attachments as a PDF, but <b>MAY</b> use other formats by local agreement.

## Receivers of Attachments ##

Receivers <b>SHOULD</b> process attachments in-line with the rules stated in the <a href="https://developer.nhs.uk/apis/itk3messagedistribution/explore_s_and_r.html" target="_blank">ITK3 Messaging Distribution Specification</a>. 

## Binary Resource ##

All attachments are carried in the FHIR Binary Resource and <b>MUST</b> be Base64 encoded. The FHIR Binary Resource is profiled as <a href="https://fhir.nhs.uk/STU3/StructureDefinition/ITK-Attachment-Binary-1">ITK-Attachment-Binary-1</a> . 

## Example Attachment ##


{% include note.html content="these examples have not been clinially assured against Digital Medicines use cases" %}
<script src="https://gist.github.com/IOPS-DEV/58db5fe49a403172541478f2dadffa8b.js"></script> 






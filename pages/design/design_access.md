---
title: Overview | Design & Build 
keywords: design, build, access, security, overview
tags: [design, overview]
sidebar: overview_sidebar
permalink: design_access.html
summary: Describes the steps required to design & build an ITK3 Messaging Solution using the interactions and profiles described in Explore.
---

{% include important.html content="All information provided below is indicative and subject to on-going review." %}

## Background ##

The Design & Build section contains descriptions of approaches and suggestions for building ITK3 Messaging Solutions using the ITK3 eDischarge components in conjunction with NHS Digital Payload specifications. The payload specification must be consulted for specific domain or payload information.


| Page              |  Description    |
|+---------------------|+--------------------------------+|
| Design Patterns / Topology | Describes access patterns necessary which influence the access, security and use of ITK3 Messaging Solutions. Depending on the pattern or topology of the sending and receiving systems. The relationship between the sender and receiver influences the choice of access mechanism, security of payload and access finally build of the system |
| Access | The access mechanism and of sending system is influenced by many factors. This section demonstrates the design decisions to consider | 
| Security | The security of the FHIR payload, access and data at rest are all important design decisions while building an ITK3 Messaging Solution.The specification for the payload should also be consulted as well as this specification. | 
| Build | A look at some tools and techniques to help build ITK3 Messaging Solutions using the interactions and Resources defined in Explore | 

## Providing a ITK3 Messaging Solution  ##

The following diagram explains the elements of ITK3 Messaging Solutions allowing the development of ITK3 Messaging Solutions:


{% include custom/provide_messaging.svg %}




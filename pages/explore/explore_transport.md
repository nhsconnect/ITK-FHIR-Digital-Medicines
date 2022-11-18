---
title: Transport
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_transport.html
summary: "The transport mechanisms used for ITK3 FHIR Documents"
---

## ITK3 and MESH  ##

Digital Medicines documents are part of the ITK3 FHIR Messaging solution. ITK3 FHIR Documents should be sent using the ITK3-FHIR-Messaging-Distribution over MESH. 

For further information on the transport mechanism see the <a href="https://developer.nhs.uk/apis/itk3messagedistribution/explore_bundle_overview.html" target="_blank">ITK3-FHIR-Messaging-Distribution</a> specification.

### MESH WorkflowIDs

| Use Case | Sender MESH WorkflowID | Receiver (Responder) MESH WorkflowID |
| -- | -- | -- |
| Pharmacy Vaccinations | DIGMED_FLU_VAC | DIGMED_FLU_VAC_ACK |
| Pharmacy Emergency Supply | DIGMED_EMG_MED | DIGMED_EMG_MED_ACK |
| Minor Illness Referral Consultation | DIGMED_MINOR_ILLNESS_PEM | DIGMED_MINOR_ILLNESS_PEM_ACK |

Refer to [MESH endpoint lookup service and WorkflowIDs](https://digital.nhs.uk/services/message-exchange-for-social-care-and-health-mesh/mesh-guidance-hub/endpoint-lookup-service-and-workflowids).

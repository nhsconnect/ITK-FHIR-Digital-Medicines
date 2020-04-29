---
title: Data Mapping
keywords: design, build,
tags: [design]
sidebar: foundations_sidebar
permalink: build_data_mapping.html
summary: "Mapping of system data to ITK3 Message and Document resources"
---

{% include important.html content="The ITK3 Messaging Solution data mapping described in this section is not meant to be complete but a starting point to understand some design considerations to consider when implementing ITK3 Messaging Solutions." %}

## What is ITK3 Messaging Solution Data Mapping? ##

Any ITK3 Messaging Solution will require some mapping of the systems data to the FHIR Resources included in the Message Bundle. For documents the data will also need to be mapped to the narrative element of the sections of the document. Some data items will probably not be available on the sending system data source and will therefore need to be created when the message is constructed. For example UUIDs for identifiers. 
Other information may need to be retrieved from central systems. For example ODS codes, SDS identifiers and in some cases patient information.  




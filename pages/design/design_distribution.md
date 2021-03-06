---
title: Access
keywords: design, build, access, security
tags: [design]
sidebar: foundations_sidebar
permalink: design_distribution.html
summary: "The Access page shows developers and users of the API how to access and call the API"
---

{% include important.html content="All phases outlined below are indicative and subject to on-going review." %}

# What is API Access? #

API access is the process of ensuring that calls to APIs with authenticated logins are able to access the APIs. API products are also a good way to control access to a specific bundle of resources/profiles or aspects of information.

This implementation guide identifies the need to manage any exposed APIs. When access control and monitoring is combined while creating an API, this can empower API implementing organisations to improve, control, limit and deny access to APIs and therefore the underlying data in a consistent mechanism. When APIs are the central mechanism for authorization and access control to your APIs. 

API access control measures need to be defined alongside API creation and need to look for:
- enforcement of authorisation
- security of Payload and access
- matching security with scope of use
- access and approval for particular resources

# Access and ITK3 eDischarges #

Access to APIs needs to considered at the design phase to include the process of managing and maintaing valid and consistant APIs. The following design considerations become increasingly important as an accessible API moves through Test to Assure to Deployed.

- Endpoints
- Report & Monitoring
- Traffic Management
- Transformation
- Versioning

For more information on the wider design decisions involved in providing safe access to information please see: 

{% include custom/contribute.html content="Provide design patterns and API usage case studies by getting in touch with careconnect@interopen.org "%}


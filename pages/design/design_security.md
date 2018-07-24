---
title: Security
keywords: design, build, access, security
tags: [design]
sidebar: foundations_sidebar
permalink: design_security.html
summary: "The security page shows how to establish initial security credentials (where necessary) with the a ITK3 Messaging Solution"
---

{% include important.html content="The ITK3 Messaging Solution security described in this section is not meant to be complete but a starting point to understand some design considerations to consider when implementing ITK3 Messaging Solutions." %}

## What is ITK3 Messaging Solution Security? ##

ITK3 Messaging Solution Security often encapsulates authentication and encryption. However, various concepts requiring diverse expertise and approaches need to be considered especially concerning testing and quality:

- Authentication: reliably identify end user
- Authorisation: identified user access to correct resources/data 
- Encryption: hide information from unauthorized access
- Signatures: ensure information integrity

Two common ways of accessing and managing ITK3 Messaging Solution security based on the need to balance access to ITK3 Messaging Solutions with the permissions to access the information contained within the ITK3 FHIR Documents and messages include:

- Federation: reusing Credentials & Spreading Resources
- Delegation: access and rights can be given to authorized users

## Authentication and Authorisation ##

Authentication and authorisation are commonly used together:

- Authentication: reliably identify end user
- Authorisation: identified user access to correct resources/data 

Authentication is most often implemented with a user-name and password. To increase the security this can be supplemented by adding 

- software certificates, 
- hardware keys and 
- external devices. 

Authorisation occurs once the user is authenticated, the system decides which resources or data to allow access to.

## Security and ITK3 Messaging Solutions ##

Security is a key consideration when establishing ITK3 Messaging Solution projects and should be considered within the design from the start of any project. The four key principles to consider are:

- Authentication
- Authorisation
- Encryption
- Signatures

For more information on the wider design decisions involved in providing safe access to information please see: 

- [Safe, legal and secure](https://developer.nhs.uk/library/save-legal-secure/) guide from developer.nhs.uk provides an overview of some design decisions and considerations to consider when implementing APIs. 

## ITK3 Messaging Solution Considerations ##

Other ITK3 Messaging Solution consideration are shown below. Please click on the parts of the ITK3 Messaging Solution process to continue your ITK3 Messaging Solution creation journey.

{% include custom/provide_messaging.svg %}



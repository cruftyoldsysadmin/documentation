# Impact Claim Template Specification

***

### _Public Working Draft dated 15 August 2017_
**Editors**

Cedric Franz (cedric@ixo.foundation.org)

## Abstract
An Impact Claim Template is used to specify the format off of which an impact claim is based.  This specification provides a standard way to express impact claims in a way that is cryptographically secure, privacy respecting, and automatically verifiable.  By standardizing the way impact claims are expressed impact claims can be compared and measured against one another.

## Status of This Document
This document is in draft status and comments regarding this document are welcome. Please file issues directly on [Github](https://github.com/TrustlabTech/Amply-Platform/issues).

***

## 1. Introduction
The Impact Claim Template is used to add consistency to the data attributes that are captured as part of an impact claim.  These standards and specifications allow for evaluating and measuring impact claims in a consistent way.  Impact Claim Templates are created and stored in a decentralized public repository.  Entities that want to specify a new type of impact claim may create their own Impact Claim Templates so that it may be used as a blueprint for the impact claims they will create. 
 
### 1.1 Ecosystem Overview
The Impact Claim ecosystem is made up of a number of different entities, but at it's core there are Funders, Service Providers and Evaluators. Funders fund the work needed to deliver on impact claims and require that these claims are evaluated to verify the impact has been delivered.  Service Providers deliver the impact, while Evaluators verify the impact, as claimed by the Service Provider of having been delivered, has actually be delivered. The data captured by the Service Provider that is needed to verify the delivery of the impact is stored in an impact claim and the data that the Service Provider needs to capture so the impact claim can be verified is specified in an Impact Claim Template.

![Impact Claim Ecosystem](https://github.com/TrustlabTech/Amply-Platform/blob/master/images/Use%20Cases.png)

### 1.2 What is an Impact Claim Template
The impact Claim Template is a schema that defines the format of impact claims.  It is structured in a way that the impact claims created using the template can be measured, evaluated and queried in a manner that is consistent across the impact claim ecosystem. The Impact Claim Template format specifies sections that contain attributes that conform to widely used schemas from the likes of [Schema.org](http://www.schema.org). 

### 1.3 What is an Impact Claim Template Registry
The Impact Claim Registry is a registry of prebuilt templates that define the attributes that are needed when creating different types of impact claims.  The registry is publicly available and is needed to ensure consistency in the way that impact claims are captured.  Any entity may add to the Impact Claim Template Registry provided that the Impact Claim Template that is added conforms to the Impact Claim Template specification.

### 1.4 Use Cases and Requirements
The critical use cases for Impact Claim Templates are numerous, but the key use cases are listed below:
* Validate Impact Claim Template against Impact Claim Template specifications
* Add Impact Claim Template to Impact Claim Registry
* Search Impact Claim Template using Impact Indicator
* Sign and save new Impact Claim Template to Impact Claim Template Registry
* Validate Impact Claim data against an Impact Claim Template

## 2. Data Model and Relationships
![High Level Object Model](https://github.com/TrustlabTech/Amply-Platform/blob/master/images/Template%20Object%20Model.png)

## 3. Impact Claim Template Specification
The Impact Claim Template is a plain text file that uses JSON-LD and schemas to structure the content of the impact claims that are capture using the template. All impact claims must conform to an impact claim template in order to work with the ixo protocols.  Any person or organization may create a new impact Claim Template and add it to the Impact Claim Registry, but it must follow the specifications outlined in this document.  Impact Claim Templates are signed and allocated a unique hash to ensure that users of the Impact Claim Template are using the correct template. 

### 3.1 Syntax
The syntax of the Impact Claim Template is plain text in JSON-LD format.  It makes use of widely used schemas and ixo schemas to define the structure of template and the values that need to be captured in the claim.

#### 3.1.1 JSON-LD
JSON-LD is a lightweight Linked Data format. It is easy for humans to read and write. It is based on the already successful JSON format and provides a way to help JSON data interoperate at Web-scale. JSON-LD is an ideal data format for programming environments, REST Web services, and unstructured databases.
find out more about JSON-LD here: [https://json-ld.org](https://json-ld.org)

### 3.2 Components of an Impact Claim Template
The Impact Claim Template specifies the format for the Impact Claim that will be captured.  This data is split into two sections.  The first section contains the attributes that are specific to the type of claim that is being captured and these vary from claim type to claim type.  This section is known as the Claim Attributes.  The second sections contains information about how, when and where the claim was captured.  This section is mandatory and must be present on all claims.  It is called the Claim Metadata.  The data in this section is normally filled in by the system or device that submits the claim.  Both these sections are individually signed with the signature of the Service Provider that submits the claim.

#### 3.2.1 Claim Attributes
The Claim Attributes vary from claim type to claim type and are specific to the claim that is being submitted and contains the information for a validator to validate that the impact was delivered.  These are specified in the Claim Attributes Schema of the Impact Claim Template. The Claim Attributes may be stored outside of the ixo network provided that the information needed to access this data is provided in the Claim Metadata section.  This data will not be publicly available.

#### 3.2.2 Claim Metadata
The Claim Metadata consists of the information to verify how the claim was submitted, who submitted it and when it was submitted. It is normally populated by the device or system submitting the claim and includes data like, IP address, device fingerprint, location, date and time of submission.  It is used to further validate the authenticity of the claim.  This data is used to create publicly available metadata about the impact claim that can be used for high level assessments of impact claims.

## 4. JSON-LD Schema
_TODO: Add link to ixo schemas_

### 4.1. References
[https://json-ld.org](https://json-ld.org)

[http://schema.org](http://schema.org)

[http://schema.cnsnt.io](http://schema.cnsnt.io)

[https://www.jamesdflynn.com/json-ld-schema-generator/](https://www.jamesdflynn.com/json-ld-schema-generator/)

[https://www.schemaapp.com/tools/jsonld-schema-generator/](https://www.schemaapp.com/tools/jsonld-schema-generator/)

[https://search.google.com/structured-data/testing-tool](https://search.google.com/structured-data/testing-tool)


## 5. Privacy Considerations
Privacy of information is critical for impact claims and serious consideration has been put in to ensure that the data remains private.  The Impact Claim Template splits the data into two sections namely the Claim Metadata and the Claim Attributes.  The Claim Attributes section contains sensitive data and this data can be stored outside of the ixo network in secure storage as chosen by the service provider or within the ixo network where strict access controls and privacy will be ensured. The Claim Metadata will be used to derive standard publicly available high level information about the Impact Claim, but ensure that privacy related details are not revealed.  The derived information will be made available through the ixo protocols, while the actual Claim Metadata will be stored securely.

## 6. Device Fingerprinting Considerations

## 7. Storage Considerations


# Impact Claim

***

### _Public Working Draft dated 21 September 2017_
**Editors**

Cedric Franz

Shaun Conway

## Introduction
Granting the proof that an impact has been deliver by a service agent is a key component of the ixo protocol.  It requires an evaluation process to ensure the service delivery took place.  In this process, the **service agent** submits a claim for evaluation and an **evaluation agent** either verifies or denies the **impact claim** based on the evaluation of the data contained within the claim and by using other external data.

For example, a service agent could submit an impact claim that they have vaccinated a particular person for malaria.  The claim would include the data, location barcode of the malaria vile, beneficiary information etc. This specification provides a standard way to express these claims on the Web in a way that is cryptographically secure, privacy respecting, and automatically verifiable.

### What is an Impact Claim
An Impact Claim is a Verifiable Claim stating that an **impact service** has been delivered by a **service agent**.  It draws from the work done by the [W3C Verifiable Claims Working Group](https://www.w3.org/TR/verifiable-claims-data-model/) and also follows the standards and structures of the [Linked Data Signatures 1.0 Draft](https://w3c-dvcg.github.io/ld-signatures/). It is useful to understand the basic terminology and structure of an impact claim.

A verifiable impact claim maps from a Verifiable claim as follows:

![Impact Claim](../diagrams/datamodel-impactClaim.png)

## Terminlology ##

**impact claim**
> A statement made by an entity about an event. A verifiable impact claim is a claim that is effectively tamper-proof and whose authorship can be cryptographically verified.

**entity**
> A thing with distinct and independent existence such as a person, organization, concept, or device that triggers and event and claims it happened

**holder**
> An entity that is in control of one or more verifiable impact claims. Typically a holder is also the issuer of the verifiable impact claims that they issued.

**issuer**
> An entity that creates a verifiable impact claim, associates it with a particular event, and transmits it to a holder.  Typically this is a **service agent**

**service agent**
> The service agent is an entity that provices an impact service.  The entity could be a person or a machine. *Examples: nurse administring a vaccinantion, fingerprint scanner recording attendance*

**evaluation agent**
> An entity that receives one or more verifiable impact claims for processing. They either verify or deny a verifiable impact claim set. This could be a manual task performed by a person or a machine that can evaluate the claim.

### Impact claim set processing ecosystem
This section outlines the set of roles and as part of the ecosystem where impact claims are processed. We distinguish the essential roles of the core actors and the relationships between them including the way these actors interact. The following roles are introduced in this specification:

![Impact Claim Pocess](../diagrams/datamodel-impactClaimProcess.png)

### Requirements
The are a number of key requirements that the actors within the ecosystem must perform:

The **holder** must receive and store impact claim sets from the **service agent**

The **holder** mediates the transmission of the impact claims between the service agent and the evaluation agent

Impact claim sets must be associated with an impact **indicator** and not particular services

**Service agents** should be able to easily control and own their own identifiers

**Holders** must be able to freely choose and change the agents they employ to help them manage and share their impact claims.

### Data Model
Every Impact Claim Set must contain the following information

**impact claim set**
> A set of data elements captured by an entity. It must include the following properties and then any other impact specific properties.
**metadata**: A set of metadata about the claim set
- **templateID**: Contains an ID of the impact claim template
- **contractID**: The ID of the contract governing these claims
- **indicator**: To classify the metric that will be captured by this impact claim
- **issued**: The date and time the impact was delivered
- **claims**: A set of impact claims relating to the delivery of this impact

**impact claim**
> An impact claim is a claim that is effectively tamper-proof and whose authorship can be cryptographically verified. An impact claim relates to the impact delivery and is issued by a service agent, which could be a person or a device. 
**metadata**: A set of metadata about the claim
- **issuer**: The DID of the issuer of this claim
- **issued**: The date and time the impact claim was made
- **claim**: Contains the claim data
- **signature**: The claim is signed by the claim issuer using a cryptographic signature to ensure the authenticity of the authorship of the impact claim


### JSON-LD Syntax

This section defines how the data model described in Data Model Section is realized in JSON-LD. Although syntactic mappings are only provided for these three different languages, applications and services may also use any other data representation language (XML, for example) that can support the data model.

### Example: Verifiable Impact Claim ###
```json-ld
{
  "id": "http://ixo.foundation/schema/",
  "type": ["Impact Claim Set"],
  “templateID” : "01454600a18666a9f08f2f99a79ce8734e5b6f353a91",
  "contractID" : "0134b4b59c3acfeb9afd9398c88b2f6f003cbf29b553"
  "indicator": {
    "type": "Indicator",
    "brand": "IRIS",
    "code": "PI9468"
  },
  "issued": "2016-02-08T16:02:20Z",
  claims: [
      {
      "@context": [
        "http://schema.org/",
        “http://ixo.foundation/schema/”,
      ],
      "id": "did:method:424342341218764655"  
      "type": ["Location", "Time"],
      "issuer": "did:method:464562546245625",  //devices did
      "issued": "2016-02-08T16:02:20Z",
      "claim": {
        "geo": {
          "location": {
            "latitude": "12.01156874",
            "longitude": "-175.57177874"
          },
        "timestamp": "2016-02-08T16:02:20Z"
      }
      "signature": {
        "type": "RsaSignature2016",
        "created": "2016-02-08T16:02:20Z",
        "creator": "did:method:8uQhQMGzWxP1vw5P3W9H1j#key/1",
        "signatureValue": "IOmA4R7TfhkYTYW8...CBMq2/gi25s="
      }
    },
    {
      "@context": [
        "http://schema.org/",
        “http://ixo.foundation/schema/”,
      ],
      "id": "did:method:4645621218764655"  
      "type": ["Location", "Time"],
      "issuer": "did:method:464562121245625",   // sevice agents did
      "issued": "2016-02-08T16:02:20Z",
      "claim": {
        "serviceCenterID": "did:method:637463264"   // did of the service center
        "productsUsed": [],
          "reason": "Water provided",
        "result": {
          "type": "Rating",
          "ratingValue": "79"
        },

      },
      "signature": {
        "type": "RsaSignature2016",
        "created": "2016-02-08T16:02:20Z",
        "creator": "did:method:8uQhQMGzWxR8vw5P3UWH1j#key/1",
        "signatureValue": "IOmA4R7TfhkYTYW8...CBMq2/gi25s="
      }
    }
  ]
}

```


### Schema ###
#### ClaimSet ####
```json-ld
{
   "@context": {
     "type": "@type",

     "cn":  "http://schema.cnsnt.io/",
     "so":  "http://schema.org/",
     "ixo": “http://ixo.foundation/schema/ClaimSet”,
     "id":  "https://w3id.org/identity",
     "sec": "https://w3id.org/security/v1",
     "ind": "https://iris.thegiin.org/indicators",

     “templateID” : "ixo:TemplateRef"
     “contractID” : "ixo:ContractRef"
     "indicator": ixo:ImpactIndicator"
     "issued": "so:Date",
     "claims": "ixo:ClaimSet",    // array of type Claim
}
```

#### Claim ####
```json-ld
{
   "@context": {
     "type": "@type",

     "cn":  "http://schema.cnsnt.io/",
     "so":  "http://schema.org/",
     "ixo": “http://ixo.foundation/schema/Claim”,
     "id":  "https://w3id.org/identity",
     "sec": "https://w3id.org/security/v1",
     "ind": "https://iris.thegiin.org/indicators",

     "issuer": "cn:DID",  //service Agent did
     "issued": "so:Date",
     "claim": "ixo:ClaimData",
     "signature": "sec:Signature"
}

```

## References ##
[Verifiable Claims Working Group](https://www.w3.org/TR/verifiable-claims-data-model/)

[Linked Data Signatures 1.0 Draft](https://w3c-dvcg.github.io/ld-signatures/)

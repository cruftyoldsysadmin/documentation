# Evaluation Claim

***

### _Public Working Draft dated 25 September 2017_
**Editors**

Cedric Franz

## Introduction
Granting the proof that an impact has been deliver by a service agent is a key component of the ixo protocol.  It requires a formal verification process to ensure the delivery took place.  In this process, the **service agent** submits a claim for verification and an **evaluation agent** either verifies or denies the **impact claim** based on the evaluation of the data contained within the claim and by using other external data.

For example, a service agent could submit an impact claim that they have vaccinated a particular person for malaria.  The claim would include the data, location barcode of the malaria vile, beneficiary information etc. This specification provides a standard way to express these claims on the Web in a way that is cryptographically secure, privacy respecting, and automatically verifiable.

### What is an Evaluation Claim
An Evaluation Claim is a Verifiable Claim stating that an **impact claim** has been evaluated by an **evaluation agent**.  If follows the structure and standards setup by the [W3C Verifiable Claims Working Group](https://www.w3.org/TR/verifiable-claims-data-model/) and also follows the standards and structures of the [Linked Data Signatures 1.0 Draft](https://w3c-dvcg.github.io/ld-signatures/). It is useful to understand the basic terminology and structure of an evaluation claim.

An evaluation claim is made up of the following key elements:

**entity**
> A thing with distinct and independent existence such as a person, organization, concept, or device. That makes the evaluation claim

**impact claim identifier**
> A reference to an immutable version of the impact claim that was evaluated

**claim data**
> A set of metadata that is included with the claim that captures information regarding how, what and where the claim was captured

**signature**
> The claim is signed by the entity, in this case the evaluation agent, using a cryptographic signature to ensure the authenticity of the authorship of the evaluation claim

### Evaluating an Impact Claim
This section outlines the evaluation procese that forms part of the impact claim process.  Please read the [Impact Claim](./Impact%20Claim.md) to fully understand the full ecosystem. We distinguish the essential roles of the core actors and the relationships between them including the way these actors interact. The following roles are introduced in this specification:

**holder**
> The holder is an entitiy that stores and manages the impact claim and the associated data.

**evaluation agent**
> Evaluation agent is an entity that either verifies or denies an impact claim that was made by service agent.  This could be a manual task performed by a person or a machine that can evaluate the claim.

![Impact Claim Pocess](../diagrams/datamodel-impactClaimProcess.png)

### Requirements
The are a number of key requirements that the actors within the ecosystem must perform:

The **holder** must receive and store impact claims from the service agent

The **holder** mediates the transmission of the impact claims between the service agent and the evaluation agent

**Holders** must be able to freely choose and change the agents they employ to help them manage and share their impact claims.

The **evaluation agent** must submit an evaluation claim contain the results of their evaluation

### Data Model
Every Evaluation Claim must contain the following information

- **issuer**: Is the DID of the evaluation agent that performed this evaluation
- **issued**: The date and time the evaluation claim was made
- **impactClaimID**: Contains an IPLD reference to the impact claim template
- **location**: The location where the evaluation claim was delivered
- **evaluationProcedure**: The procedure followed to make the evalaution
- **result**: One of the following results captured by the evaluation agent
  - VERIFIED
  - NEUTRAL
  - NOT_VERIFIED
- **reason**: The reason for this evaluation result
- **signature**: Is a list of entities who sign the claim.  The service agent must sign it, but other entities such as the beneficiaries might also sign the claim



### JSON-LD Syntax

This section defines how the data model described in Data Model Section is realized in JSON-LD. Although syntactic mappings are only provided for these three different languages, applications and services may also use any other data representation language (XML, for example) that can support the data model.

```json-ld
{
   "@context": [
     "http://schema.org/",
     "http://schema.cnsnt.io/",
     “http://ixo.foundation/schema”,
     "https://w3id.org/identity/v1",
     "https://w3id.org/security/v1",
   ],
   "@type": "EvaluationClaim",
   "issuer": <did for the evaluation agent>,
   "issued": <date and time the evaluation claim was made>,
   "location": {
      "@type": "GeoCoordinates",
      "latitude": <latitude value>,
      "longitude": <longitude value>
   },
   “impactClaimID” : <IPLD reference to unique id of the impact claim>
   "evaluationProcedure": <Evaluation procedure performed>,
   "result": < [VERIFIED|NEUTRL|NOT_VERIFIED] >,
   "reason": <reason for the evaluation result>,
   "signature": [
    {
       "@type": <signature algorithm>,
       "created": <date and time of signature>,
       "creator": <did of the evaluationAgent>,
       "signatureValue": <signature value>
     }
  ]
}

```






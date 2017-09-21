# Impact Claim

***

### _Public Working Draft dated 21 September 2017_
**Editors**

Cedric Franz (cedric@ixo.foundation.org)

## Introduction
Granting the proof that an impact has been deliver by a service agent is a key component of the ixo protocol.  It requires a formal verification process to ensure the delivery took place.  In this process, the **service agent** asks for the verification of the claim and the **evaluation agent** either verifies or denies the **impact claim** based on the evaluation of the data contained within the claim and by using other external data.

For example, a service agent could submit an impact claim that they have vaccinated a particular person for malaria.  The claim would include the data, location barcode of the malaria vile, beneficiary information etc. This specification provides a standard way to express these claims on the Web in a way that is cryptographically secure, privacy respecting, and automatically verifiable.

### What is a Impact Claim
An Impact Claim is a Verifiable Claim stating that an **impact service** has be delivered by a **service agent**.  If follows the structure and standards setup by the [W3C Verifiable Claims Working Group](https://www.w3.org/TR/verifiable-claims-data-model/). It is useful to understand the basic terminology and structure of an impact claim.

An impact claim is made up of the following key elements:

![Impact Claim](../diagrams/datamodel-impactClaim.png)

**entity**
> A thing with distinct and independent existence such as a person, organization, concept, or device.

**claim data**
> A set of data elements captured by an entity. An impact claim is a claim that is effectively tamper-proof and whose authorship can be cryptographically verified.

**metadata**
> A set of metadata that is included with the claim that captures information regarding how, what and where the claim was captured

**signature**
> The claim is signed by the entity using a cryptographic signature to ensure the authenticity of the authorship of the impact claim

# ixo Protocol: Command Line Interface Specifications


The ixo protocol commes with a command line interface to perform most of the functions that the protocol supports.  The are four broad catgories for of commands and the this document provides the specifications for each of them as well as how to install the system and run the commands.

[Flow Diagrams](./diagrams/Flows.png)

## Installation
 _(TODO - Spec out the installation instructions for setting up this)_
 
## Command Line Specification

#### General Usage
*(TODO - describe the general structure of commands and thier usage e.g. shortened form vs longer form etc.)*

## Agent Management

### Create a Decentralized Identity (DID)

Creates a Sovrin DID based off a passphrase

**Command:** createDID

**Arguments:**

**Optional Arguments:**
The name of a file to output the agent to
>-o, --output \<filename\>

A mnemonic if none is given then one will be generated
>-m, --mnemonic \<mnemonic\>

**Return:**
```
{
  "mnemonic: "toss great symptom pact rent potato current join spell inherit rescue marine",
  "sdid": {
    "did": "FYqoVcAHHYiZKnYJYh4LB6",
    "verifyKey": "8vvVSkZFU8bHYFXJnZ6j34xX7Yj2DcdndzjNsWLN5HDQ",
    "secret": {
      "seed": "9b1aacde05cdcfd715e994a796d904dbc6820aae83a32cf9bdd28e90c1e0aac5",
      "signKey": "BSTnXNamaXBCxmMNERv2Q1TerQaYYBux6PmKJHxahzCL"
    }
  }
}
```

### Create a ixo Agent

Creates a new ixo Agent

**Command:** createAgent

**Arguments:**

The DID of the agetn
>-d, --did \<did\>

The public key for the supplied DID
>-p, --publicKey \<public key for did\>

The name of the person or organisation that has this DID
>-n, --name \<name of the DID owner\>

The ISO 3166-2 two letter country code
>-c, --country \<two letter country code\>

**Optional Arguments:**

**Return:**
```
{
  "did": "FYqoVcAHHYiZKnYJYh4LB6",
  "name": "ABC Inc.",
  "country": "US",
  "publicKey": "8vvVSkZFU8bHYFXJnZ6j34xX7Yj2DcdndzjNsWLN5HDQ"
}
```

### Get Agent

Returns the registered agent for the supplied DID

**Command:** getAgent

**Arguments:**

The DID of a agent
>-d, --did \<did\>

**Optional Arguments:**

**Return:**
```
  {
    "id: "5d52e812f53efd4d4b584eba56da8bfaadb7771938be7c3871c71340c2d1d625",
    "did": "FDF5TJwDDw8BHGXEB4deXA",
    "name": "Jane Smith",
    "country": "US",
    "publicKey": "8kEwLE5d1X1RVXwRL2YEZj896LoGTfp4z2pqYZzGVp4r"
  }
```

### List Agents

List ixo Agents

**Command:** listAgents

**Arguments:**

The ISO 3166-2 two letter country code
>-c, --country \<two letter country code\>

**Optional Arguments:**

**Return:**
List of matching agents
```
[
  {
    "id: "2e812f53efd4d4b584eba56da938be75d58bfaadb7771c3871c71340c2d1d625",
    "did": "FYqoVcAHHYiZKnYJYh4LB6",
    "name": "ABC Inc.",
    "country": "US",
    "publicKey": "8vvVSkZFU8bHYFXJnZ6j34xX7Yj2DcdndzjNsWLN5HDQ"
  },
  {
    "id: "5d52e812f53efd4d4b584eba56da8bfaadb7771938be7c3871c71340c2d1d625",
    "did": "FDF5TJwDDw8BHGXEB4deXA",
    "name": "Jane Smith",
    "country": "US",
    "publicKey": "8kEwLE5d1X1RVXwRL2YEZj896LoGTfp4z2pqYZzGVp4r"
  }
]
```

### Sign a Document

Sign document

**Command:** sign

**Arguments:**

The file DID doc file for the agent performing this request
>-a, --agent \<agentDoc\>

The file containing the json document or it is read from stdin
>-i, --input \<file containing template JSON\>

The file to save the signed json document  or it is written to stdout
>-o, --output \<File to output signed template\>


**Return:**
```
{
  <some json>
  
  "issuer": "FYqoVcAHHYiZKnYJYh4LB6",
  "issued": "2016-02-08T16:02:20",
  "signature": {
    "type": "RsaSignature2016",
    "created": "2016-02-08T16:02:20",
    "creator": "FYqoVcAHHYiZKnYJYh4LB6#key/1",
    "signatureValue": "IOmA4R7TfhkYTYW8...CBMq2/gi25s="
  }
}
```


## Template Management

### Register a Template

Register a signed Impact Template with the ixo system.  The template is validated and registered to the logged in agent

**Command:** registerTemplate

**Arguments:**

The DID of a agent
>-d, --did \<did\>

A file that contains the signed impact template JSON or read from stdIn
>-i, --input \<filename\>

**Return:**
```
{
  "templateId: "938be75d52e812f53efd4d4b584eba56da8bfaadb7771c3871c71340c2d1d625",
  "indicator": "P1261.23",
  "created": "2016-02-08T16:02:20Z",
  "creator": "did:example:8uQhQMGzWxR8vw5P3UWH1j#key/1",

  <some json>
}
```

### Verify a Template

Verify that the signature of an Impact Template matches a particular agent registered on the ixo system.

**Command:** verifyTemplate

**Arguments:**

The DID of a agent that created the template
>-d, --did \<did\>

The ID of the template
>-t, --templateId \<template ID\>

**Optional Arguments:**

**Return:**
```
{
  "id: "938be75d52e812f53efd4d4b584eba56da8bfaadb7771c3871c71340c2d1d625",
  "data: {
  	...
  }
}
```

## Decentralize Impact Exchange (DIX) Management

### Create a DIX Project

Create a DIX project with the ixo system (This is done on the client)

**Command:** createProject

**Arguments:**

The DID of a agent
>-d, --did \<did\>

The description of the DIX project
>-d, --descr \<DIX description\>

The uri reference link to more information regarding the project
>-l, --link \<A URI\>

The start date yyyy-mm-dd when the DIX is due to start
>-s, --start \<start date\>

The end date yyyy-mm-dd when the DIX should be finished
>-e, --end \<end date\>

The ID of the template that needs to be used for capturing impacts
>-t, --templateId \<template ID\>

The number of impacts that need to be delivered
>-n, --number \<number of impacts\>

The value of DIX project in USD
>-v, --value \<value of the project as an integer\>

The ISO 3166-2 two letter country code
>-c, --country \<two letter country code\>

**Optional Arguments:**

The name of a file to output the signed DIX project to or stdout
>-o, --output \<filename\>

**Return:**
```
{
  "ownerDid": "FYqoVcAHHYiZKnYJYh4LB6",
  "createdOn": "2017-03-3T13:02:32"
  "description": ""
  "uri": "",
  "startDate": "2017-07-02",
  "endDate": "2019-07-02",
  "indicator": "P43527",
  "templateId": "938be75d52e812f53efd4d4b584eba56da8bfaadb7771c3871c71340c2d1d625",
  "number": 1000,
  "count": 0,
  "usdValue": 40000,
  "country": "RW",
  "status": "NotStarted"
}
```
### Submit a DIX Project

Submit a DIX Project on the ixo system.

**Command:** submitProject

**Arguments:**

The DID of a agent
>-d, --did \<did\>

**Optional Arguments:**

A file that contains the signed DIX project JSON or read from stdIn
>-i, --input \<filename\>

**Optional Arguments:**

**Return:**
```
{
  "id": "a67bf66d52e8156e3efe66fb584eba56da8bfaadb7891c3871c71340c2d1de89",
  "data: {
    "issuer": "FYqoVcAHHYiZKnYJYh4LB6",
    "issued": "2016-02-08T16:02:20",
    "ownerDid": "FYqoVcAHHYiZKnYJYh4LB6",
    "createdOn": "2017-03-3T13:02:32"
    "description": ""
    "uri": "",
    "startDate": "2017-07-02",
    "endDate": "2019-07-02",
    "indicator": "P43527",
    "templateId": "938be75d52e812f53efd4d4b584eba56da8bfaadb7771c3871c71340c2d1d625",
    "number": 1000,
    "count": 0,
    "usdValue": 40000,
    "country": "RW",
    "status": "NotStarted",
    "signature": {
      "type": "RsaSignature2016",
      "created": "2016-02-08T16:02:20",
      "creator": "FYqoVcAHHYiZKnYJYh4LB6#key/1",
      "signatureValue": "IOmA4R7TfhkYTYW8...CBMq2/gi25s="
    }
  }
}
```

### List DIX Projects

List ixo Projects

**Command:** listProjects

**Arguments:**

**Optional Arguments:**

The DID of the owner
>-d, --did \<DID of the owner\>

The indicator of the impact
>-i, --indicator \<indicator\>

The status of the project ("(N)otStarted", "(S)tarted", "(E)nded")
>-s, --status \<status\>

The ISO 3166-2 two letter country code
>-c, --country \<two letter country code\>


**Return:**
List of matching agents
```
[
  {
    "id": "a67bf66d52e8156e3efe66fb584eba56da8bfaadb7891c3871c71340c2d1de89",
    "data: {
      "issuer": "FYqoVcAHHYiZKnYJYh4LB6",
      "issued": "2016-02-08T16:02:20",
      "ownerDid": "FYqoVcAHHYiZKnYJYh4LB6",
      "createdOn": "2017-03-03T13:02:32"
      "description": "Malaria vaccinations"
      "uri": "https://impacts.com/projects/6364893",
      "startDate": "2017-07-02",
      "endDate": "2019-07-02",
      "indicator": "P43527",
      "templateId": "938be75d52e812f53efd4d4b584eba56da8bfaadb7771c3871c71340c2d1d625",
      "number": 1000,
      "count": 0,
      "usdValue": 40000,
      "country": "RW",
      "status": "NotStarted",
      "signature": {
        "type": "RsaSignature2016",
        "created": "2016-02-08T16:02:20",
        "creator": "FYqoVcAHHYiZKnYJYh4LB6#key/1",
        "signatureValue": "IOmA4R7TfhkYTYW8...CBMq2/gi25s="
      }

    }
  },
  {
    "id": "bff5f66d52e8156e3efe66fb584eba56da8bfaadb7891c3871c71340c2d1de89",
    "data: {
      "issuer": "FYqoVcAHHYiZKnYJYh4LB6",
      "issued": "2016-02-08T16:02:20",
      "ownerDid": "FYqoVcAHHYiZKnYJYh4LB6",
      "createdOn": "2016-06-30T15:12:02"
      "description": "Build school"
      "uri": "https://impacts.com/projects/6364893",
      "startDate": "2016-07-02",
      "endDate": "2018-07-02",
      "indicator": "P44428",
      "templateId": "fe65e75d52e812f53efd4d4b584eba56da8bfaadb7771c3871c71340c2d1d625",
      "number": 3,
      "count": 2,
      "usdValue": 30000,
      "country": "US",
      "status": "Started",
      "signature": {
        "type": "RsaSignature2016",
        "created": "2016-02-08T16:02:20",
        "creator": "FYqoVcAHHYiZKnYJYh4LB6#key/1",
        "signatureValue": "IOmA4R7TfhkYTYW8...CBMq2/gi25s="
      }
    }
  }
]
```

### Create Add Agent to DIX Project Request

Register an agent to the DIX project for a particular role.  Only agents with owner role on the dix can add an agent

**Command:** createAddAgentToProjectRequest

**Arguments:**

The ID of the DIX
>-p, --dixProjectID \<dix ID\>

The DID of the agent being added
>-d, --did \<DID of agent\>

The role of the agent that is being added to the DIX project ("(O)wner, (S)ervice Agent, (F)unding Agent, (E)valuation Agent")
>-r, --role \<the role\>

**Optional Arguments:**

**Return:**
```
{
  "type": ["Role"],
  "dixID" : "bff5f66d52e8156e3efe66fb584eba56da8bfaadb7891c3871c71340c2d1de89"
  "role": {
  	"type": "FundingAgent",
	"did": "YiZKnFYqoVcAHHYJYh4LB6",
  }
}
```
### Add Agent to DIX Project

Register an agent to the DIX project for a particular role.  Only agents with owner role on the dix can add an agent

**Command:** addAgentToProject

**Arguments:**

The DID of a agent
>-d, --did \<did\>

**Optional Arguments:**

A file that contains the signed request to add an agent to a DIX project JSON or read from stdIn
>-i, --input \<filename\>

**Return:**
```
{
  "id": "de89bff5f66db71340caadb7891c387a56da8bf52e8156ec12d13efe66fb584e",
  "type": ["Role"],
  "dixID" : "bff5f66d52e8156e3efe66fb584eba56da8bfaadb7891c3871c71340c2d1de89"
  "issuer": "FYqoVcAHHYiZKnYJYh4LB6",
  "issued": "2016-02-08T16:02:20",
  "role": {
  	"type": "FundingAgent",
	"did": "YiZKnFYqoVcAHHYJYh4LB6",
  },
  "signature": {
    "type": "RsaSignature2016",
    "created": "2016-02-08T16:02:20",
    "creator": "FYqoVcAHHYiZKnYJYh4LB6#key/1",
    "signatureValue": "IOmA4R7TfhkYTYW8...CBMq2/gi25s="
  }
}
```
### Create Revoke Agent from DIX Project Request

Revoke an agent for a role from the DIX project.  Only agents with owner role on the dix can revoke an agent for a role. You can't revoke your own capability.

**Command:** createRevokeAgentFromProjectRequest

**Arguments:**

The ID of the DIX 
>-p, --dixProjectID \<dix ID\>

The DID of the agent being added
>-d, --did \<DID of agent\>

The id of capability being revoked from the DIX project
>-r, --roleID \<the RoleID\>

**Optional Arguments:**

**Return:**
```
{
  "type": ["Revoked Role"],
  "dixID" : "bff5f66d52e8156e3efe66fb584eba56da8bfaadb7891c3871c71340c2d1de89"
  "roleID": "de89bff5f66db71340caadb7891c387a56da8bf52e8156ec12d13efe66fb584e",
}
```

### Revoke Agent for a Role from DIX Project

Revoke an agent for a role from the DIX project.  Only agents with owner role on the dix can revoke an agent for a role. You can't revoke your own capability.

**Command:** revokeAgentFromProject

**Arguments:**

The DID of a agent
>-d, --did \<did\>

**Optional Arguments:**

A file that contains the signed request to revoke an agent from a DIX project JSON or read from stdIn
>-i, --input \<filename\>


**Return:**
```
{
  "id": "df5f66db71340c8156ec12d13efe66fbaadb78e89bf91c387a56da8bf52e584e",
  "type": ["Revoked Role"],
  "dixID" : "bff5f66d52e8156e3efe66fb584eba56da8bfaadb7891c3871c71340c2d1de89"
  "issuer": "FYqoVcAHHYiZKnYJYh4LB6",
  "issued": "2016-02-08T16:02:20",
  "roleID": "de89bff5f66db71340caadb7891c387a56da8bf52e8156ec12d13efe66fb584e",
  "signature": {
    "type": "RsaSignature2016",
    "created": "2016-02-08T16:02:20",
    "creator": "FYqoVcAHHYiZKnYJYh4LB6#key/1",
    "signatureValue": "IOmA4R7TfhkYTYW8...CBMq2/gi25s="
  }
}
```

## Impact Claims Management

### Sign a Claim

Sign a claim use the sign document with the claim data

**Example Claim:**
```
{
  "type": ["Location", "Time"],
  "claim": {
    "serviceCenterID": "FYqojhvfSiZKnYJYh4LB6",
    "productsUsed": [],
    "reason": "Water provided",
    "result": {
      "type": "Rating",
      "ratingValue": "79"
    }
  },
}
```

### Create a Claim Set

The creates a signed Claim Set for a DIX contract.  

**Command:** createClaimSet

**Arguments:**

The ID of the DIX project that this claimSet is for
>-p, --dixProjectID \<dix ID\>

The list of signed claims that make up this claim set
>-f, --files \<one or more file that contain signed claims\>

**Optional Arguments:**

The file to save the signed claim set or it is written to stdout
>-o, --output \<File to output signed claimSet\>


**Return:**
```
{
  "id": "de89bff5f66db71340caadb7891c387a56da8bf52e8156ec12d13efe66fb584e",
  "type": ["Impact Claim Set"],
  "dixID" : "bff5f66d52e8156e3efe66fb584eba56da8bfaadb7891c3871c71340c2d1de89"
  "claims": [
      {
      "id": "c71340c2d1de89bff5f66dba56da8bfaadb7891c387152e8156e3efe66fb584e"  
      "type": ["Location", "Time"],
      "issuer": "FnYJYh4LBYqoVcAHHYiZK6",
      "issued": "2016-02-08T16:02:20",
      "claim": {
        "geo": {
          "location": {
            "latitude": "12.01156874",
            "longitude": "-175.57177874"
          },
        "timestamp": "2016-02-08T16:02:20"
      }
      "signature": {
        "type": "RsaSignature2016",
        "created": "2016-02-08T16:02:20",
        "creator": "FnYJYh4LBYqoVcAHHYiZK6#key/1",
        "signatureValue": "IOmA4R7TfhkYTYW8...CBMq2/gi25s="
      }
    },
    {
      "id": "752e8156e3e2d1de89bff51340cca56da8bfaadb7891c3871f66dbfe66fb584e"  
      "type": ["Location", "Time"],
      "issuer": "FYqoVcAHHYiZKnYJYh4LB6",
      "issued": "2016-02-08T16:02:20",
      "claim": {
        "serviceCenterID": "FYqojhvfSiZKnYJYh4LB6",
        "productsUsed": [],
        "reason": "Water provided",
        "result": {
          "type": "Rating",
          "ratingValue": "79"
        },

      },
      "signature": {
      "type": "RsaSignature2016",
      "created": "2016-02-08T16:02:20",
      "creator": "FYqoVcAHHYiZKnYJYh4LB6#key/1",
      "signatureValue": "IOmA4R7TfhkYTYW8...CBMq2/gi25s="
      }
    }
  ]
}

```
### Submit a Claim Set

The loggned in agent submits a Claim Set to the DIX contract.  Before the claim set is accepted a number of checks are done:
* The issuer of the claimSet is validated against the DIX contract to ensure they may submit claims
* Each claim is validated to ensure that it conforms to template registered for this DIX contract
* The signatures of each individual claim is verified against the issuer for that claim.

**Command:** submitClaimSet

**Arguments:**

The DID of the agent submitting the claimset
>-d, --did \<DID of agent\>

The ID of the DIX that this claim is for
>-p, --dixProjectID \<dix ID\>

**Optional Arguments:**

The file containing the claim data or it is read from stdin
>-i, --input \<file containing signed claimSet\>


**Return:**
```
{
  "id": "de89bff5f66db71340caadb7891c387a56da8bf52e8156ec12d13efe66fb584e",
  "type": ["Impact Claim Set"],
  “templateID” : "fe65e75d52e812f53efd4d4b584eba56da8bfaadb7771c3871c71340c2d1d625",
  "dixID" : "bff5f66d52e8156e3efe66fb584eba56da8bfaadb7891c3871c71340c2d1de89"
  "indicator": "P44428",
  "issuer": "FYqoVcAHHYiZKnYJYh4LB6",
  "issued": "2016-02-08T16:02:20",
  "claims": [
      {
      "id": "c71340c2d1de89bff5f66dba56da8bfaadb7891c387152e8156e3efe66fb584e"  
      "type": ["Location", "Time"],
      "issuer": "FnYJYh4LBYqoVcAHHYiZK6",
      "issued": "2016-02-08T16:02:20",
      "claim": {
        "geo": {
          "location": {
            "latitude": "12.01156874",
            "longitude": "-175.57177874"
          },
        "timestamp": "2016-02-08T16:02:20"
      }
      "signature": {
        "type": "RsaSignature2016",
        "created": "2016-02-08T16:02:20",
        "creator": "FnYJYh4LBYqoVcAHHYiZK6#key/1",
        "signatureValue": "IOmA4R7TfhkYTYW8...CBMq2/gi25s="
      }
    },
    {
      "id": "752e8156e3e2d1de89bff51340cca56da8bfaadb7891c3871f66dbfe66fb584e"  
      "type": ["Location", "Time"],
      "issuer": "FYqoVcAHHYiZKnYJYh4LB6",
      "issued": "2016-02-08T16:02:20",
      "claim": {
        "serviceCenterID": "FYqojhvfSiZKnYJYh4LB6",
        "productsUsed": [],
        "reason": "Water provided",
        "result": {
        "type": "Rating",
        "ratingValue": "79"
      },

      },
      "signature": {
      "type": "RsaSignature2016",
      "created": "2016-02-08T16:02:20",
      "creator": "FYqoVcAHHYiZKnYJYh4LB6#key/1",
      "signatureValue": "IOmA4R7TfhkYTYW8...CBMq2/gi25s="
      }
    }
  ],
  "signature": {
    "type": "RsaSignature2016",
    "created": "2016-02-08T16:02:20",
    "creator": "FnYJYh4LBYqoVcAHHYiZK6#key/1",
    "signatureValue": "IOmA4R7TfhkYTYW8...CBMq2/gi25s="
  }
}

```

### Create an Evaluation for Claim Set

Create an evaluate a Claim Set.

**Command:** createEvaluation

**Arguments:**

The file DID doc file for the agent performing this request
>-u, --agent \<agentDoc\>

The ID of the claimSet
>-c, --claimsetId \<claimSet ID\>

The result of the evaluation ("(V)erified", "(F)ailed", "(U)ndecided")
>-r, --result \<Result of the evaluation\>

**Optional Arguments:**

A comment relating to the result of evaluation 
>-n, --comment \<Comment\>

**Return:**
```
{
  "type": "Evaluation Claim",
  "issuer": "FncAHHYiYJYh4LBYqoVZK6",
  "issued": "2016-04-18T12:02:20",
  “claimSetID” : "de89bff5f66db71340caadb7891c387a56da8bf52e8156ec12d13efe66fb584e",
  "evaluationProcedure": <Evaluation procedure performed>,
  "result": "Verified",
  "comment": "Verification successful.",
  "signature": {
    "type": "RsaSignature2016",
    "created": "2016-04-18T12:02:20",
    "creator": "FncAHHYiYJYh4LBYqoVZK6#key/1",
    "signatureValue": "IOmA4R7TfhkYTYW8...CBMq2/gi25s="
  }
}
```
### Submit an Evaluation for Claim Set

Submit an evaluation for a Claim Set.

**Command:** submitClaimSet

**Arguments:**

The DID of the agent submitting the claimset
>-d, --did \<DID of agent\>

The ID of the claimSet
>-c, --claimsetId \<claimSet ID\>

**Optional Arguments:**

The file containing the claim data or it is read from stdin
>-i, --input \<file containing signed claimSet\>

**Return:**
```
{
  "id": "daad5f66db71340caadb7891c387a5efe89bff5f66db71340ce66fb584e",
  "type": "Evaluation Claim",
  "issuer": "FncAHHYiYJYh4LBYqoVZK6",
  "issued": "2016-04-18T12:02:20",
  “claimSetID” : "de89bff5f66db71340caadb7891c387a56da8bf52e8156ec12d13efe66fb584e",
  "evaluationProcedure": <Evaluation procedure performed>,
  "result": "Verified",
  "comment": "Verification successful.",
  "signature": {
    "type": "RsaSignature2016",
    "created": "2016-04-18T12:02:20",
    "creator": "FncAHHYiYJYh4LBYqoVZK6#key/1",
    "signatureValue": "IOmA4R7TfhkYTYW8...CBMq2/gi25s="
  }
}
```



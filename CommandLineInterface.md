# ixo Protocol: Command Line Interface Specifications


The ixo protocol commes with a command line interface to perform most of the functions that the protocol supports.  The are four broad catgories for of commands and the this document provides the specifications for each of them as well as how to install the system and run the commands.

## Installation
 _(TODO - Spec out the installation instructions for setting up this)_
 
## Command Line Specification

Commands must be executed within a particular scope.  There are two scopes defined for the  ixo protocil commands the first scope is the root scope and the second scope is as a loggined in user.  For the purposes of this interface we call these scopes **root** and **user** scope.  Some of the commands can only be executed in **user** scope and requires a user to be 'logged in'.  The commands that require **user** scope are mostly related to commands where a user needs to sign some information with their private key.  All commands that can be executed in **root** scope can also be executed in **user** scope.

#### General Usage
*(TODO - describe the general structure of commands and thier usage e.g. shortened form vs longer form etc.)*

## User Management

### Create a Decentralized Identity (DID)

Creates a Sovrin DID based off a passphrase

**Command:** createDID

**Arguments:**

**Optional Arguments:**

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

**Scope:** root

---

### Create a User

Creates a new ixo User

**Command:** createUser

**Arguments:**

The DID of the user
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

**Scope:** root

---

### Get User

Returns the registered user for the supplied DID

**Command:** getUser

**Arguments:**

The DID of a user
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

**Scope:** root

---

### List Users

List ixo User

**Command:** listUsers

**Arguments:**

The ISO 3166-2 two letter country code
>-c, --country \<two letter country code\>

**Optional Arguments:**

**Return:**
List of matching users
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

**Scope:** root

---

### Login

Log the user in and change the scope to **user** scope if successful

**Command:** login

**Arguments:**

The DID of a user
>-d, --did \<did\>

A mnemonic if none is given then one will be generated
>-m, --mnemonic \<mnemonic\>

**Optional Arguments:**

**Return:**
List of matching users
```
{
   "did": "FYqoVcAHHYiZKnYJYh4LB6",
}
```

**Scope:** root

---

### Logout

Log the current user out and change the scope to **root** scope if successful

**Command:** logout

**Arguments:**

**Optional Arguments:**

**Return:**
```
{
   "success": "true",
}
```

**Scope:** user

---

## Template Management

### Register a Template

Register an Impact Template with the ixo system.  The template is validated and registered to the logged in user and signed with their private key

**Command:** registerTemplate

**Arguments:**

A file that contains the impact template JSON
>-t, --template \<filename\>

**Optional Arguments:**

**Return:**
```
{
  "templateId: "938be75d52e812f53efd4d4b584eba56da8bfaadb7771c3871c71340c2d1d625",
}
```

**Scope:** user

---

### Verify a Template

Verify that the signature of an Impact Template matches a particular user registered on the ixo system.

**Command:** verifyTemplate

**Arguments:**

The DID of a user that created the template
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

**Scope:** root

---

## Decentralize Impact Exchange (DIX) Management

### Register a DIX Project

Register an DIX with the ixo system.

**Command:** registerProject

**Arguments:**

The description of the DIX project
>-d, --descr \<DIX description\>

The uri reference to more information regarding the project
>-u, --uri \<A URI\>

The start date YYYY-MM-SS when the DIX is due to start
>-s, --start \<start date\>

The end date YYYY-MM-SS when the DIX should be finished
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

**Return:**
```
{
  "id": "a67bf66d52e8156e3efe66fb584eba56da8bfaadb7891c3871c71340c2d1de89",
  "data: {
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
}
```

**Scope:** user

---

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
List of matching users
```
[
  {
    "id": "a67bf66d52e8156e3efe66fb584eba56da8bfaadb7891c3871c71340c2d1de89",
    "data: {
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
      "status": "NotStarted"
    }
  },
  {
    "id": "bff5f66d52e8156e3efe66fb584eba56da8bfaadb7891c3871c71340c2d1de89",
    "data: {
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
      "status": "Started"
    }
  }
]
```

**Scope:** root

---

### Add User to DIX Project

Register a user to the DIX project with a particular capability.  Only users with owner capability on the dix can add capabilities

**Command:** addUserToProject

**Arguments:**

The ID of the DIX that this claim is for
>-d, --dixId \<dix ID\>

The DID of the user being added
>-d, --did \<DID of user\>

The capability being added to the DIX project ("(O)wner, (S)ervice Agent, (F)unding Agent, (E)valuation Agent")
>-c, --capability \<the capability\>

**Optional Arguments:**

**Return:**
```
{
  "id": "de89bff5f66db71340caadb7891c387a56da8bf52e8156ec12d13efe66fb584e",
  "type": ["Capability"],
  "dixID" : "bff5f66d52e8156e3efe66fb584eba56da8bfaadb7891c3871c71340c2d1de89"
  "issuer": "FYqoVcAHHYiZKnYJYh4LB6",
  "issued": "2016-02-08T16:02:20",
  "capability": {
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
**Scope:** user

---

### Revoke User Capability from DIX Project

Revoke a capability from the DIX project.  Only users with owner capability on the dix can revoke a capability. You can't revoke your own capability.

**Command:** revokeUserFromProject

**Arguments:**

The ID of the DIX that this claim is for
>-d, --dixId \<dix ID\>

The DID of the user being added
>-d, --did \<DID of user\>

The id of capability being revoked from the DIX project
>-c, --capabilityID \<the capabilityID\>

**Optional Arguments:**

**Return:**
```
{
  "id": "df5f66db71340c8156ec12d13efe66fbaadb78e89bf91c387a56da8bf52e584e",
  "type": ["Revoked Capability"],
  "dixID" : "bff5f66d52e8156e3efe66fb584eba56da8bfaadb7891c3871c71340c2d1de89"
  "issuer": "FYqoVcAHHYiZKnYJYh4LB6",
  "issued": "2016-02-08T16:02:20",
  "capabilityID": "de89bff5f66db71340caadb7891c387a56da8bf52e8156ec12d13efe66fb584e",
  "signature": {
    "type": "RsaSignature2016",
    "created": "2016-02-08T16:02:20",
    "creator": "FYqoVcAHHYiZKnYJYh4LB6#key/1",
    "signatureValue": "IOmA4R7TfhkYTYW8...CBMq2/gi25s="
  }
}
```
**Scope:** user

---

## Impact Claims Management

### Sign a Claim

Sign a claim

**Command:** signClaim

**Arguments:**

The file containing the claim data
>-i, --input \<file containing claim JSON\>

The file to save the signed claim
>-o, --output \<File to output signed claim\>

**Optional Arguments:**

**Return:**
```
{
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
  "signature": {
    "type": "RsaSignature2016",
    "created": "2016-02-08T16:02:20",
    "creator": "FYqoVcAHHYiZKnYJYh4LB6#key/1",
    "signatureValue": "IOmA4R7TfhkYTYW8...CBMq2/gi25s="
  }
}
```

**Scope:** user

---

### Submit a Claim Set

The loggned in user submits a Claim Set to the DIX contract.  Before the claim set is accepted a number of checks are done:
* The issuer of the claimSet is validated against the DIX contract to ensure they may submit claims
* Each claim is validated to ensure that it conforms to template registered for this DIX contract
* The signatures of each individual claim is verified against the issuer for that claim.

**Command:** submitClaimSet

**Arguments:**

The ID of the DIX that this claim is for
>-d, --dixId \<dix ID\>

The list of signed claims that make up this claim set
>-f, --files \<one or more file that contain signed claims\>

**Optional Arguments:**

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
  ]
}

```

**Scope:** user

---
### Evaluate a Claim Set

Evaluate a Claim Set.

**Command:** evaluateClaimSet

**Arguments:**

The ID of the claimSet
>-c, --claimsetId \<claimSet ID\>

The result of the evaluation ("(V)erified", "(F)ailed", "(U)ndecided")
>-r, --result \<Result of the evaluation\>

**Optional Arguments:**

A comment relating to the result of evaluation 
>-c, --comment \<Comment\>

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

**Scope:** user

---



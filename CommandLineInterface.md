# ixo Protocol 
# Command Line Interface Specifications


The ixo protocol commes with a command line interface to perform most of the functions that the protocol supports.  The are four broad catgories for of commands and the this document provides the specifications for each of them as well as how to install the system and run the commands.

## Installation
 _TODO_
 
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

### Add Capability to a User

Adds a capability to an ixo User

*(TODO)*

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
    "did": "FYqoVcAHHYiZKnYJYh4LB6",
    "name": "ABC Inc.",
    "country": "US",
    "publicKey": "8vvVSkZFU8bHYFXJnZ6j34xX7Yj2DcdndzjNsWLN5HDQ"
  },
  {
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

Verify the signature of an Impact Template matches a particular user registered on the ixo system.

**Command:** registerTemplate

**Arguments:**

The DID of a user that created the template
>-d, --did \<did\>

The address of the template
>-t, --templateAddress \<template Address\>

**Optional Arguments:**

**Return:**
```
{
  "templateID: "938be75d52e812f53efd4d4b584eba56da8bfaadb7771c3871c71340c2d1d625",
}
```

**Scope:** root

---

# Decentralized Impact Exchanges

*Authors: Dr Shaun Conway and Lohan Spies*

In this article we introduce the concept of Decentralized Impact Exchanges that
are central to the ixo Protocol. <br> Impact Exchanges provide a mechanism for
producing verified Impact Data that provides Proof of Impact and then to
exchange this for funding and other forms of value. We believe this is a
foundational concept for growing the [Impact
Economy](http://impacteconomy.org/).

### Investing for Impact

We all try to make intelligent personal investment decisions that are based on
good information. Our choices are informed by performance data from sources we
expect to be trustworthy, so that we can know: Which mutual funds performed
best? What’s the housing price trend in the neighbourhood? How did the company
fare in its latest quarterly results? Is the fuel consumption of the car on
offer going to be good value for money? Will this school award me a degree that
increases my earning potential?

On the basis of this information, we decide whether to exchange our capital for
the results that we hope to achieve. Then we track the outcomes of our
investments to know whether these results have delivered.

In contrast, billions are invested by governments and development agencies every
year, without good quality, trustworthy data. <br> Trillions more in capital
funds will be directed in coming years, towards making investments and
alleviating risks by funding impacts. This need much improved ways for impacts
to be measured, to optimise the returns on these investments — for both
finanancial and societal results.

### Why this matters

The rationale for investing in impact is based on the growing need to address
global sustainability challenges such as climate change, political instability,
healthcare, education and other development priorities for humanity to prosper.
But without good impact data, these investments cannot optimise results. We need
[a World That Counts](http://www.undatarevolution.org/report/). <br> The UN
Secretary-General has therefore called for a [Data
revolution](http://www.undatarevolution.org/) for sustainable development

### An Impact Protocol for the world

Over the past 4 years we have been working on a blockchain Impact Protocol,
which we refer to as **The ixo Protocol**. <br> The fundamental principle of
this protocol is that impact funding should be exchanged for trustworthy impact
data that provides Proof of Impact.

Like all trusty tripods, there are three core components to this:

* **Decentralised Impact Exchanges** enable anyone to coordinate and incentivise a
combination of funders, service agents and evaluation agents to come together
and produce explicitly defined, measurable impacts. This is a market-making
mechanism. Impact Exchange Projects can be established without any reliance on
central authorities or intermediaries. Fees paid to the network hosts of the
protocol, as well as peer-to-peer payments for services to execute and evaluate
projects, are transacted through these decentralised impact exchanges.
* **Proof of Impact** that gets generated through the data processing capabilities
of the protocol. This includes a semantic abstraction graph that links open data
ontologies, impact claim templates and indicator definitions. Mechanisms for
evaluation agents to evaluate impact claims interface with the protocol at this
layer and this encodes the generic business logic for processing claims and to
produce cryptographic proofs that are tokenised and stored in the Global Impact
Ledger.
* **The Global Impact Ledger** which provides the decentralised data asset storage
and data sharing capabilities of the protocol. This enables tokenized Proofs of
Impact to be recorded within blockchain transactions. The distributed ledger
serves as a global index to a virtually shared and distributed Big Impact Data
commons. This provides a transparent and accountable public record of
Sustainable Development impacts. It also routes to all the underlying datasets
and provides a mechanism for this data to be shared. The protocol includes a
built-in data governance mechanism that encodes permissions for different users
and uses, which gets executed through authenticated access.

### Impact Exchanges

In this article, we are focusing on the first compnent — the Decentralised
Impact Exchange (DIX). Each DIX encodes in a smart contract the offer to
deliver, fund or evaluate the impacts of a specific intervention project. The
size of project, type of impact, number of participants, value and duration of
the project are all configurable.

A DIX is set up as a unique project that initiates its own independent system of
Ethereum blockchain Smart Contracts. A project sponsor initiates a project DIX
and retains full control over their Smart Contracts.

The main function of the DIX is to coordinate and incentivise participants in a
project to achieve expected impacts through funding, delivering and evaluating
the creation of Verified Impact Data and Proofs of Impact that can be
cryptographically verified.

The DIX governs and facilitates the relationships and value exchanges between
project participants.

### The players

Within each project, there are three generic types of participants:

* **Funding Agents** which includes any institution, financing instrument, or
individual that contributes economic value to an Impact Exchange Project. This
provides for many different ways of funding projects — for instance, through
crowd-funding, bounties, liquid pledging, or other innovations.
* **Service Agents** include organisations and their related agents, or
independent individuals, or devices, such as a vending machine that dispenses
essential commodities for disease prevention.
* **Evaluation Agents **are the organisations, individuals, or software algorithms
that process impact claims to evaluate whether these claims meet the
requirements for issuing a Proof of Impact.

As the ixo Protocol is fully decentralized, the relationships between these
parties can be many-to-many. One or more funding agents can finance a project;
One or more service agents can submit impact claims; And one or more evaluation
agents can verify claims.

These roles are also interchangeable. For instance, a Service Agent could choose
to set up and fund their own project, thereby acting in the Funding Agent role,
to generate Proof of Impact credits that they can subsequently use to recruit
new investors by demonstrating the impacts they are already delivering.

![](https://cdn-images-1.medium.com/max/1600/0*uTTwKs3A_JDhKgEP.)

#### How this works

In the most simple form, a decentralised impact exchange can be conceptualised
as a multi-party escrow Smart Contract. This requires a deposit of value, in the
form of IXO tokens, that is only released by the smart contract during state
transitions, when participating signatories approve transactions.

Let’s look at a simplified example of how this works in practice:

1.  A project sponsor is typically the Funding Agent, but in some contexts this
could be the Evaluation Agent, or Service agent. Using the ixo Portal, the
project sponsor specifies the details for a new Impact Exchange Project. In
this, they define the project description, authorised participants — including
any capabilities the participants must demonstrate, and the Impact Claims
Templates to be used.
1.  To initiate the DIX that will run this project, the sponsor submits a deposit of
(let’s say) 100,000 IXO tokens from their IXO Wallet, to the project’s DIX
address.
1.  Service Agents connect with the project using a mobile application, to accept
the terms of the project and download the project’s Impact Claim Templates. They
will use the application to record delivery of their service by digitally
signing and submitting their Impact Claims. These claims are messaged to a node
on the ixo Network. Third-party developers produce specific end-user
applications that interface with the ixo Network, for their specific use-cases.
1.  An Evaluation Agent connects with the DIX and accepts the specific terms of the
project. Using Agent Software to evaluate the claims that have been submitted,
the agent verifies the claim if the evaluation criteria have been successfully
met. The agent produces a Proof of Impact for the claim. The agent automatically
receives a defined number of IXO tokens for each claim they process, as payment
from the project sponsor.
1.  The Proof of Impact is recorded as a transaction in the Global Impact Ledger.
1.  The Service Agent is paid by the Funding Agent for the successful Impact Claim.
This payment can be made off-chain, using an acceptable payment method , or
peer-to-peer, through the DIX. Proof of Payment is submitted to the DIX and this
triggers a transfer ownership to the project sponsor, who now controls the Proof
of Impact Credit and access to the related data assets.
1.  A small fixed value transaction fee in IXO is automatically paid to the network
node host that received and validated the transaction request.
1.  If the project is processing a Qualifying Impact Claim type, the DIX will mint a
new IXO Token as a protocol reward. The project sponsor receives these new
tokens for each successful Proof of Impact the project produces.

#### Executing Impact Exchanges

Anyone should be able to set up an Impact Exchange Project. The ixo Protocol is
agnostic as to who initiates and sponsors a project. This could be a service
agent, evaluation agent, funding agent, or any other third-party. There are many
use-cases that require each of these sponsorship scenarios. The main
prerequisite is that all the entities must at least be identified with their own
universal [decentralized identifier (DID)](https://w3c-ccg.github.io/did-spec/).

To participate in a project, entities must match the identity and demonstrate
that they have capabilities, such as qualification credentials, that are
specified in the project’s DIX smart contract. For instance, the project might
specify that any service agent that has the credential of a qualified health
professional in a specific jurisdiction, based on a verifiable claim that has
been issued to them by a recognized credentialing authority. This is why the ixo
protocol is rooted in a decentralized identity network. It is a powerful feature
of ixo that all claims resolve to authenticated identities and are based on
provable credentials.

The entity that sets up the project (project sponsor) pays the ixo Network fees
for the project to be executed. At a minimum, this covers the computation costs
of evaluating the Impact Claims through the DIX and the storage costs of the
resultant crypto-asset Impact Credits, that will be permanently recorded in the
Global Impact Ledger.

The DIX can be configured for any combination of evaluation agents and
mechanisms. The criteria for Evaluation Agents to participate in a project can
be restricted to specific identifiers, or to matching identity credentials
(authenticated against verifiable claims of identity). For Evaluation Agents
that call external services to retrieve oracle data or services through DApps,
or using web APIs, the flow of value using IXO tokens should allow for increased
automation in payment processing. This should become a powerful driver for
growing an open marketplace for Impact Evalution services.

#### The ixo Portal

The ixo Portal is a self-hosted browser interface that provides the tools for
users to configure Decentralized Impact Exchanges as new Impact Exchange
Projects.<br> Users can also view and manage their IXO wallet transactions and
interact with the Global Impact Ledger. The portal includes a secure messaging
channel, to interact with project participants and for signed messages, such as
Impact Claims, to be securely passed between trusted participants.

The portal is used to set up Impact Exchange Projects by following a sequence of
logical steps. This starts with a user registering a new project identity,
purpose and scope. The parameters of the project are defined — including the
data model for the impact claims that will be accepted and the evaluation
criteria to be applied. The project is initiated with a deposit of IXO tokens to
a smart contract transaction. This records the blockchain address of the DIX
smart contract in the project document. This information can be displayed on any
web browser and broadcast through all available communication channels,
including decentralised protocols such as Whisper and Swarm. The project data
uses semantic standards, so projects are easily discoverable and can be matched
to suitable participants.

![](https://cdn-images-1.medium.com/max/1600/0*aeG1O7-jxMBD4nUm.)
<span class="figcaption_hack">**The ixo Portal**</span>

Through the Project Portal, users view the status of their projects and manage
communications with the project participants. The portal enables entities to
register, manage and fund their IXO wallet.

#### Earning protocol rewards

A protocol rewards mechanism is built into the DIX. This incentivises bottom-up
use of the ixo Protocol. A limited set of specific impact claims are designated
as Qualifying Claims. These are prioritised because they will promote the
delivery of high-priority Childhood Development impacts. For each successfully
verified Qualifying Claim, the DIX will mint a new IXO token as a reward that is
transferred back to the wallet address of the project sponsor on completion of
the project. We elaborate further on the mechanism in a future article.

What’s really cool is that any project sponsor or external parties can similarly
incentivize the delivery of projects that are important to them, by adding a
bounty, performance bonus or simple reward.

#### A standardised Impact Data model

The DIX smart contract system codifies what impact claims will be evaluated,
which entities are eligible to submit, evaluate and finance the project; the
mechanisms and terms for payment; links to the legal terms; validity period and
other conditions. These parameters are semantically defined within a JSON
document and contextualised to open schema definitions, using linked-data
specifications. The conceptual structure of a project definition document is
shown in the Project Template diagram below.

![](https://cdn-images-1.medium.com/max/1600/0*BK_zaecQrtv8Y_YB.)
<span class="figcaption_hack">**Project Template conceptual design**</span>

The manifest of each project sets out the terms under which the DIX will
operate, such as the project duration. This also defines who is eligible to
participate in the project. Participation is restricted to specific authorised
Funding Agent, Service Agent and Evaluation Agent capabilities. To transact with
the DIX Smart Contract system, these agents must be able to cryptographically
authenticate that they have the required Object Capabilities — for instance,
they must be able to sign the transaction with the valid cryptographic private
key associated with their identifier.

#### P2P payments for Impact services

DIX Smart Contracts can transact payments for services that include the services
delivered by Service Agents and Evaluation Agents. Each payment is specified by
the type of payment (e.g. Crypto-token), method of payment (e.g. out-of-band or
crypto-transaction), terms of payment (e.g. Bounty or fee-for-service) and
condition of payment (e.g. minimum number of claims to be submitted or due-date
to be complied with).

To begin with, ixo could be used more as a coordination and accounting
mechanism, with only a fraction of evaluator fees being transacted through the
DIX, to incentivize evaluation agents to use the protocol. However, over time we
see the full payment for evaluation services being transacted peer-to-peer
through the DIX — especially when these evaluations are conducted by software
agents.

### A decentralised Impact marketplace

IXO provides an open utility for coordinating and incentivising the trade in
Impact Data and associated Proofs of Impact. The protocol is accessed through a
low-cost decentralised network of computational nodes. This provides the data
processing, storage and payment mechanisms to run a truly decentralised,
multi-sided marketplace for the Impact Economy.

### The future of Impact

Using the ixo Protocol should dramatically reduce the costs of collecting and
evaluating Impact Data through automation and crowd-sourcing. The performance of
impact evaluations and resource matching will become increasingly augmented by
machine intelligence that learns from growing Big Impact Data commons. <br> Use
of the protocol should spread through coordinating and incentivizing networks of
service-providers and providers of capital to come together. These new
information and value flows will optimize how Sustainable Development impacts
are delivered and funded through decentralised networks, to accelerate progress
towards the Global Goals.<br> Decentralised Impact Exchanges will be possible at
all levels, as well as through local and global exchanges.

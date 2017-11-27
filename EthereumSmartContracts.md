# Ethereum Smart Contracts

There are a number of smart contracts that need to reside in the public Ethereum network, these mainly have to do with the manaement of the ixt Token.  The ixo token is critical to the ixo ecosystem as it allows for the payment of the ixo network validators as well as the minting of new tokens for incentivising the delivery of key impacts in pursuit of the sustainable development goals set out by the UN.

## Requirements of the Smart Contracts 
### ixo Token
The ixo token is an ERC20 Token.  It will be used for paying the agents involved in the DIX projects.  The total supply of ixo Tokens will be fixed, but tokens will be minted as incentives for certain impacts that are delivered and tokens might be burned when validating node misbehave.

### Token Distribution Contract
The distribution contract is responsible for managing the distribution of the ixo tokens that will be allocated during the presale event and the public token generation event.

### Mint/Burn Auth
This contract contains the rules that define who can trigger the mint and burning of tokens.  This would normally be the validator Voting Contract

### Decentralized Impact Exchange Project
At the core of the ixo protocol is the Decentralixed Impact Exchange Project.  This smart contract manages the stake of ixo tokens allocated to the project and the allocation of ixo tokens that are payable to the different entities involved in the project when certain events occur during the lifecycle of the project. 
The ixo tokens are normally staked by the funding agent and after certain events occur on the project, these tokens are distributed to the funding agent, the service agents and the evaluation agents or any other party incentivised on the project.
The events that cause the payments of ixo tokens are as follows:
- Evaluation of a claim
- Completion of the project

### DIX Auth
This contract contains the rules that define who can trigger the payments.  This would normally be the validator Voting Contract
(This could potentially be merged with **Mint/Burn Auth** contract)

### Validator Voting
This contract is used to coordinate calls from the permissioned ixo network to ensure that there is consensus on any calls made to other ixo smart contracts.

### Validator Proof Of Stake
The validator nodes that validate transactions on the ixo network are required to stake ixo Tokens, which they will lose if they falsely validate a transaction.  The stake is also used to determine how many votes each validator can cast when voting for a block.

## Technology
### Key Principles
- Contracts should be simple
- Contracts should perform one function
- Contracts should be composable
- Contracts should be testable

In order to comply with the above principles we will use the contracts from the [dapp.tools project](https://dapp.tools).  This project contains a number of contracts that will form the building blocks for the smart contracts that the ixo protocol requires.  Where new smart contracts need to be created we will follow a similar philosophy in building them.

We will use the DSAuthority contract to test whether certain function calls can be made by users or other contracts.

![Smart Contract Dependancies](./diagrams/SmartContracts.png)



# B2Lab-TokenPlus
Smart Contract for Token+ (labeled tokens) and Identity Management

## Token+  Generic Implementation

This repository contains a generic implementation of labeled tokens called Token+ by B2Lab.
Token+  is fully adherent to the ERC721 non fungible token standard and implements both the minting and the interface to transfer them between identities registered in a white list. Such identities are stored in a separated Smart Contract that interacts with the main contract. Each registered identity is characterized by attributes such as `name`, `surname`, `biometric data`, etc and can be extended to different additional permissions, for example buying Token+ in Europe, China or Usa. 
The main goal of the development of Token + is to create a Smart Contract that manages labeled tokens from minting to transfer, in order to follow the whole chain of property of each single Token+.  Even the actors of the sale must be registered in a white list that reports the attributes that bind them to physical persons, in order to mitigate the anonymity on the Ethereum Blockchain. In this way it will be possible to approach compliance with regulatory entities making tokenization a tool usable by the traditional financial sector.

## Smart Contract Structure

This repo's contracts are separated in 2 parts:

•	Identity Manager

•	B2Lab Token+

The first part is divided into `IdentityBase` and `IdentityExtended`. The first is composed of a data structure characterized by the attributes `biometricData`, `name` and `surname`, `setMyIdentity` and `checkIdentity` methods. The second is an optional extension of `IdentityBase` which, through the `setIdentityExtended` method, implements three permissions such as: `usePermission`, `euPermission`, `chinaPermission`.

The second part is B2Lab_TokenPlus minting and transfer.  In the minting phase  each token is labeled with a positive autoincremental integer number and additional data (for example, dataA, dataB, dataC).
As previously mentioned, each token can be purchased or transfered only by actors registered in `IdentityBase` (or `IdentityExtended` ).

## Usage

First of all you have to deploy `IdentityBase` ( or `IdentityExtended`  ), than you’ll deploy B2Lab_TokenPlus passing as parameter the address of `IdentityBase` smart contract, in this way you’ll become the owner of the first contract linked to the second.

After you have to register yourself using `setMyIdentity` passing parameters:  `biometricData`, `name`, `surname`. You can now check if your `biometricData` is linked to your personal data using `checkIdentity`, buy and sell Token+.
You can buy a Token+ individually or at most in batches of 100 tokens+ per transaction and transfer till to 10 of them per transaction.

Currently  Token+ suffers some problem related to gas consumption, for this reason we suggest to maintain the limit of 100 Tokens+ and 10 Tokens+ respectively for buying and the transfer.
This type of solution is meant for not too large tokenizations of an asset with the highest value possible.


## Authors

* **B2Lab Team**

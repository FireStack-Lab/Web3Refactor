# Intro

`Web3.js` is an important part of ethereum ecosystem, almost all node.js-based and browser-based apps or services use it.

Tooling for example `Truffle`, and wallet like `MetaMask`, they all start with `Web3.js`.

`Infura.io`, particularly, implemented a lot of features inside `Web3.js`, also including access method to `IPFS`'s storage.

`Web3.js` is more like a multi-eco-system common tools for developers from all sides.

We started porting and migrating `Web3.js` for other pub-chain since mid-2018, and we find that even the developer tools for each pub-chain are different, however the basic parts are somehow similar.

We think it is important to understand these when developing multi-language-sdks

## Basic

- Account model
- Crypto packages for keyGen
- Crypto packages for AES/DES
- BIP39 and BIP44 packages
- Wallet instance for managing accounts
- Signing method for messages and transactions/contracts

## Network

- HttpProvider/WebsocketProvider
- RPCMethods
- Middlewares
- Protobuf/gRPC serializer

## Transactions

- Transaction factory method/class
- Transaction counstructor
- Transaction sender

## Smart-Contracts

- ABI decoder/parser
- Contract factory method/class
- Contract consturctor
- Contract state manager

## Common utils

- Data-type validators
- Data-type transformers
- Unit transformers
- Error handlers

## coinbase package(trading)

## ipfs package(storage)

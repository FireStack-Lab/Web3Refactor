# Intro

`Web3.js` is an important part of ethereum ecosystem, almost all node.js-based and browser-based apps or services use it.

Tooling for example `Truffle`, and wallet like `MetaMask`, they all start with `Web3.js`.

`Infura.io`, particularly, implemented a lot of features inside `Web3.js`, also including access method to `IPFS`'s storage.

`Web3.js` is more like a multi-eco-system common tools for developers from all sides.

We started porting and migrating `Web3.js` for other pub-chain since mid-2018, and we find that even the developer tools for each pub-chain are different, however the basic parts are somehow similar.

## Basic features

- Account model
- Crypto packages for keyGen
- Crypto packages for AES/DES
- Signing methods

## Network features

- HttpProvider/WebsocketProvider
- RPCMethods
- Middlewares
- Protobuf/gRPC serializer

## Transaction related

- Transaction counstructor
- Transaction sender

## Smart-Contract related

- ABI decoder/parser
- Contract consturctor
- Contract state manager

## Common utils

- Data-type validators
- Data-type transformers
- Unit transformers
- Error handlers

## coinbase package(trading)

## ipfs package(storage)

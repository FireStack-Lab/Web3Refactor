## About

1. Priorities from high to low
2. Method name should be defined by Blockchain itself, if we want them to be compatible to different provider like MetaMask, we just use client SDKs to implement(easier).

## For explorers

1. GetChainId
2. GetBlockchainInfo
3. GetLatestBlockNumber
4. GetTransactionByBlockHashAndIndex
5. GetTransactionByBlockNumberAndIndex
6. GetTransactionByHash
7. others...

## For Wallet/extensions

1. GetBalance
2. CreateTransaction
3. CallMessage
4. ...others

## migrate from eth

1. eth_getBlockByHash
2. eth_getBlockByNumber
3. eth_getBlockTransactionCountByHash
4. eth_getBlockTransactionCountByNumber
5. eth_getCode
6. eth_getTransactionByBlockHashAndIndex
7. eth_getTransactionByBlockNumberAndIndex
8. eth_getTransactionByHash
9. eth_syncing
10. net_peerCount
11. eth_getBalance
12. eth_getStorageAt
13. eth_getTransactionCount
14. eth_sendTransaction
15. eth_sendRawTransaction

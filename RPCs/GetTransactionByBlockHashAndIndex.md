# GetTransactionByBlockHashAndIndex

Returns information about a transaction by block hash and transaction index position.

### Request

| Parameter | Type          | Required | Description                               |
| --------- | ------------- | -------- | ----------------------------------------- |
| `id`      | string        | Required | `"1"`                                     |
| `jsonrpc` | string        | Required | `"2.0"`                                   |
| `method`  | string        | Required | `"GetTransactionByBlockHashAndIndex"`     |
| `params`  | Array<string> | Required | `[BLOCK HASH,TRANSACTION INDEX POSITION]` |

#### Request Params

- `BLOCK HASH` _[required]_ - a string representing the hash (32 bytes) of a block
- `TRANSACTION INDEX POSITION` _[required]_ - a hex of the integer representing the position in the block

#### Curl example

```bash
## JSON-RPC over HTTPS POST
## You can also replace mainnet with a different supported network
curl https://devnet.harmony.one \
    -X POST \
    -H "Content-Type: application/json" \
    -d '{"jsonrpc":"2.0","method":"GetTransactionByBlockHashAndIndex","params": ["0xb3b20624f8f0f86eb50dd04688409e5cea4bd02d700bf6e79e9384d47d6a5a35","0x0"],"id":1}'


```

### Response

#### Result fields

- `TRANSACTION` - A transaction object, or null when no transaction was found
  - `hash`: 32 Bytes - hash of the transaction.
  - `nonce`: the number of transactions made by the sender prior to this one.
  - `blockHash`: 32 Bytes - hash of the block where this transaction was in. null when its pending.
  - `blockNumber`: block number where this transaction was in. null when its pending.
  - `transactionIndex`: integer of the transactions index position in the block. null when its pending.
  - `from`: 20 Bytes - address of the sender.
  - `to`: 20 Bytes - address of the receiver. null when its a contract creation transaction.
  - `value`: value transferred in Wei.
  - `gasPrice`: gas price provided by the sender in Wei.
  - `gas`: gas provided by the sender.
  - `input`: the data send along with the transaction.

#### Response Body

```js
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "blockHash": "0xb3b20624f8f0f86eb50dd04688409e5cea4bd02d700bf6e79e9384d47d6a5a35",
    "blockNumber": "0x5bad55",
    "from": "0xfbb1b73c4f0bda4f67dca266ce6ef42f520fbb98",
    "gas": "0x249f0",
    "gasPrice": "0x174876e800",
    "hash": "0x8784d99762bccd03b2086eabccee0d77f14d05463281e121a62abfebcf0d2d5f",
    "input": "0x6ea056a9000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000bd8d7fa6f8cc00",
    "nonce": "0x5e4724",
    "r": "0xd1556332df97e3bd911068651cfad6f975a30381f4ff3a55df7ab3512c78b9ec",
    "s": "0x66b51cbb10cd1b2a09aaff137d9f6d4255bf73cb7702b666ebd5af502ffa4410",
    "to": "0x4b9c25ca0224aef6a7522cabdbc3b2e125b7ca50",
    "transactionIndex": "0x0",
    "v": "0x25",
    "value": "0x0"
  }
}
```

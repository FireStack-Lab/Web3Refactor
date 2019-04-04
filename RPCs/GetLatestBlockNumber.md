# GetLatestBlockNumber

Returns the current "latest" block number.

### Request

| Parameter | Type   | Required | Description              |
| --------- | ------ | -------- | ------------------------ |
| `id`      | string | Required | `"1"`                    |
| `jsonrpc` | string | Required | `"2.0"`                  |
| `method`  | string | Required | `"GetLatestBlockNumber"` |
| `params`  | string | Required | Empty string `""`        |

#### Curl example

```bash
## JSON-RPC over HTTPS POST
## You can also replace mainnet with a different supported network
curl https://devnet.harmony.one \
    -X POST \
    -H "Content-Type: application/json" \
    -d '{"jsonrpc":"2.0","method":"GetLatestBlockNumber","params": [],"id":1}'

```

### Response

#### Result fields

- `BLOCK NUMBER` - a hex code of an integer representing the current block number the client is on.

#### Response Body

```js

  "jsonrpc": "2.0",
  "id": 1,
  "result": "0x65a8db"
}
```

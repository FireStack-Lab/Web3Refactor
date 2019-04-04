# GetLatestBlockNumber

Returns the current "latest" block number.

### REQUEST

`POST https://devnet.harmony.one`

#### HEADERS

`Content-Type: application/json`

#### EXAMPLE

```bash
## JSON-RPC over HTTPS POST
## You can also replace mainnet with a different supported network
curl https://devnet.harmony.one \
    -X POST \
    -H "Content-Type: application/json" \
    -d '{"jsonrpc":"2.0","method":"GetLatestBlockNumber","params": [],"id":1}'

```

### RESPONSE

#### RESULT FIELDS

- `BLOCK NUMBER` - a hex code of an integer representing the current block number the client is on.

#### BODY

```js

  "jsonrpc": "2.0",
  "id": 1,
  "result": "0x65a8db"
}
```

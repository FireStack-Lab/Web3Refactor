# hmy_getBalance

Returns the balance of the account of given address.

### Request

| Parameter | Type   | Required | Description                     |
| --------- | ------ | -------- | ------------------------------- |
| `id`      | string | Required | `"1"`                           |
| `jsonrpc` | string | Required | `"2.0"`                         |
| `method`  | string | Required | `"hmy_getBalance"`              |
| `params`  | Array  | Required | `["ADDRESS","QUANTITY or TAG"]` |

#### Request params

- `ADDRESS` _[required]_ - a string representing the address (20 bytes) to check for balance
- `QUANTITY|TAG` _[required]_ integer block number,or string"latest", "earliest" or "pending"

#### Curl example

```bash
## JSON-RPC over HTTPS POST
## You can also replace mainnet with a different supported network
curl https://devnet.harmony.one \
    -X POST \
    -H "Content-Type: application/json" \
    -d '{"jsonrpc":"2.0","method":"hmy_getBalance","params": ["0xc94770007dda54cF92009BFF0dE90c06F603a09f","latest"],"id":1}'

```

### Response

#### Result fields

- `Balance State`
  - `balance` - integer of the current balance in wei.
  - `nonce` - integer of the current account's nonce

#### Response Body

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": { "balance": "0x2fe84e3113d7b", "nonce": "0x2" }
}
```

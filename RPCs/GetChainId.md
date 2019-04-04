# GetChainId

Returns the currently configured chain id, a value used in replay-protected transaction signing as introduced by EIP-155.

### Request
| Parameter | Type   | Required | Description       |
| --------- | ------ | -------- | ----------------- |
| `id`      | string | Required | `"1"`             |
| `jsonrpc` | string | Required | `"2.0"`           |
| `method`  | string | Required | `"GetChainId"`    |
| `params`  | string | Required | Empty string `""` |

#### Curl example

```bash
## JSON-RPC over HTTPS POST
## You can also replace mainnet with a different supported network
curl https://devnet.harmony.one \
    -X POST \
    -H "Content-Type: application/json" \
    -d '{"jsonrpc":"2.0","method":"GetChainId","params": [],"id":1}'


```

### Response

#### Result Fields

- `QUANTITY` - big integer of the current chain id.

#### Response Body

```js
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "0x1"
}
```

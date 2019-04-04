# GetEstimatedGas

Generates and returns an estimate of how much gas is necessary to allow the transaction to complete. The transaction will not be added to the blockchain. Note that the estimate may be significantly more than the amount of gas actually used by the transaction, for a variety of reasons including EVM mechanics and node performance.


### Request
| Parameter | Type   | Required | Description           |
| --------- | ------ | -------- | --------------------- |
| `id`      | string | Required | `"1"`                 |
| `jsonrpc` | string | Required | `"2.0"`               |
| `method`  | string | Required | `"GetEstimatedGas"`   |
| `params`  | string | Required | `TRANSACTION PAYLOAD` |

#### Request params

- `TRANSACTION PAYLOAD` _[required]_
  - `from`: _[optional]_ 20 Bytes - The address the transaction is sent from.
  - `to`: 20 Bytes - The address the transaction is directed to.
  - `gas`: _[optional]_ Integer of the gas provided for the transaction execution. eth_estimateGas consumes zero gas, but this parameter may be needed by some executions.
  - `gasPrice`: _[optional]_ Integer of the gasPrice used for each paid gas
  - `value`: _[optional]_ Integer of the value sent with this transaction
  - `data`: _[optional]_ Hash of the method signature and encoded parameters. For details see Ethereum Contract ABI

If no gas limit is specified geth uses the block gas limit from the pending block as an upper bound. As a result the returned estimate might not be enough to executed the call/transaction when the amount of gas is higher than the pending block gas limit.

#### Curl example

```bash
## JSON-RPC over HTTPS POST
## You can also replace mainnet with a different supported network
curl https://devnet.harmony.one \
    -X POST \
    -H "Content-Type: application/json" \
    -d '{"jsonrpc":"2.0","method":"GetEstimatedGas","params": [{"from": "0xb60e8dd61c5d32be8058bb8eb970870f07233155","to": "0xd46e8dd67c5d32be8058bb8eb970870f07244567","gas": "0x76c0","gasPrice": "0x9184e72a000","value": "0x9184e72a","data": "0xd46e8dd67c5d32be8d46e8dd67c5d32be8058bb8eb970870f072445675058bb8eb970870f072445675"}],"id":1}'

```

### Response

#### Result fields

- `GAS USED` - the amount of gas used.

#### Response Body

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "0x5cec"
}
```

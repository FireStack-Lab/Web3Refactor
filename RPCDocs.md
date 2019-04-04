# Introduction

[JSON-RPC](https://en.wikipedia.org/wiki/JSON-RPC) is a remote procedure call protocol encoded in JSON. You can use this API to access data from the Harmony nodes.
The JSON-RPC API server runs on:

| Chain(s)            | URL(s)                       |
| ------------------- | ---------------------------- |
| **Harmony devNet**  | https://devnet.harmony.one/  |
| **Harmony mainnet** | https://mainnet.harmony.one/ |
| **Local testnet**   | http://localhost:????/       |

All API calls are POST requests.

## Requests
All requests follow the standard JSON-RPC format and include 4 variables in the data object:

| Data object | Example                                               |
| ----------- | :---------------------------------------------------- |
| `id`        | e.g. `"1"`                                            |
| `jsonrpc`   | e.g. `"2.0"`                                          |
| `method`    | e.g. `"GetBalance"`                                   |
| `params`    | e.g. `["0x0000000000000000000000000000000000000001"]` |

All client sdks follows this patterns, such as:

### curl example
```shell
curl -d '{
    "id": "1",
    "jsonrpc": "2.0",
    "method": "GetBalance",
    "params": ["0x0000000000000000000000000000000000000001"]
}' -H "Content-Type: application/json" -X POST "https://devnet.harmony.one/"
```

### javascript example
```javascript
// in javascript sdk, the request are injected with `id,jsonrpc`, 
// all methods are becoming sub-method to specific classes.
//...
const balance = await harmony.blockchain.getBalance('0x0000000000000000000000000000000000000001');
```

### Suggestion on `Request.params`
1. All params are inside the array, we use comma to separate multiple parameters. like this
```js
    {
        "params":["1","2","3"]
    }
```
2. All params have to be `json-encoded` before sending, for example, we wish to send a transaction object, we have to encode it first.

```javascript
const txnThumbObject=
{
    toAddr:"0x00000",
    amount:"1000000",
}

const encodeBeforeSend=JSON.Stringify(txnThumbObject).replace(/\\"/g, '"');

```

and the request params would be:

```js
    {
        "params":["{"toAddr":"0x00000","amount":"1000000"}"]
    }
```

3. When client encounter data like BigNumber, we should always transform those to `string` before send, like this:
```js
   const amount=new BN(100000);

   const amountToSend= amount.toString()
   
```

## Responses

All responses follows standard JSON-RPC format and included 3 variables int the data object:

| Data object | Example            |
| ----------- | :----------------- |
| `id`        | e.g. `"1"`         |
| `jsonrpc`   | e.g. `"2.0"`       |
| `result`    | e.g. `"123456789"` |

`id` and `jsonrpc` are standard by default, `result` can be different by different method responses.

for single result, like a `string`, can be like this:

```js
{
    "id":"1",
    "jsonrpc":"2.0",
    "result":"123456789"
}
```

for array-like result, we suggest following a collection pattern:

```js
{
    "id":"1",
    "jsonrpc":"2.0",
    "result":[
        {
            "hash":"0x123",
            "timestamp":"00000000000"
        },
        {
            "hash":"0x125",
            "timestamp":"00000000001"
        },
        {
            "hash":"0x126",
            "timestamp":"00000000008"
        }
    ]
}
```

result can be JSON-Object, like this:

```js
{
  "id": "1",
  "jsonrpc": "2.0",
  "result": {
    "hashID": "0x655107c300e86ee6e819af1cbfce097db1510e8cd971d99f32ce2772dcad42f2",
    "amount": "0",
    "gasLimit": "10000",
    "gasPrice": "1000000000",
    "nonce": "20",
    "signature": "0x6DEA9FE535AB3557963CA47323B150979CB7C3990515389AF18AFFDD1049ECF3C5AEB5107A64636A946E75219B9482AFE9C7E1D8E5C59D55A1A28A24C0B877B6",
    "toAddr": "0x0000000000000000000000000000000000000000",
    "version": "131073"
  }
}
```
### Suggestion on `Resonponse.result`

Client-side have different data type to deal with, especially in different client enviorment.

For example, in javascript, the `SAFE_INTEGER` range is `-(253 - 1)` to `253 - 1`, when dealing with BigNumber, especially when blockchain returns value, like gWei, is to big for `js` to dealt with.

To make things easy, we suggest as following.

1. `Int/Uint` always returns with `Stringify` data, like `"10000"` or `"-100"`, don't do `10000` or `-100` directly
2. `Boolean` returns boolean directly. like `true` or `false`, don't use `0/1`,`-1/1` as boolean tag.
3. `Address`/`Hash`/`Signature`...,these are blockchain specific data, we use `0x` prefix string. like this

    ```js
    {
        "address":"0x0000000000000000000000000000000000000001",
        "hash":"0x123",
        "signature":"0x6DEA9FE535AB3557963CA47323B150979CB7C3990515389AF18AFFDD1049ECF3C5AEB5107A64636A946E75219B9482AFE9C7E1D8E5C59D55A1A28A24C0B877B6"
    }
    ```
4. `String` data should be return directly, like we handle the errors:
 
   ```js
    {
        "errorCode":"-100",
        "errorMessage":"Oops, something weird happens",
    }
    ```
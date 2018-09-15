# ethersearch-gem
`gem = go-ethereum-modified`

A modified version of go-ethereum. It supports RPC-API for transaction history,  ERC20 history of an address.

# New RPC
## eth_getHistory
Return recent transactions of given address. The result is in blocktime descending order .
#### Parameters
1. data: Address of account
2. offset: The position of transactions.
3. limit: Total number of transactions.
#### Returns
List of transactions.
#### Examples
Get 10 latest transactions of account `0x59c8e1Cc9c312DDB9FAC89A339e0EEfEe439Fd52`
```
curl -X POST -H "Content-Type: application/json" --data '{"jsonrpc":"2.0","method":"eth_getHistory","params":["0x59c8e1Cc9c312DDB9FAC89A339e0EEfEe439Fd52", 0, 10],"id":3}' http://localhost:8547

```
```
{
    "jsonrpc": "2.0",
    "id": 3,
    "result": {
        "data": [
            {
                "blockNumber": 10566,
                "blockTime": 1534431406,
                "from": "0x2f0036792df25362a2de0bab82b4798657b4bc36",
                "gasPrice": "1",
                "gasUsed": "21000",
                "hash": "0xd8d7740442770335a677c5f50a80ae43526bb93679edc6ea41ecc4ef5e9bdcbb",
                "to": "0xc4c7fc58b37be1b4f2a6230cace76afd47cff748",
                "txIndex": 0,
                "type": 1,
                "value": "10"
            },
            {
                "blockNumber": 10562,
                "blockTime": 1534431394,
                "from": "0x2f0036792df25362a2de0bab82b4798657b4bc36",
                "gasPrice": "1",
                "gasUsed": "21000",
                "hash": "0x432e5dd342e52659c811dc1b88a7781011bf80ede75ac386e5dce03b634510f0",
                "to": "0xc4c7fc58b37be1b4f2a6230cace76afd47cff748",
                "txIndex": 0,
                "type": 1,
                "value": "10"
            }
        ]
    }
}
```

## eth_getERC20TokenHistory
Return recent ERC20 transactions of given address. The result is in blocktime descending order .
#### Parameters
1. account address: Address of account.
1. token address: Address of token.
2. offset: The position of transactions.
3. limit: Total number of transactions.
#### Returns
List of transactions.
#### Examples
Get 10 latest ERC20 transactions of account `0xc4c7fc58b37be1b4f2a6230cace76afd47cff748` at token `0x2d051595aa51a29c6eda4eacafbe79234508ca7c`.

```
curl -X POST -H "Content-Type: application/json" --data '{"jsonrpc":"2.0","method":"eth_getERC20TokenHistory","params":["0xc4c7fc58b37be1b4f2a6230cace76afd47cff748","0x2d051595aa51a29c6eda4eacafbe79234508ca7c",0,10],"id":1}' http://localhost:8547
```
```
"jsonrpc": "2.0",
    "id": 3,
    "result": {
        "data": 
                [
                        {
                            "blockTime": 1533445312,
                            "contract": "0x2d051595aa51a29c6eda4eacafbe79234508ca7c",
                            "from": "0x2f0036792df25362a2de0bab82b4798657b4bc36",
                            "hash": "0xcaebd83e99420ae820ca40a64aa5c5d9106e3fda6db2e75ad8049b93896b10f6",
                            "logIndex": 0,
                            "to": "0xc4c7fc58b37be1b4f2a6230cace76afd47cff748",
                            "txIndex": 0,
                            "type": 0,
                            "value": "9"
                        },
                        {
                            "blockTime": 1533445291,
                            "contract": "0x2d051595aa51a29c6eda4eacafbe79234508ca7c",
                            "from": "0x2f0036792df25362a2de0bab82b4798657b4bc36",
                            "hash": "0x4cd60afdbc966175f2ad3cd51405c6223f3cf179131a3e9cc98525c99ab87a4c",
                            "logIndex": 0,
                            "to": "0xc4c7fc58b37be1b4f2a6230cace76afd47cff748",
                            "txIndex": 1,
                            "type": 0,
                            "value": "99"
                        }
                ]
    }
```
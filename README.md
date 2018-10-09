# BTC - ETH Cross Chain Atomic Swap
#### The project won the Consensys Sponsorship Prize on the [ETHSanFrancisco](https://ethsanfrancisco.com) hackathon. 
#### Created by HU Yao-Chieh, Lee Ting Ting, and Kevin Gau.
We built the CrossChain Swap environments for Bitcoin and Ethereum respectively. We implemented the mvp of the idea as a demo to visualize the BTC/ETH swapping process. Description on project deatils is available on [Devpost](https://devpost.com/software/web-v2-btc) with the [demo video](https://youtu.be/-IsOF69HrBY)

# End-to-end Test Case
1. Open Ethereum private node: `ganache-cli`
1. Open Bitcoin private node (after downloading bitcoin core): 
`bitcoind -txindex -regtest -reindex -rpcpassword=local321 -rpcuser=bitcoin -rpcport=18332`
1. Host the html site on port 9000: 
`serve-https /Users/tingtinglee/hack/WEB-v2-BTC/examples/swap/swap-e2e-local.html -p 9000`
2. In the browser, GOTO https://localhost:9000/examples/swap/_swap-e2e-local.html 
3. Fill in Bitcoin params: 100000 (or any)
4. Click on Generate Secret
## A Initiates SWAP on Bitcoin
4. Copy over Secret Hash to Bitcoin Initiate Swap
5. Click on Initiate Swap
## B Initiates SWAP on Ethereum
6. Fill in Secret Hash at Ethereum Initiate Swap
7. Click on Initiate Swap
## A Claims SWAP on Ethereum
8. Fill in Secret from A
9. Fill in Initiate Transaction Hash from B's Initiation on Ethereum
## B Claims SWAP on Bitcoin
10. Fill in Secret from A
11. Fill in Initiate Transaction Hash from A's Initiation on Bitcoin

# Addresses
* A's BTC address: muWrnsfYwzv24sAuC1t45JssWttHUtA162 
* A's ETH address: 0x5a3df33ebab91eb80712493c8ad30855b882c669
* B's BTC address: muT9jzX9Jws7X9xE6JZkXcNrzNAfQRDaj9
* B's ETH address: 0x1cdf3aac5329aa9d1dee420468a72bad24055885

# Bitcoin tips
## Host Bitcoin private net
```
bitcoind -txindex -regtest -reindex -rpcpassword=local321 -rpcuser=bitcoin -rpcport=18332
```

## Interact with the Bitcoin private net via console
```
bitcoin-cli -rpcpassword=local321 -rpcuser=bitcoin -rpcport=18332 <function_name> <function_param>
```

## Generate a Bitcoin address
```
bitcoin-cli -rpcpassword=local321 -rpcuser=bitcoin -rpcport=18332 getrawchangeaddress "legacy"
```

## get help
```
bitcoin-cli -rpcpassword=local321 -rpcuser=bitcoin -rpcport=18332 help
```

## import private key
```
bitcoin-cli -rpcpassword=local321 -rpcuser=bitcoin -rpcport=18332 importprivkey cVuHNLamShn9pJEVQLy76fdzLPZxgfhenVdK7wo1vBweue4x2dHv
bitcoin-cli -rpcpassword=local321 -rpcuser=bitcoin -rpcport=18332 importprivkey cTYiTKhEujcjM4xqgzRHbpCc9Mbtpvqd8VpsRUB6aXygBgg5JsYp
```

## generate 100 blocks
```
bitcoin-cli -rpcpassword=local321 -rpcuser=bitcoin -rpcport=18332 generate 101
```

## fund an address
```
bitcoin-cli -rpcpassword=local321 -rpcuser=bitcoin -rpcport=18332 sendtoaddress muT9jzX9Jws7X9xE6JZkXcNrzNAfQRDaj9 10
```

# Examine on console
## Check bitcoin balance
```
bitcoin.getBalance(["muT9jzX9Jws7X9xE6JZkXcNrzNAfQRDaj9"]).then(console.log)
```

## Chain Abstraction Layer <img align="right" src="./liquality-logo.png" height="80px" />

[![ChainAbstractionLayer](https://travis-ci.org/liquality/chainabstractionlayer.svg?branch=master)](https://travis-ci.org/liquality/chainabstractionlayer)
[![Standard Code Style](https://img.shields.io/badge/codestyle-standard-brightgreen.svg)](https://github.com/standard/standard)
[![MIT License](https://img.shields.io/badge/license-MIT-brightgreen.svg)](./LICENSE.md)
[![ChainAbstractionLayer](https://img.shields.io/npm/dt/chainabstractionlayer.svg)](https://npmjs.com/package/chainabstractionlayer)

> :warning: This project is under heavy development. Expect bugs & breaking changes.

Query different blockchains with a single and simple interface.


## Installation

```bash
npm install @liquality/chainabstractionlayer
```

> **Error: Cannot find module 'babel-runtime/core-js/get-iterator'**
>
> Issues to track: [LedgerHQ/ledgerjs/issues/211](https://github.com/LedgerHQ/ledgerjs/issues/211), [LedgerHQ/ledgerjs/issues/218](https://github.com/LedgerHQ/ledgerjs/issues/218)
>
> `npm install babel-runtime`


## Usage

```javascript
import { Client, providers } from '@liquality/chainabstractionlayer'

const { BitcoinRPCProvider } = providers.bitcoin

const bitcoin = new Client()
bitcoin.addProvider(new BitcoinRPCProvider('http://localhost:8080', 'bitcoin', 'local321'))

bitcoin
  .generateBlock(1) // returns Promise
  .then(console.log) // Array<BlockHash>
```

## Community

[Liquality Gitter](https://gitter.im/liquality/Lobby?source=orgpage)

### Try ChainAbstractionLayer in Browser

<table>
  <thead>
    <tr>
      <th>Chain</th>
      <th>Wallet Provider</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td rowspan=2>Ethereum</td>
      <td>Ledger</td>
      <td>
        <a href="./examples/browser/ethereum/ledger.html">Source</a>
        &amp;
        <a href="https://liquality.github.io/chainabstractionlayer/examples/browser/ethereum/ledger.html">Demo</a>
      </td>
    </tr>
    <tr>
      <td>MetaMask</td>
      <td>
        <a href="./examples/browser/ethereum/metamask.html">Source</a>
        &amp;
        <a href="https://liquality.github.io/chainabstractionlayer/examples/browser/ethereum/metamask.html">Demo</a>
      </td>
    </tr>
    <tr>
      <td>Bitcoin</td>
      <td>Ledger</td>
      <td>
        <a href="./examples/browser/bitcoin/ledger.html">Source</a>
        &amp;
        <a href="https://liquality.github.io/chainabstractionlayer/examples/browser/bitcoin/ledger.html">Demo</a>
      </td>
    </tr>
  </tbody>
</table>


## Documentation

The documentation is being generated by [esdoc](https://www.npmjs.com/package/esdoc). Github Page hosted documentation is available at [liquality.github.io/chainabstractionlayer](https://liquality.github.io/chainabstractionlayer/)

If you want to build documentation locally;

```bash
npm run build:docs
```


## License

[MIT](./LICENSE.md)

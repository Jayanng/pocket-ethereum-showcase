# Showcase: Ethereum Mainnet JSON-RPC, via Pocket Network

A real listed Pocket service, shown working live. No wallet, no API key, no payment.

## The service

- **Name:** Ethereum Mainnet JSON-RPC
- **Listed at:** https://agent.pocket.network/services
- **Endpoint:** https://eth.api.pocket.network
- **Protocol:** JSON-RPC over HTTPS, read-only
- **Auth:** none on the public endpoint. The public endpoint answers without a key and without payment.
- **Two routes, one service:** the portal route `POST https://agent.pocket.network/v1/eth` is $0.005 per call, paid with x402. This showcase uses the free Pocket Foundation public endpoint `https://eth.api.pocket.network` for the same service, key-free and unpaid, so no purchase is needed to repeat it.
- **What it does:** answers standard Ethereum JSON-RPC calls, served by Pocket Network's decentralised supplier set.

## How to call it

One POST per call, with a JSON body. This is the exact shape used in the walkthrough:

```bash
curl -X POST https://eth.api.pocket.network \
  -H "Content-Type: application/json" \
  -d '{"jsonrpc":"2.0","id":1,"method":"eth_chainId","params":[]}'
```

## The five calls, with real results

All five were run live on 2026-11-22 at 17:00 UTC. The exact requests and responses are in `evidence.json`. Every number below came from a real live call.

| # | Call | What it asks | Live answer | What it means |
|---|------|--------------|-------------|---------------|
| 1 | `eth_chainId` | Which chain is this? | `0x1` | Chain 1, Ethereum mainnet. One number proves you reached the right chain. |
| 2 | `eth_blockNumber` | What is the latest block? | `0x193ee48` | Block 26,472,008. Run it twice and the number moves forward. |
| 3 | `eth_gasPrice` | What does the network charge right now? | `0x7b835dc` | 129,512,924 wei, about 0.13 gwei. |
| 4 | `eth_getBalance` | What is the balance of vitalik.eth? | `0x507c30d79341ec0a` | 5.7996 ETH, at the public address `0xd8dA6BF26964aF9D7eEd9e03E53415D37aA96045`. |
| 5 | `eth_getBlockTransactionCountByNumber` | How many transactions in the latest block? | `0xfd` | 253 transactions. |

Result: 5 of 5 calls answered live, 0 failed.

## The walkthrough

- **Video:** `pocket-service-showcase.mp4`, 60 to 90 seconds. It opens the showcase page, runs all five calls live, and shows each answer on screen as it arrives.
- **Screenshots:** in `screenshots/`, one per meaningful step.
- **Live page:** `showcase.html`. Open it in a browser and press "Run the live calls" to repeat the whole walkthrough yourself, against the same public endpoint.

## Why this service

It is the flagship Pocket service, it is listed, it works live with no key and no payment, and its answers are visible and checkable: a chain ID, a block height that advances, a gas price, a public balance, and a transaction count. Anyone can re-run every call above with curl and get a live answer.

## What is not in here

No fabricated calls. No paid purchase. No API key. The balance is for a public address, and no private data appears anywhere in this package.

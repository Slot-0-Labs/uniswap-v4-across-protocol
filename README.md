# 🔄 Cross-Chain Swap Hook with Uniswap V4 and Across Protocol 🔄
## Uniswap V4 🦄

Uniswap V4 is a non-custodial, non-upgradeable, and permissionless Automated Market Maker (AMM) protocol built on the Ethereum Virtual Machine (EVM). It introduces several architectural changes and features that improve upon the AMM model built in Uniswap V1 and V2, and the concentrated liquidity model introduced in Uniswap V3. Key features include hooks, singleton, flash accounting, and native ETH support. 🌟

## Across Protocol 🌉

Across Protocol is a trust-minimized bridge for transferring assets between Ethereum and its Layer 2s. It uses a network of relayers and an Optimistic Oracle to ensure that transfers are secure and efficient. The protocol also introduces a unique UBA Fee Model to balance liquidity across chains. 💸

## Cross-Chain Swapping with Uniswap V4 and Across Protocol 🔀

The Cross-Chain Swap Hook leverages the features of Uniswap V4 and Across Protocol to enable efficient cross-chain swaps. Here's a step-by-step process of how it works:

1. **User initiates a swap on Chain A** in a Uniswap V4 pool with the Cross-Chain Swap Hook.
2. The **beforeSwap hook on Chain A triggers**, initiating a bridge transfer from Chain A to Chain B via Across Protocol.
3. **Relayers in the Across Protocol ecosystem** provide the equivalent amount of tokens to the user on Chain B.
4. The **beforeSwap hook on Chain B triggers**, executing the swap using the tokens provided by the relayer.
5. The **afterSwap hook on Chain B triggers**, performing any necessary actions after the swap.
6. A **proof of the swap** and the validity of the original deposit is submitted to the Optimistic Oracle in the Across Protocol, and the relayer is reimbursed.
7. The **afterSwap hook on Chain A triggers**, performing any necessary actions after the swap.

## Flash Accounting in Cross-Chain Swapping 💡
Uniswap V4 and Across Protocol can be combined to facilitate cross-chain swapping by leveraging the flash accounting feature of Uniswap V4. In this setup, a user initiates a swap on Chain A in a Uniswap V4 pool. The tokens provided by the user are temporarily stored in the pool, creating a positive balance delta. This swap triggers a bridge transfer via Across Protocol to Chain B, where the equivalent amount of tokens are provided to the user, creating a negative balance delta. The balance deltas are local to each chain and do not need to be zero across chains. Instead, each chain ensures that its balance delta is zero at the end of each transaction, adhering to the principles of flash accounting. This allows for efficient cross-chain swaps while maintaining the integrity of the Uniswap V4 pools on both chains.


## Current Concerns/Issues 🚩

- **Handling of balance deltas:** Ensuring the balance delta on each chain is zero at the end of each transaction.
- **High gas costs:** Cross-chain transfers involve multiple transactions and state updates, which can be expensive.
- **Balancing of liquidity pools:** An imbalance in the pools could lead to slippage or other undesirable effects.
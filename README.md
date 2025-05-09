# BitYield: Decentralized Yield Aggregator on Stacks

**BitYield** is a decentralized, composable, and intelligent yield aggregator built on the Stacks Layer 2 blockchain. It automatically allocates user funds across the best-performing DeFi strategies within the Stacks ecosystem, optimizing returns through data-driven allocation and strategy management.

## Overview

BitYield smart contracts implement an autonomous system for:

* **Automated Yield Optimization**
* **Decentralized Strategy Management**
* **SIP-010 Tokenized Shares**
* **Governance & Access Control**
* **Emergency Shutdown & Risk Controls**

Each user deposit is tokenized into BitYield (BYT) shares that represent their stake in the vault, and the vault rebalances funds dynamically toward top-performing strategies based on APY and risk scores.

## Features

* **SIP-010 Token Standard**: Users receive share tokens representing their deposits.
* **Automated Strategy Allocation**: Dynamically assigns funds to the best APY-generating strategies.
* **Strategy Governance**: Admins can add, configure, enable/disable strategies.
* **Risk-Aware Optimization**: Considers APY, TVL, and risk scores during allocation.
* **Secure & Permissioned**: Strict owner-only functions for sensitive operations.
* **Emergency Mode**: Pause operations instantly in case of threats.

## Smart Contract Structure

### Key Modules

* **Strategies Map**: Stores yield strategies and their metadata.
* **UserDeposits Map**: Tracks individual user deposits and share balances.
* **StrategyAllocations Map**: Controls allocation constraints per strategy.
* **Admin Controls**: Add strategies, toggle emergency mode, update APYs.

## Getting Started

### Prerequisites

* [Clarity Language](https://docs.stacks.co/docs/write-smart-contracts/clarity-overview)
* Stacks CLI or Clarity IDE
* SIP-010-compatible token contract

### Deployment

1. Set your token contract via `set-token-contract`.
2. Add yield strategies via `add-strategy`.
3. Users can start depositing using the `deposit` function.

## Functions Overview

### User-Facing

| Function                  | Description                                 |
| ------------------------- | ------------------------------------------- |
| `deposit`                 | Deposit SIP-010 tokens and receive shares   |
| `withdraw`                | Redeem shares for proportional token amount |
| `get-user-info`           | View user-specific deposit data             |
| `get-strategy-info`       | View metadata of a given strategy           |
| `calculate-best-strategy` | View optimal strategy based on APY          |

### Admin-Only

| Function                    | Description                           |
| --------------------------- | ------------------------------------- |
| `add-strategy`              | Add a new yield strategy              |
| `update-strategy-apy`       | Update the APY of a strategy          |
| `toggle-emergency-shutdown` | Enable/disable protocol functionality |
| `set-token-contract`        | Define which SIP-010 token to accept  |

## Tokenomics

* **BYT Token**: Represents shares in the vault.
* **Fees**:

  * **Performance Fee**: 2% (default)
  * **Management Fee**: 1% (default)

> Fees can be modified in future iterations for dynamic governance.

---

## Security Considerations

* **Access Control**: Only contract owner can perform sensitive actions.
* **Reentrancy Protection**: Critical functions use safety checks.
* **Emergency Shutdown**: Halts deposits/withdrawals to prevent damage during attacks.

## Technical Specs

* **Language**: Clarity
* **Stacks Compatibility**: SIP-010 compliant
* **Contract Name**: `bityield`
* **Version**: 1.0.0
* **Author**: BitYield Labs

## Example Usage

```clojure
;; Deposit 100 tokens
(deposit token-contract u100)

;; Withdraw 50 share tokens
(withdraw token-contract u50)

;; Check best strategy
(calculate-best-strategy u500)
```

## Contributing

We welcome community contributions! Please fork the repo, make your changes, and open a PR. For larger proposals, feel free to open an issue or contact BitYield Labs.
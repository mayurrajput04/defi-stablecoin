# 🚀 Decentralized Stablecoin (DSC) - Your Gateway to Stability!

## 🌟 Overview

The **Decentralized Stablecoin (DSC)** is a next-gen, overcollateralized stablecoin inspired by DAI but with **zero governance fees**! 

Powered by **ETH & BTC collateral**, it ensures **price stability** using an advanced minting and burning mechanism. 

The system is secured by **Chainlink oracles** and includes **fail-safe liquidation protections** to keep everything running smoothly. 💪

## 🔥 Features

- **Overcollateralized Stability**: Backed by ETH & BTC for a robust peg.
- **Smart Minting & Burning**: Fully algorithmic & trustless.
- **Rock-Solid Price Feeds**: Chainlink-powered oracles ensure reliable data.
- **Failsafe Mechanisms**: No risky trades—only secure transactions!
- **Bulletproof Testing**: Unit tests, fuzz testing, and mocks for complete reliability.

---

## 🚀 Installation & Setup

### 📌 Prerequisites

Before diving in, ensure you have:

- [Foundry](https://github.com/foundry-rs/foundry) 🛠️ (Solidity dev toolkit)
- Node.js & npm (for extra scripting magic ✨)
- A private Ethereum testnet (Anvil, Hardhat, or Sepolia)

### 🛠️ Clone the Repository

```bash
git clone https://github.com/mayurrajput04/defi-stablecoin
cd defi-stablecoin
```

### 📦 Install Dependencies

```bash
forge install
```

---

## 🔍 Smart Contract Breakdown

### 🎯 **DecentralizedStableCoin.sol** (The Stablecoin)

- ERC20-based stablecoin, **minting/burning restricted** to `DSCEngine`.
- **Burnable** for controlled supply management.
- Ownership **transferred to `DSCEngine`** to prevent abuse.

### 🏗️ **DSCEngine.sol** (The Powerhouse)

- Manages **collateral deposits, redemptions, and minting.**
- Implements **liquidation protection** to avoid depegging risks.
- Uses **Chainlink price feeds** to fetch real-time collateral values.
- Ensures users stay above the **liquidation threshold**.

### 📡 **OracleLib.sol** (The Truth Teller)

- **Chainlink-powered price feeds** ensure up-to-date asset values.
- **Prevents outdated data usage** with built-in freshness checks.

---

## 🏦 How to Use DSC

### 💰 **Minting DSC** (Get Your Stablecoins!)

- Deposit **WETH or WBTC** as collateral.
- Ensure you meet the **overcollateralization ratio**.
- Call `depositCollateralAndMintDsc()` in `DSCEngine`.

### 🔄 **Redeeming Collateral** (Get Back Your Assets!)

- Burn **DSC** equal to the collateral value.
- Call `redeemCollateralForDsc()` in `DSCEngine`.

### ⚠️ **Liquidation Protection**

- If a user’s **health factor** falls below `1.0`, liquidation kicks in to protect the system.

---

## 🧪 Testing DSC Like a Pro!

### 🛠️ **Run Unit Tests**

```bash
forge test --match-path test/unit/*
```

### 🔀 **Run Fuzz Tests**

```bash
forge test --match-path test/fuzz/*
```

### 🚀 **Run All Tests**

```bash
forge test
```

---

## 📤 Deployment Guide

### 🏗️ **Deploy Using Foundry**

```bash
forge script script/DeployDSC.s.sol --rpc-url <YOUR_RPC_URL> --broadcast
```

### ✅ **Verify Deployment**

```bash
forge verify-contract <CONTRACT_ADDRESS> <CONTRACT_NAME> --etherscan-api-key <YOUR_KEY>
```

---

## 🤝 Contribute & Build With Me!

I love contributions! Follow these simple steps:

- **Fork the repository**.
- **Create a new feature branch**.
- **Commit your changes with great messages**.
- **Submit a pull request**—let's make DSC stronger together! 💪

---

## 📜 License

This project is **open-source** and available under the **MIT License**. 🎉


# Decentralized Stablecoin (DSC)

## Overview
The Decentralized Stablecoin (DSC) project is an overcollateralized stablecoin system inspired by DAI but without governance or fees. It ensures price stability through an algorithmic minting and burning mechanism, backed by ETH and BTC collateral. The system is secured using Chainlink oracles and includes robust liquidation protections.

## Features
- **Overcollateralized Stablecoin**: Backed by ETH and BTC to maintain stability.
- **Algorithmic Minting & Burning**: Ensures price peg via `DSCEngine`.
- **Chainlink Oracles**: Secure and reliable price feeds to prevent manipulation.
- **Failsafe Mechanisms**: Prevents minting/burning if price feeds fail.
- **Extensive Testing**: Includes unit tests, fuzz testing, and mock contracts.

---
## Installation & Setup

### Prerequisites
Ensure you have the following installed:
- [Foundry](https://github.com/foundry-rs/foundry) (Solidity development toolkit)
- Node.js & npm (for scripting if needed)
- A private Ethereum testnet or fork (e.g., Anvil, Hardhat, or Sepolia)

### Clone the Repository
```bash
git clone https://github.com/mayurrajput04/defi-stablecoin
cd defi-stablecoin-main
```

### Install Dependencies
```bash
forge install
```

---
## Smart Contract Details

### **DecentralizedStableCoin.sol** (Stablecoin Contract)
- Implements an ERC20-based stablecoin with minting/burning restricted to `DSCEngine`.
- Uses `ERC20Burnable` to allow token burning.
- Ownership is transferred to `DSCEngine`.

### **DSCEngine.sol** (Core Protocol Engine)
- Manages collateral deposits and redemptions.
- Implements liquidation mechanisms for undercollateralized positions.
- Uses Chainlink price feeds to fetch collateral values.
- Ensures users maintain a health factor above liquidation thresholds.

### **OracleLib.sol** (Price Oracle Library)
- Interfaces with Chainlink price feeds (`AggregatorV3Interface`).
- Ensures oracle price freshness to prevent outdated data usage.

---
## Usage Guide

### **Minting DSC**
To mint DSC, a user must:
1. Deposit WETH or WBTC as collateral.
2. Ensure they meet the overcollateralization requirement.
3. Call `depositCollateralAndMintDsc()` in `DSCEngine`.

### **Redeeming Collateral**
To redeem collateral, a user must:
1. Burn DSC equal to the redeemed value.
2. Call `redeemCollateralForDsc()` in `DSCEngine`.

### **Liquidation Process**
If a user's health factor falls below `1.0`, their collateral is liquidated to maintain system solvency.

---
## Testing

### **Run Unit Tests**
```bash
forge test --match-path test/unit/*
```

### **Run Fuzz Tests**
```bash
forge test --match-path test/fuzz/*
```

### **Run All Tests**
```bash
forge test
```

---
## Deployment Guide

### **Deploy Using Foundry**
```bash
forge script script/DeployDSC.s.sol --rpc-url <YOUR_RPC_URL> --broadcast
```

### **Verify Deployment**
```bash
forge verify-contract <CONTRACT_ADDRESS> <CONTRACT_NAME> --etherscan-api-key <YOUR_KEY>
```

---
## Contribution
Contributions are welcome! Please follow these steps:
1. Fork the repository.
2. Create a feature branch.
3. Commit your changes with detailed messages.
4. Submit a pull request.

---
## License
This project is open-source and available under the MIT License.


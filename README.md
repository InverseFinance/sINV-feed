# sINV Price Feed

A collection of Chainlink-compatible price feed contracts to build sINV price feed.

## Overview

This repository contains three main price feed contracts:

### ERC4626Feed

A generalized price feed for ERC4626 vaults that converts a normalized asset/USD price to the vault share/USD price using the vault's exchange rate.

- Combines an underlying feed with ERC4626 vault rate
- Uses `previewRedeem` with fallback to `convertToAssets` for rate calculation
- Returns prices in 18 decimals

### DynamicFeeCurveFeed

A combined Chainlink and Curve price oracle that accounts for dynamic trading fees.

- Fetches paired token/USD price from a Chainlink feed
- Uses Curve pool's `price_oracle()` for asset/paired-token rate
- Applies dynamic fee discount (capped at configurable `maxFee`)
- Supports governance for fee parameter updates

### NormalizedPriceFeed

A wrapper that normalizes Chainlink feed prices to 18 decimals with optional fallback support.

- Normalizes any Chainlink feed to 18 decimal precision
- Supports fallback feed for stale price handling
- Includes price boundary checks via aggregator min/max answers

## Installation

```shell
forge install
```

## Usage

### Build

```shell
forge build
```

### Test

```shell
forge test
```

### Format

```shell
forge fmt
```

## Dependencies

- [OpenZeppelin Contracts](https://github.com/OpenZeppelin/openzeppelin-contracts) - ERC4626, ERC20 interfaces
- [Solmate](https://github.com/transmissions11/solmate) - FixedPointMathLib
- [Forge Std](https://github.com/foundry-rs/forge-std) - Testing utilities

## License

MIT

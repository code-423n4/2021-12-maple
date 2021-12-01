

# Maple Finance contest details
- $67,500 USDC main award pot
- $7,500 USDC gas optimization award pot
- Join [C4 Discord](https://discord.gg/code4rena) to register
- Submit findings [using the C4 form](https://code4rena.com/contests/2021-12-maple-finance-contest/submit)
- [Read our guidelines for more details](https://docs.code4rena.com/roles/wardens)
- Starts December 2, 2021 00:00 UTC
- Ends December 8, 2021 23:59 UTC


Hi everyone!

The following repos are included in the audit, all with release tags that correspond to this audit:

- [maple-labs/debt-locker](https://github.com/maple-labs/debt-locker/releases/tag/v2.0.0-beta.1)
- [maple-labs/erc20-helper](https://github.com/maple-labs/erc20-helper/releases/tag/v1.0.0-beta.1)
- [maple-labs/liquidations](https://github.com/maple-labs/liquidations/releases/tag/v1.0.0-beta.1)
- [maple-labs/loan](https://github.com/maple-labs/loan/releases/tag/v2.0.0-beta.1)
- [maple-labs/maple-proxy-factory](https://github.com/maple-labs/maple-proxy-factory/releases/tag/v1.0.0-beta.1)
- [maple-labs/proxy-factory](https://github.com/maple-labs/proxy-factory/releases/tag/v1.0.0-beta.1)

These contracts include inheritance, so the scope of the audit will be expressed as the contracts at the lowest end of the hierarchy, as these are what will be deployed to mainnet. Since there are no external libraries used, all of the code that these flattened contracts use is in scope for audit.

## `maple-labs/debt-locker`
- DebtLocker.sol
- DebtLockerFactory.sol
- DebtLockerInitializer.sol

## `maple-labs/liquidations`
- Liquidator.sol
- SushiswapStrategy.sol
- UniswapV2Strategy.sol

## `maple-labs/loan`
- MapleLoan.sol
- MapleLoanFactory.sol
- MapleLoanInitializer.sol
- Refinancer.sol

## Focus Areas
- Proxy pattern: check if only allows correct deployments and desired upgrades. 
- Liquidation module: check if the opens to malicious keepers to take advantage of this module. 
- Loan accounting: check if the loan correctly accounts for payments, fees, interest, etc.  

It is recommended to clone our integration testing repo [contract-test-suite](https://github.com/maple-labs/contract-test-suite) locally in order to provide clearer context with how these contracts interact with the rest of the protocol.

In all repos, all dependencies can be found in the `./modules` directory. All repo READMEs include instructions on how to get the environment up and running for testing.

All technical documentation related to this release will be located in the `maple-labs/loan` [wiki](https://github.com/maple-labs/loan/wiki). Some information may move to other wikis over the course of the audit, but we will explicitly communicate these changes if/when they are made.

## Observations

In the wiki, there's a page called [List of Assumptions](https://github.com/maple-labs/loan/wiki/List-of-Assumptions) which outlines some basic terms that we assume that will always hold true. Therefore any issue that breaks this assumptions will likely be considered invalid.

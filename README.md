# ✨ So you want to sponsor a contest

This `README.md` contains a set of checklists for our contest collaboration.

Your contest will use two repos: 
- **a _contest_ repo** (this one), which is used for scoping your contest and for providing information to contestants (wardens)
- **a _findings_ repo**, where issues are submitted. 

Ultimately, when we launch the contest, this contest repo will be made public and will contain the smart contracts to be reviewed and all the information needed for contest participants. The findings repo will be made public after the contest is over and your team has mitigated the identified issues.

Some of the checklists in this doc are for **C4 (🐺)** and some of them are for **you as the contest sponsor (⭐️)**.

---

# Contest setup

## 🐺 C4: Set up repos
- [X] Create a new private repo named `YYYY-MM-sponsorname` using this repo as a template.
- [ ] Get GitHub handles from sponsor.
- [ ] Add sponsor to this private repo with 'maintain' level access.
- [X] Send the sponsor contact the url for this repo to follow the instructions below and add contracts here. 
- [ ] Delete this checklist and wait for sponsor to complete their checklist.

## ⭐️ Sponsor: Provide contest details

Under "SPONSORS ADD INFO HERE" heading below, include the following:

- [x] Name of each contract and:
  - [ ] lines of code in each
  - [ ] external contracts called in each
  - [ ] libraries used in each
- [ ] Describe any novel or unique curve logic or mathematical models implemented in the contracts
- [ ] Does the token conform to the ERC-20 standard? In what specific ways does it differ?
- [ ] Describe anything else that adds any special logic that makes your approach unique
- [x ] Identify any areas of specific concern in reviewing the code
- [ ] Add all of the code to this repo that you want reviewed
- [ ] Create a PR to this repo with the above changes.

---

# ⭐️ Sponsor: Provide marketing details

- [ ] Your logo (URL or add file to this repo - SVG or other vector format preferred)
- [ ] Your primary Twitter handle
- [ ] Any other Twitter handles we can/should tag in (e.g. organizers' personal accounts, etc.)
- [ ] Your Discord URI
- [ ] Your website
- [ ] Optional: Do you have any quirks, recurring themes, iconic tweets, community "secret handshake" stuff we could work in? How do your people recognize each other, for example? 
- [ ] Optional: your logo in Discord emoji format

---

# Contest prep

## 🐺 C4: Contest prep
- [X] Rename this repo to reflect contest date (if applicable)
- [X] Rename contest H1 below
- [X] Add link to report form in contest details below
- [X] Update pot sizes
- [X] Fill in start and end times in contest bullets below.
- [X] Move any relevant information in "contest scope information" above to the bottom of this readme.
- [ ] Add matching info to the [code423n4.com public contest data here](https://github.com/code-423n4/code423n4.com/blob/main/_data/contests/contests.csv))
- [ ] Delete this checklist.

## ⭐️ Sponsor: Contest prep
- [ ] Make sure your code is thoroughly commented using the [NatSpec format](https://docs.soliditylang.org/en/v0.5.10/natspec-format.html#natspec-format).
- [ ] Modify the bottom of this `README.md` file to describe how your code is supposed to work with links to any relevent documentation and any other criteria/details that the C4 Wardens should keep in mind when reviewing. ([Here's a well-constructed example.](https://github.com/code-423n4/2021-06-gro/blob/main/README.md))
- [ ] Please have final versions of contracts and documentation added/updated in this repo **no less than 8 hours prior to contest start time.**
- [ ] Ensure that you have access to the _findings_ repo where issues will be submitted.
- [ ] Promote the contest on Twitter (optional: tag in relevant protocols, etc.)
- [ ] Share it with your own communities (blog, Discord, Telegram, email newsletters, etc.)
- [ ] Optional: pre-record a high-level overview of your protocol (not just specific smart contract functions). This saves wardens a lot of time wading through documentation.
- [ ] Designate someone (or a team of people) to monitor DMs & questions in the C4 Discord (**#questions** channel) daily (Note: please *don't* discuss issues submitted by wardens in an open channel, as this could give hints to other wardens.)
- [ ] Delete this checklist and all text above the line below when you're ready.

---

# Maple Finance contest details
- $67,500 USDC main award pot
- $7,500 USDC gas optimization award pot
- Join [C4 Discord](https://discord.gg/code4rena) to register
- Submit findings [using the C4 form](https://coderena.com/contests/2021-12-maple-finance-contest/submit)
- [Read our guidelines for more details](https://docs.code4rena.com/roles/wardens)
- Starts December 2, 2021 00:00 UTC
- Ends December 8, 2021 23:59 UTC


Hi everyone!

The following repos are included in the audit, all with release tags that correspond to this audit:

- [maple-labs/debt-locker](https://github.com/maple-labs/debt-locker/releases/tag/v2.0.0-beta.0)
- [maple-labs/erc20-helper](https://github.com/maple-labs/erc20-helper/releases/tag/v1.0.0-beta.1)
- [maple-labs/liquidations](https://github.com/maple-labs/liquidations/releases/tag/v1.0.0-beta.1)
- [maple-labs/loan](https://github.com/maple-labs/loan/releases/tag/v2.0.0-beta.0)
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

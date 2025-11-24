# Merkl audit details
- Total Prize Pool: $18,000 in USDC
    - HM awards: up to $14,400 in USDC
        - If no valid Highs or Mediums are found, the HM pool is $0
    - QA awards: $600 in USDC
    - Judge awards: $2,500 in USDC
    - Scout awards: $500 in USDC
- [Read our guidelines for more details](https://docs.code4rena.com/competitions)
- Starts November 25, 2025 20:00 UTC
- Ends December 1, 2025 20:00 UTC

### ❗ Important notes for wardens
1. A coded, runnable PoC is required for all High/Medium submissions to this audit. 
    - This repo includes a basic template to run the test suite.
    - PoCs must use the test suite provided in this repo.
    - Your submission will be marked as Insufficient if the POC is not runnable and working with the provided test suite.
    - Exception: PoC is optional (though recommended) for wardens with signal ≥ 0.68.
1. Judging phase risk adjustments (upgrades/downgrades):
    - High- or Medium-risk submissions downgraded by the judge to Low-risk (QA) will be ineligible for awards.
    - Upgrading a Low-risk finding from a QA report to a Medium- or High-risk finding is not supported.
    - As such, wardens are encouraged to select the appropriate risk level carefully during the submission phase.

## V12 findings

[V12](https://v12.zellic.io/) is [Zellic](https://zellic.io)'s in-house AI auditing tool. It is the only autonomous Solidity auditor that [reliably finds Highs and Criticals](https://www.zellic.io/blog/introducing-v12/). All issues found by V12 will be judged as out of scope and ineligible for awards.

V12 findings will be posted in this section within the first two days of the competition.  

## Publicly known issues

_Anything included in this section is considered a publicly known issue and is therefore ineligible for awards._

Merkl operates as a centralized solution. Therefore, any issues related to the contract owner's administrative access should be considered out of scope.
Additionally, the following assumptions underpin the system's security model:

- The dispute resolution mechanism functions as intended
- Active monitoring bots continuously verify reward distributions through Merkl

We acknowledge a known risk: When users designate a smart contract as their reward recipient and pass data to it, their rewards are potentially vulnerable if:

- The recipient contract is misconfigured or malicious
- The user submits incorrect parameters (such as executing a swap without slippage protection)

In such cases, the recipient contract could redirect or capture the user's rewards.

# Overview

[ ⭐️ SPONSORS: add info here ]

## Links

- **Previous audits:**  https://code4rena.com/reports/2023-06-angle
- **Documentation:** https://docs.merkl.xyz
- **Website:** https://merkl.xyz/
- **X/Twitter:** https://x.com/merkl_xyz

---

# Scope

*See [scope.txt](https://github.com/code-423n4/2025-11-merkl/blob/main/scope.txt)*

### Files in scope


| File   | Logic Contracts | Interfaces | nSLOC | Purpose | Libraries used |
| ------ | --------------- | ---------- | ----- | -----   | ------------ |
| /contracts/DistributionCreator.sol | 1| **** | 333 | |@openzeppelin/contracts-upgradeable/security/ReentrancyGuardUpgradeable.sol<br>@openzeppelin/contracts/token/ERC20/extensions/IERC20Metadata.sol<br>@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol<br>@openzeppelin/contracts/utils/cryptography/ECDSA.sol|
| /contracts/Distributor.sol | 1| **** | 271 | |@openzeppelin/contracts/token/ERC20/IERC20.sol<br>@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol<br>@openzeppelin/contracts/utils/math/SafeCast.sol|
| **Totals** | **2** | **** | **604** | | |

### Files out of scope

*See [out_of_scope.txt](https://github.com/code-423n4/2025-11-merkl/blob/main/out_of_scope.txt)*

| File         |
| ------------ |
| ./contracts/AccessControlManager.sol |
| ./contracts/Disputer.sol |
| ./contracts/DistributionCreatorWithDistributions.sol |
| ./contracts/ReferralRegistry.sol |
| ./contracts/interfaces/IAccessControlManager.sol |
| ./contracts/interfaces/IClaimRecipient.sol |
| ./contracts/mock/DistributionCreatorUpdatable.sol |
| ./contracts/mock/MockAccessControl.sol |
| ./contracts/mock/MockClaimRecipient.sol |
| ./contracts/mock/MockPool.sol |
| ./contracts/mock/MockToken.sol |
| ./contracts/mock/MockTokenPermit.sol |
| ./contracts/mock/MockUniswapV3Pool.sol |
| ./contracts/partners/middleman/MerklGaugeMiddlemanTemplate.sol |
| ./contracts/partners/tokenWrappers/NativeTokenWrapper.sol |
| ./contracts/partners/tokenWrappers/PointToken.sol |
| ./contracts/partners/tokenWrappers/PufferPointTokenWrapper.sol |
| ./contracts/partners/tokenWrappers/PullTokenWrapperAllow.sol |
| ./contracts/partners/tokenWrappers/PullTokenWrapperTransfer.sol |
| ./contracts/partners/tokenWrappers/PullTokenWrapperTransferV0.sol |
| ./contracts/partners/tokenWrappers/PullTokenWrapperWithdraw.sol |
| ./contracts/partners/tokenWrappers/SonicFragment.sol |
| ./contracts/partners/tokenWrappers/TokenTGEWrapper.sol |
| ./contracts/struct/CampaignParameters.sol |
| ./contracts/struct/DistributionParameters.sol |
| ./contracts/struct/RewardTokenAmounts.sol |
| ./contracts/utils/Errors.sol |
| ./contracts/utils/UUPSHelper.sol |
| ./scripts/AccessControlManager.s.sol |
| ./scripts/Disputer.s.sol |
| ./scripts/DistributionCreator.s.sol |
| ./scripts/Distributor.s.sol |
| ./scripts/MockToken.s.sol |
| ./scripts/PointToken.s.sol |
| ./scripts/deployCreateX.s.sol |
| ./scripts/deployPufferPointTokenWrapper.s.sol |
| ./scripts/deployPullTokenWrapper.s.sol |
| ./scripts/deployPullTokenWrapperTransfer.s.sol |
| ./scripts/deployReferralRegistry.s.sol |
| ./scripts/deploySonicFragment.s.sol |
| ./scripts/deployTokenTGEWrapper.s.sol |
| ./scripts/deployUpgradeImplementations.s.sol |
| ./scripts/deployUpgradeImplementationsSingle.s.sol |
| ./scripts/merklDeploy.s.sol |
| ./scripts/protocols/hyperdrive/Hyperdrive.s.sol |
| ./scripts/toggleOperatorBatch.s.sol |
| ./scripts/utils/Base.s.sol |
| ./scripts/utils/ChainUtils.s.sol |
| ./scripts/utils/CreateXConstants.sol |
| ./scripts/utils/TokensUtils.sol |
| ./scripts/utils/UpgradeDeploymentBase.s.sol |
| ./test/DistributionCreator.t.sol |
| ./test/Fixture.t.sol |
| ./test/unit/Disputer.t.sol |
| ./test/unit/DistributionCreator.t.sol |
| ./test/unit/Distributor.t.sol |
| ./test/unit/ReferralRegistry.t.sol |
| ./test/unit/partners/tokenWrappers/NativeTokenWrapper.t.sol |
| ./test/unit/partners/tokenWrappers/PullTokenWrapperAllow.t.sol |
| Totals: 59 |


# Additional context

## Areas of concern (where to focus for bugs)

Primary Security Concerns:

### 1. Campaign Pre-Deposit Protection

Can an address exploit or access funds pre-deposited by another address without authorization?

### 2. Reward Claim Integrity

Do rewards consistently reach their intended recipient through all claim paths (the claimant's address, a recipient specified in the call parameters, or a user-defined default recipient)?

### 3. Unauthorized Access and Fund Theft

Any scenario enabling unauthorized assumption of user roles or theft of funds constitutes a valid issue, including:

- Pre-deposited funds in the distributionCreator contract
- Idle funds in the distributor contract


## Main invariants

### Guardian Restrictions
The Guardian role must not have the ability to steal user funds or perform actions that result in fund reallocation.

### Reward Finality
Once rewards are earned and recorded in a Merkle root, they are immutably assigned to the recipient. These rewards cannot be revoked or redirected within the current Merkle root, except through:
- An explicit reallocation by authorized parties
- Token recovery executed by the admin address

### Campaign Creator Autonomy

Campaign creators retain full control over:
- End-to-end campaign management
- Their pre-deposited funds
- The ability to recover ownership of their funds at any time
- They can revoke any role or allowance they give at anytime

## All trusted roles in the protocol

The contracts include three main trusted roles:

### 1. Governor

- Held by a multisig wallet
- Possesses administrative rights over the contract

### 2. Guardian

- May be held by externally owned accounts (EOAs)
- Performs standard operational tasks, including:
    - Whitelisting tokens
    - Toggling operator permissions for addresses that lack direct access to these functions

### 3. Updater Addresses

- Authorized to update Merkle roots
- May be EOAs, as the dispute period provides a safeguard mechanism to detect and prevent malicious root updates before they take effect

✅ SCOUTS: Please format the response above 👆 using the template below👇

| Role                                | Description                       |
| --------------------------------------- | ---------------------------- |
| Owner                          | Has superpowers                |
| Administrator                             | Can change fees                       |

✅ SCOUTS: Please format the response above 👆 so its not a wall of text and its readable.

## Running tests

Simply run:
`forge compile`
`forge test`

You need a .env file set like .env.example and with potentially other entries to have the secrets as they're introduced in the foundry.toml file

✅ SCOUTS: Please format the response above 👆 using the template below👇

```bash
git clone https://github.com/code-423n4/2023-08-arbitrum
git submodule update --init --recursive
cd governance
foundryup
make install
make build
make sc-election-test
```
To run code coverage
```bash
make coverage
```

✅ SCOUTS: Add a screenshot of your terminal showing the test coverage

## Miscellaneous
Employees of Merkl and employees' family members are ineligible to participate in this audit.

Code4rena's rules cannot be overridden by the contents of this README. In case of doubt, please check with C4 staff.

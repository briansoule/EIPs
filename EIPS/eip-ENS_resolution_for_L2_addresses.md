---
eip: <to be assigned>
title: ENS Resolution for L2 Chains
description: Allow ENS nameholders to specify addresses on EVM compatible chains.
author: Brian Soule (@BrianSoule) <brian@briansoule.com>
  <a comma separated list of the author's or authors' name + GitHub username (in parenthesis), or name and email (in angle brackets).  Example, FirstName LastName (@GitHubUsername), FirstName LastName <foo@bar.com>, FirstName (@GitHubUsername) and GitHubUsername (@GitHubUsername)>
discussions-to: <URL>
status: Draft
type: Standards Track
category: ERC
created: 2021-11-24
requires: 2304
---

## Abstract
This EIP introduces support for EVM compatible sidechains under the multichain address resolver as defined in EIP [2304](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-2304.md).

## Motivation
With the proliferation of EVM compatible L2s and sidechains, many users, projects, and contracts have addresses on alternate chains that are different from that of Mainnet. By allowing ENS name holders to specify addresses for alternate EVM chains, we expand upon the multichain support outlined in EIP 2304. Additionally, support for EVM compatible chains will help prevent the need for alternate EVM chains to create their own nameservices.
This EIP aims to add clarity for client developers who consume ENS data on L2s and Sidechains.

## Specification
The key words “MUST”, “MUST NOT”, “REQUIRED”, “SHALL”, “SHALL NOT”, “SHOULD”, “SHOULD NOT”, “RECOMMENDED”, “MAY”, and “OPTIONAL” in this document are to be interpreted as described in RFC 2119.

The technical specification should describe the syntax and semantics of any new feature. The specification should be detailed enough to allow competing, interoperable implementations for any of the current Ethereum platforms (go-ethereum, parity, cpp-ethereum, ethereumj, ethereumjs, and [others](https://github.com/ethereum/wiki/wiki/Clients)).

In the absence of an explicitly specified L2 or Sidechain address, the resolver will return the specified `function addr(bytes32 node)` Ethereum mainnet address.
Example:
  ** Point of discussion
  When `addr(bytes32 node, uint coinType)` is queried, and the EVM address isn't set. Return the mainnet address
  ** /End point of discussion
  
  
| Cryptocurrency | Coin Type | Encoding |
| --- | --- | --- |
| Optimism | 614 | ChecksummedHex |
| Fantom | 1007 | ChecksummedHex |
| Polygon | 966 | ChecksummedHex |
| Binance Smart Chain | 714 | ChecksummedHex |
| Avalanche | 9000 | ChecksummedHex |
| xDai | 700 | ChecksummedHex |

| Chains not yet accepted into [SLIP-0044](https://github.com/satoshilabs/slips/blob/master/slip-0044.md) |
| --- |
| Arbitrum |
| Boba |
| Loopring |
| Starkware |


  
## Rationale
The rationale fleshes out the specification by describing what motivated the design and why particular design decisions were made. It should describe alternate designs that were considered and related work, e.g. how the feature is supported in other languages.

## Backwards Compatibility
All EIPs that introduce backwards incompatibilities must include a section describing these incompatibilities and their severity. The EIP must explain how the author proposes to deal with these incompatibilities. EIP submissions without a sufficient backwards compatibility treatise may be rejected outright.

## Test Cases
Test cases for an implementation are mandatory for EIPs that are affecting consensus changes.  If the test suite is too large to reasonably be included inline, then consider adding it as one or more files in `../assets/eip-####/`.

## Reference Implementation
An optional section that contains a reference/example implementation that people can use to assist in understanding or implementing this specification.  If the implementation is too large to reasonably be included inline, then consider adding it as one or more files in `../assets/eip-####/`.

## Security Considerations
All EIPs must contain a section that discusses the security implications/considerations relevant to the proposed change. Include information that might be important for security discussions, surfaces risks and can be used throughout the life cycle of the proposal. E.g. include security-relevant design decisions, concerns, important discussions, implementation-specific guidance and pitfalls, an outline of threats and risks and how they are being addressed. EIP submissions missing the "Security Considerations" section will be rejected. An EIP cannot proceed to status "Final" without a Security Considerations discussion deemed sufficient by the reviewers.

## Copyright
Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).

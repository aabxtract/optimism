<div align="center">
  <br />
  <br />
  <a href="https://optimism.io"><img alt="Optimism" src="./logo.svg" width=600></a>
  <br />
  <h3><a href="https://optimism.io">Optimism</a> is Ethereum, scaled.</h3>
  <br />
</div>

**Table of Contents**

<!--TOC-->

- [What is Optimism?](#what-is-optimism)
- [Documentation](#documentation)
- [Specifications](#specifications)
- [Community](#community)
- [Contributing](#contributing)
- [Security and Vulnerability Reporting](#security-and-vulnerability-reporting)
- [Repository Structure](#repository-structure)
- [Development and Release Process](#development-and-release-process)
  - [Release Overview](#release-overview)
  - [Production Releases](#production-releases)
  - [Development Branch](#development-branch)
- [License](#license)

<!--TOC-->

## What is Optimism?

[Optimism](https://www.optimism.io/) scales Ethereum's technology to coordinate global collaboration on decentralized economies and governance systems. The [Optimism Collective](https://www.optimism.io/vision) builds open-source software that powers scalable blockchains and addresses key governance and economic challenges across the Ethereum ecosystem. We operate on the principle of **impact=profit**: individuals who create positive impact for the Collective should be proportionally rewarded. **Change the incentives and you change the world.**

This repository contains core components of the OP Stack, the decentralized software stack maintained by the Optimism Collective. The OP Stack powers Optimism and serves as the foundation for blockchains like [OP Mainnet](https://explorer.optimism.io/) and [Base](https://base.org). Built to be aggressively open-source, you're welcome to explore, modify, and extend this code.

## Documentation

**Building on OP Mainnet?** Start with the [Optimism Documentation](https://docs.optimism.io)

**Building your own OP Stack blockchain?** Follow the [OP Stack Guide](https://docs.optimism.io/stack/getting-started) and familiarize yourself with our [Development and Release Process](#development-and-release-process)

## Specifications

Detailed technical specifications for the OP Stack are available in the [OP Stack Specs](https://github.com/ethereum-optimism/specs) repository.

## Community

Join the conversation on the [Optimism Discord](https://discord.gg/optimism) for general discussion, or participate in governance decisions on the [Optimism Governance Forum](https://gov.optimism.io/).

## Contributing

The OP Stack is built through collaboration. By working together on free, open software and shared standards, the Optimism Collective prevents fragmented development and accelerates the growth of the entire Ethereum ecosystem. Join us to build the future and redefine power, together.

**Getting started:**
- Read [CONTRIBUTING.md](./CONTRIBUTING.md) for a detailed explanation of our contribution process
- Follow the [Developer Quick Start](./CONTRIBUTING.md#development-quick-start) to set up your development environment
- Browse [Good First Issues](https://github.com/ethereum-optimism/optimism/issues?q=is:open+is:issue+label:D-good-first-issue) for beginner-friendly tasks
- Check [CONTRIBUTING.md](./CONTRIBUTING.md) for information on larger projects

## Security and Vulnerability Reporting

Review our [Security Policy](https://github.com/ethereum-optimism/.github/blob/master/SECURITY.md) for detailed information on reporting vulnerabilities in this codebase.

**Bug bounty hunters:** Check out the [Optimism Immunefi bug bounty program](https://immunefi.com/bounty/optimism/), which offers rewards up to $2,000,042 for critical vulnerabilities.

## Repository Structure

<pre>
├── <a href="./cannon">cannon</a>: Onchain MIPS instruction emulator for fault proofs
├── <a href="./devnet-sdk">devnet-sdk</a>: Toolkit for standardized devnet interactions
├── <a href="./docs">docs</a>: Documentation including audits and post-mortems
├── <a href="./kurtosis-devnet">kurtosis-devnet</a>: OP Stack Kurtosis devnet
├── <a href="./op-acceptance-tests">op-acceptance-tests</a>: Acceptance tests and configuration
├── <a href="./op-alt-da">op-alt-da</a>: Alternative Data Availability mode (beta)
├── <a href="./op-batcher">op-batcher</a>: L2 batch submitter to L1
├── <a href="./op-chain-ops">op-chain-ops</a>: State surgery utilities
├── <a href="./op-challenger">op-challenger</a>: Dispute game challenge agent
├── <a href="./op-conductor">op-conductor</a>: High-availability sequencer service
├── <a href="./op-deployer">op-deployer</a>: CLI for deploying and upgrading OP Stack contracts
├── <a href="./op-devstack">op-devstack</a>: Flexible test frontend for integration testing
├── <a href="./op-dispute-mon">op-dispute-mon</a>: Dispute game monitoring service
├── <a href="./op-dripper">op-dripper</a>: Controlled token distribution service
├── <a href="./op-e2e">op-e2e</a>: End-to-end testing for all bedrock components
├── <a href="./op-faucet">op-faucet</a>: Development faucet with multi-chain support
├── <a href="./op-fetcher">op-fetcher</a>: Data fetching utilities
├── <a href="./op-interop-mon">op-interop-mon</a>: Interoperability monitoring service
├── <a href="./op-node">op-node</a>: Rollup consensus-layer client
├── <a href="./op-preimage">op-preimage</a>: Go bindings for Preimage Oracle
├── <a href="./op-program">op-program</a>: Fault proof program
├── <a href="./op-proposer">op-proposer</a>: L2 output submitter to L1
├── <a href="./op-service">op-service</a>: Common codebase utilities
├── <a href="./op-supervisor">op-supervisor</a>: Cross-chain message safety monitoring
├── <a href="./op-sync-tester">op-sync-tester</a>: Sync testing utilities
├── <a href="./op-test-sequencer">op-test-sequencer</a>: Development test sequencer
├── <a href="./op-up">op-up</a>: Deployment and management utilities
├── <a href="./op-validator">op-validator</a>: Chain configuration validation tool
├── <a href="./op-wheel">op-wheel</a>: Database utilities
├── <a href="./ops">ops</a>: Operational packages
├── <a href="./packages">packages</a>
│   ├── <a href="./packages/contracts-bedrock">contracts-bedrock</a>: OP Stack smart contracts
</pre>

## Development and Release Process

### Release Overview

**Important:** Read this section carefully if you're planning to fork this repository or make frequent contributions.

### Production Releases

Production releases are tagged using the format `<component-name>/v<semver>`.

**Examples:**
- `op-node/v1.1.2` for an op-node release
- `op-contracts/v1.0.0` for smart contract releases
- `op-node/v1.1.2-rc.1` for release candidates (always starting with `rc.1`)

**Smart contract releases:** Review the GitHub release notes for each release, which specify exactly which contracts are included. Not all contracts in a release are production-ready—many remain under active development.

**Go-only releases:** Tags formatted as `v<semver>` (e.g., `v1.1.4`) indicate releases containing all Go code components (`op-*`) but **excluding** smart contracts (`contracts-*`). This naming convention is required by Go's module system.

**op-geth versioning:** op-geth embeds upstream geth's version using the format `vMAJOR.GETH_MAJOR GETH_MINOR GETH_PATCH.PATCH`. For example, if geth is at `v1.12.0`, the corresponding op-geth version is `v1.101200.0`. Geth's minor version is padded to three characters, and the patch version to two characters. The major version is not padded.

See the [Node Software Releases](https://docs.optimism.io/builders/node-operators/releases) documentation for detailed information about releases for node components.

**Components with production releases:**
- `op-batcher`
- `op-contracts`
- `op-challenger`
- `op-node`
- `op-proposer`

All other components are development-only and do not have official releases.

### Development Branch

The primary development branch is [`develop`](https://github.com/ethereum-optimism/optimism/tree/develop/), which contains the latest backwards-compatible software for experimental [network deployments](https://docs.optimism.io/chain/networks). Direct pull requests for backwards-compatible changes to `develop`.

**Contract changes:** Modifications to contracts in `packages/contracts-bedrock/src` are usually **not** backwards compatible. Exceptions exist when we must deploy new contracts after a tag has been fully deployed. If you're unsure which branch to target for contract changes, use a feature branch. Feature branches help manage conflicts when multiple projects modify the same code.

## License

All files in this repository are licensed under the [MIT License](https://github.com/ethereum-optimism/optimism/blob/master/LICENSE) unless otherwise stated.

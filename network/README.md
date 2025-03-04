# Real Estate Secure Ledger (RESL) Network

## Introduction

The current folder configures the Real Estate Secure Ledger (RESL) network.

Currently the network topology is as follows:

- 1 Orderer Organization
- 2 Peer Organizations
- 1 Certificate Authority (CA) for each organization

The network will be configured with more organizations and peers in the future as we set up the network for the Real Estate Secure Ledger (RESL) application. This is the first step in setting up the network.

## Development Workflow

### Mac OS Pre-requisites

- Install [Homebrew](https://brew.sh/)
- Install [Docker Desktop](https://www.docker.com/products/docker-desktop)
- Install [Hyperledger Fabric Tools](https://stackoverflow.com/questions/45498921/steps-to-install-cryptogen-tool-for-hyperledger-fabric-node-setup)

```bash
brew tap hyperledger/fabric
```

```bash
brew install fabric-tools@2.1.0
```

### Development Workflow

```bash
cryptogen generate --config=./crypto-config.yaml
```

```bash

```

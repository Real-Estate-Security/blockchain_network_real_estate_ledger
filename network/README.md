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

### Creating Assets and Network Configuration

```bash
cryptogen generate --config=./crypto-config.yaml
```

```bash

```

### DNS Resolution on OSX

Fabric's OSX binaries have been statically linked with the golang `go` DNS resolver. In some environments, this
causes a brief but [noticeable delay](https://github.com/hyperledger/fabric/issues/3372) when issuing peer commands
against the test network.

Workarounds to improve DNS resolution time on OSX:

- Add manual DNS overrides for virtual hosts by adding our hosts for peers to /etc/hosts with the following format:

```
127.0.0.1 org0-ca.localho.st
127.0.0.1 org1-ca.localho.st
127.0.0.1 org2-ca.localho.st
127.0.0.1 org0-orderer1.localho.st
127.0.0.1 org0-orderer2.localho.st
127.0.0.1 org0-orderer3.localho.st
127.0.0.1 org1-peer1.localho.st
127.0.0.1 org1-peer2.localho.st
127.0.0.1 org2-peer1.localho.st
127.0.0.1 org2-peer2.localho.st
```

- Reduce the system resolver timeout from the default 5s by adding to /etc/resolv.conf:

```shell
options: timeout 2
```

- Compile the [fabric binaries](https://github.com/hyperledger/fabric) on a Mac and copy `build/bin/*` outputs to
  `test-network-k8s/bin`. Mac native builds are linked against the `netdns=cgo` DNS resolver, and are not
  subject to the timeouts associated with the Golang DNS resolver.

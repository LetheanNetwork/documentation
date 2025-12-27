---
title: FAQ
description: Frequently asked questions about Lethean, LTHN, and the network.
---

# Frequently Asked Questions

## General

### What is Lethean?
Lethean is confidential infrastructure for assured information exchange. It combines a privacy-preserving blockchain with distributed network infrastructure to enable secure data logistics where users maintain sovereignty over their information. See [What is Lethean?](../about/index.md) for a complete overview.

### Is Lethean free to use?
Yes. Lethean is open source under the [EUPL-1.2 license](https://joinup.ec.europa.eu/collection/eupl/eupl-text-eupl-12) and free to use forever. There are no premium tiers or artificial limitations.

### Who controls Lethean?
Lethean has been community-governed since 2020. There is no corporate ownership or central authority. Development decisions are made transparently by contributors and community members.

### How is Lethean different from other cryptocurrencies?
Lethean is built on CryptoNote technology with Zano enhancements, providing native privacy features including confidential transactions. Beyond the blockchain, Lethean includes a network layer with ethical constraints encoded at the protocol level through the Axioms of Life framework.

---

## LTHN Token

### What is LTHN?
LTHN is the native token of the Lethean network. It's used for transactions, staking, and paying for network services.

### Where can I get LTHN?
You can acquire LTHN through:

- Mining (PoW)
- Staking (PoS)
- Exchanges that list LTHN
- Community distribution

### What's the total supply?
See the [Tokenomics](../web3/tokenomics.md) page for detailed supply mechanics, distribution, and inflation schedule.

### How do I store LTHN?
Use the official [CLI wallet](../getting-started/wallet.md) or wait for the Desktop application (currently in beta).

---

## Technical

### What consensus mechanism does Lethean use?
Lethean uses a hybrid Proof-of-Work (PoW) and Proof-of-Stake (PoS) consensus mechanism, providing both security and energy efficiency.

### What are Confidential Assets?
Confidential Assets allow anyone to create custom tokens on the Lethean blockchain with the same privacy guarantees as LTHN itself—hidden amounts and unlinkable transactions.

### What are Auditable Wallets?
Auditable wallets provide optional transparency for compliance use cases. Users can generate view keys that allow designated parties to verify transactions without gaining spending control.

### What is the Axioms of Life framework?
The Axioms of Life are ethical principles encoded into the Lethean network protocol. They ensure the infrastructure cannot be weaponized against users. Learn more in the [Gateway documentation](../web3/labs/gateway.md).

### How do I run a node?
Follow the [Blockchain/Node setup guide](../getting-started/chain.md). You'll need approximately 50GB of disk space and a stable internet connection.

---

## Troubleshooting

### My wallet won't sync
1. Ensure your daemon is running and fully synced
2. Try connecting to a remote node: `--daemon-host=seed.lethean.io`
3. Check your firewall isn't blocking connections on port 48772

### The daemon is syncing slowly
Initial sync can take several hours depending on your connection. You can speed this up by:

1. Downloading the [blockchain export](https://seed.lethean.io/blockchain.raw)
2. Importing it with `lethean-blockchain-import`

See the [chain guide](../getting-started/chain.md) for detailed import instructions.

### Build is failing
1. Run `make clean` before rebuilding
2. Ensure you cloned with `--recursive` flag
3. Check you have the required dependencies from the [build guide](../getting-started/developer/build.md)

---

## Community

### Where can I get help?
- [Discord](https://discord.com/invite/lethean-lthn-379876792003067906) - Active community chat
- [GitHub](https://github.com/LetheanNetwork) - Report issues and contribute

### How can I contribute?
- **Code**: Submit pull requests on [GitHub](https://github.com/LetheanNetwork)
- **Documentation**: Edit pages directly via the pencil icon or submit PRs to the [documentation repo](https://github.com/LetheanNetwork/documentation)
- **Community**: Help answer questions on Discord

### Where can I follow updates?
- [Project Updates](../updates/index.md) - Development blog
- [X/Twitter](https://x.com/LetheanNetwork) - Announcements

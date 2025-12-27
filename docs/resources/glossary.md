---
title: Glossary
description: Definitions of key terms and concepts used in Lethean documentation.
---

# Glossary

Key terms and concepts used throughout the Lethean ecosystem.

---

## A

### Auditable Wallet
A wallet configuration that allows designated third parties to view transaction history without gaining spending control. Useful for compliance, accounting, or transparency use cases. Uses a separate **view key** that can be shared independently of the spend key.

### Axioms of Life
A computational ethics framework that defines five core principles for ethical AI and network behavior. These axioms are encoded into the Lethean Gateway protocol to ensure the infrastructure cannot be weaponized against its users. See [Gateway documentation](../web3/labs/gateway.md).

---

## B

### Block
A collection of transactions that have been validated and added to the blockchain. Each block references the previous block, forming an immutable chain.

### Block Height
The number of blocks in the chain from the genesis block to the current block. Used as a measure of blockchain progress and for identifying specific points in history.

---

## C

### CM-OS
**Contextual Mesh Operating System**. The software framework that implements the UEPS protocol on Gateway nodes. Provides ethical service-oriented middleware for distributed applications.

### Confidential Assets
A feature allowing anyone to create custom tokens on the Lethean blockchain. These tokens inherit the same privacy guarantees as LTHN—hidden amounts and unlinkable transactions.

### Consensus
The mechanism by which network nodes agree on the state of the blockchain. Lethean uses a hybrid PoW/PoS consensus combining security and efficiency.

### CryptoNote
The privacy-focused cryptocurrency protocol that Lethean is built upon. Provides ring signatures, stealth addresses, and unlinkable transactions.

---

## D

### Daemon
The background process (`letheand`) that maintains a connection to the Lethean network, syncs the blockchain, validates transactions, and relays data to peers.

### Difficulty
A measure of how hard it is to find a valid block hash. Automatically adjusts to maintain consistent block times regardless of network hashrate.

---

## E

### Emission
The rate at which new LTHN is created through mining and staking rewards. Follows a predetermined schedule defined in the tokenomics.

---

## G

### Gateway
A network node that routes traffic through the Lethean network layer, enforcing the UEPS protocol. Gateway operators can earn LTHN for providing network services.

### Genesis Block
The first block in the blockchain (height 0). Contains the initial state and configuration of the network.

---

## H

### Hashrate
The computational power being used to mine blocks, measured in hashes per second (H/s). Higher network hashrate means greater security.

---

## I

### Integrated Address
A standard address combined with a payment ID, encoded as a single string. Simplifies payments by eliminating the need for separate payment ID fields.

---

## L

### LTHN
The native token of the Lethean network. Used for transactions, staking, and paying for network services. Symbol: **LTHN**.

### LMDB
**Lightning Memory-Mapped Database**. The database engine used to store blockchain data locally. Data is stored in the `lmdb` directory.

---

## M

### Mixin
The number of decoy inputs included in a ring signature. Higher mixin provides greater privacy but increases transaction size.

---

## N

### Node
A computer running the Lethean daemon software, participating in the peer-to-peer network. Nodes validate transactions, relay data, and maintain copies of the blockchain.

---

## P

### Payment ID
An optional identifier attached to transactions, allowing recipients to identify the purpose or sender. Can be encrypted for privacy.

### PoS (Proof of Stake)
A consensus mechanism where block validators are selected based on the amount of LTHN they have staked. Provides energy-efficient block production.

### PoW (Proof of Work)
A consensus mechanism where miners compete to solve cryptographic puzzles. The first to find a valid solution produces the next block and earns rewards.

### Prime Imperative
The first Axiom of Life: treat every participant as a protected, autonomous entity. Hardwired into the Gateway protocol to prevent operations that could harm network participants.

---

## R

### Ring Signature
A cryptographic signature that proves a transaction was signed by someone in a group, without revealing which member. Provides sender privacy in Lethean transactions.

### RingCT (Ring Confidential Transactions)
An enhancement to ring signatures that also hides transaction amounts while allowing network validation that no new coins were created.

### RPC (Remote Procedure Call)
An API protocol for communicating with the daemon or wallet. Used by applications and SDKs to interact with Lethean.

---

## S

### Seed Phrase
A 25-word mnemonic that can restore a wallet. Must be kept secret and backed up securely—anyone with the seed phrase has full control of the wallet.

### Spend Key
The private key required to authorize spending from a wallet. Must never be shared.

### Staking
Locking LTHN to participate in PoS consensus. Stakers earn rewards for validating blocks.

### Stealth Address
A one-time address generated for each transaction, preventing linking of transactions to a recipient's public address.

---

## T

### Transaction
A transfer of LTHN (or other assets) between addresses, recorded on the blockchain.

### TLV (Type-Length-Value)
A data encoding format used in UEPS protocol headers. Allows flexible, extensible packet structures.

---

## U

### UEPS (Unified Ethical Protocol Stack)
The network protocol implemented by Lethean Gateways. Enforces the Axioms of Life at the protocol level through consent-based routing, intent alignment, and protective guards.

### Unlock Time
The number of blocks before received funds can be spent. Provides a security buffer and is used for time-locked transactions.

---

## V

### View Key
A key that allows viewing incoming transactions to a wallet without the ability to spend. Can be shared with auditors or services that need to verify payments.

---

## W

### Wallet
Software that manages LTHN addresses and keys, creates transactions, and tracks balances. Available as CLI (`lethean-wallet-cli`) and integrated into the Desktop application.

---

## Z

### Zano
The upstream project that provides many of Lethean's advanced features including the Zarcanum PoS protocol, Confidential Assets, and Ionic Swaps.

### Zarcanum
Zano's PoS protocol that enables staking with full privacy—stake amounts and rewards are hidden, unlike traditional PoS systems.

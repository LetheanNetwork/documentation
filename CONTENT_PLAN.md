# Lethean Documentation Content Plan

## Executive Summary

This plan transforms the Lethean documentation from a technical reference into a professional guide that positions Lethean as **Confidential Infrastructure for Assured Information Exchange** — moving decisively away from "VPN" terminology toward network-focused messaging.

**Current State**: 42 markdown files, ~7/10 professionalism. Strong vision but fragmented execution.

**Target State**: Cohesive, professional documentation that clearly explains what Lethean is, why it matters, and how to use it.

---

## Phase 1: Foundation & Cleanup (Priority: Critical)

### 1.1 Remove/Revise VPN References

| File | Action |
|------|--------|
| `network/vpn.md` | **Delete or archive** — marked WIP, contradicts new positioning |
| `docs/index.md` | Audit for VPN references, replace with "network" terminology |
| `mkdocs.yml` | Update repo references from `letheanVPN` to `LetheanNetwork` |
| `overrides/main.html` | Update Twitter handle if changed |

### 1.2 Fix Broken Infrastructure

| Issue | Action |
|-------|--------|
| `updates/index.md` is empty | Add proper blog listing with recent posts |
| GitHub links point to old org | Update all `letheanVPN` → `LetheanNetwork` |
| Social links outdated | Audit and update Twitter/Discord references |

### 1.3 Create Core "What is Lethean?" Page

**New file**: `docs/about/index.md`

Structure:
```
1. One-paragraph elevator pitch (no jargon)
2. The Problem We Solve
   - Data sovereignty in a surveillance economy
   - Trust without centralization
   - Ethical infrastructure for AI age
3. How Lethean Works (high-level)
   - Blockchain layer (value + identity)
   - Network layer (confidential data transit)
   - Application layer (user-facing tools)
4. What Makes Us Different
   - Axioms of Life framework (simplified)
   - Community-governed since 2020
   - Perpetual license, free forever
```

---

## Phase 2: User Journey Restructure

### 2.1 New Information Architecture

```
Home
├── About Lethean
│   ├── What is Lethean? (NEW)
│   ├── How It Works (NEW - technical overview)
│   ├── Use Cases (NEW)
│   └── Comparison (NEW - vs traditional solutions)
│
├── Getting Started
│   ├── Choose Your Path (NEW - decision tree)
│   ├── For Users
│   │   ├── Wallet Setup (existing, enhanced)
│   │   └── Desktop App (NEW - reference November update)
│   ├── For Node Operators
│   │   ├── Run a Node (existing chain.md, enhanced)
│   │   └── Hardware Requirements (NEW)
│   └── For Developers
│       ├── Quick Start (NEW)
│       ├── Build from Source (existing)
│       ├── Docker (existing)
│       └── SDKs (existing, enhanced)
│
├── Network
│   ├── Architecture (NEW - replace vpn.md)
│   ├── Gateway Infrastructure (move from web3/labs/)
│   └── Axioms of Life (NEW - accessible version)
│
├── Blockchain
│   ├── Overview (move web3/index.md content)
│   ├── Tokenomics (existing)
│   ├── Configuration (existing, enhanced)
│   └── Staking Guide (NEW)
│
├── SDK Reference
│   └── (existing Go SDK, add examples)
│
├── Updates (existing blog)
│
└── Resources
    ├── FAQ (NEW)
    ├── Glossary (NEW)
    ├── Troubleshooting (NEW)
    └── Security Best Practices (NEW)
```

### 2.2 New "Choose Your Path" Page

**New file**: `docs/getting-started/paths.md`

Interactive decision tree:
- "I want to **use** Lethean" → Wallet + Desktop App
- "I want to **support** the network" → Node Operator guide
- "I want to **build** on Lethean" → Developer docs
- "I want to **understand** Lethean" → About section

---

## Phase 3: Content Enhancement

### 3.1 Getting Started Improvements

#### Wallet Guide Enhancements (`getting-started/wallet.md`)
Add:
- Security best practices section
- Backup procedures with verification steps
- Troubleshooting common issues
- GUI wallet mention (if Desktop app supports it)

#### Node Guide Enhancements (`getting-started/chain.md`)
Add:
- Hardware requirements table (minimum/recommended)
- Expected sync times
- Staking configuration
- Monitoring basics
- Common errors and solutions

### 3.2 New Technical Content

#### Architecture Overview
**New file**: `docs/network/architecture.md`

```
1. Network Topology
   - Peer-to-peer design
   - Node types and roles
   - Data flow diagrams

2. Consensus Mechanism
   - PoW/PoS hybrid explanation
   - Block production
   - Finality guarantees

3. Privacy Features
   - Transaction confidentiality
   - Network-level privacy
   - Audit capabilities

4. Integration Points
   - API endpoints
   - SDK capabilities
   - Extension mechanisms
```

#### Axioms of Life (Accessible Version)
**New file**: `docs/network/axioms.md`

Translate the philosophical framework into practical terms:
- What each axiom means for users
- How it's enforced in code
- Why it matters for trust

### 3.3 SDK Documentation Expansion

Current state: Go SDK has 24 auto-generated files with minimal context.

Actions:
1. Add **real-world examples** to `sdk/go/index.md`
2. Create **language-specific quick starts** for top 5 SDKs:
   - Go (existing, enhance)
   - Python (NEW)
   - TypeScript/JavaScript (NEW)
   - Rust (NEW)
   - PHP (has example, expand)
3. Add **common patterns** section:
   - Authentication (even if none required, document it)
   - Error handling
   - Pagination
   - Rate limiting

---

## Phase 4: New Essential Pages

### 4.1 FAQ Page
**New file**: `docs/resources/faq.md`

Categories:
- General (What is Lethean? Is it free? etc.)
- Technical (Sync issues, wallet problems)
- Tokenomics (Supply, staking, exchanges)
- Development (Contributing, SDK usage)

### 4.2 Glossary
**New file**: `docs/resources/glossary.md`

Define:
- LTHN, UEPS, CM-OS
- CryptoNote, Zano relationship
- Axioms of Life terms
- Technical blockchain terms

### 4.3 Troubleshooting Guide
**New file**: `docs/resources/troubleshooting.md`

Common issues:
- Wallet won't sync
- Node connection failures
- Build errors
- SDK integration problems

### 4.4 Security Best Practices
**New file**: `docs/resources/security.md`

Cover:
- Wallet security (seed phrases, backups)
- Node hardening
- Network security
- Operational security for providers

---

## Phase 5: Professional Polish

### 5.1 Consistency Audit

- [ ] Terminology: Replace all "VPN" with appropriate "network" terms
- [ ] Branding: Consistent capitalization (Lethean, LTHN, not LETHEAN)
- [ ] Links: All GitHub links to LetheanNetwork org
- [ ] Dates: Remove/update outdated timeline references
- [ ] Status badges: Consistent use (Stable, Beta, Alpha, etc.)

### 5.2 Visual Improvements

- [ ] Add architecture diagrams (use Mermaid, already configured)
- [ ] Create consistent iconography for sections
- [ ] Add screenshots for wallet/app guides
- [ ] Improve code block formatting

### 5.3 SEO & Discoverability

- [ ] Add meta descriptions to all pages
- [ ] Improve page titles for search
- [ ] Add OpenGraph images for social sharing
- [ ] Ensure sitemap is generated

---

## Content Priority Matrix

| Content | Impact | Effort | Priority |
|---------|--------|--------|----------|
| Remove VPN references | High | Low | **P0** |
| Fix broken updates index | High | Low | **P0** |
| Update GitHub org links | High | Low | **P0** |
| "What is Lethean?" page | High | Medium | **P1** |
| Choose Your Path page | High | Low | **P1** |
| FAQ | High | Medium | **P1** |
| Architecture overview | High | High | **P2** |
| Glossary | Medium | Low | **P2** |
| Enhanced wallet guide | Medium | Medium | **P2** |
| Enhanced node guide | Medium | Medium | **P2** |
| SDK examples | Medium | High | **P3** |
| Troubleshooting guide | Medium | Medium | **P3** |
| Security best practices | Medium | Medium | **P3** |
| Axioms accessible version | Low | Medium | **P4** |

---

## Messaging Guidelines

### Do Use
- "Confidential infrastructure"
- "Assured information exchange"
- "Sovereign data control"
- "Decentralized network"
- "Privacy-preserving"
- "Resilient infrastructure"

### Avoid
- "VPN" or "dVPN"
- "Anonymous" (use "private" or "confidential")
- Overly technical jargon without explanation
- Promises without implementation status

### Tone
- Professional but accessible
- Technical accuracy over marketing fluff
- Acknowledge what's complete vs in-progress
- Community-focused, not corporate

---

## Success Metrics

1. **Clarity**: New user can understand what Lethean is within 2 minutes
2. **Completeness**: Every getting-started path has end-to-end documentation
3. **Consistency**: Zero VPN references in non-legacy content
4. **Freshness**: All links work, all dates are current
5. **Professionalism**: 9/10 rating on documentation quality

---

## Next Steps

1. Review and approve this plan
2. Create GitHub issues for each P0/P1 item
3. Begin Phase 1 cleanup immediately
4. Schedule content creation for Phase 2-4
5. Establish documentation review process for ongoing maintenance

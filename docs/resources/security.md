---
title: Security Best Practices
description: Guidelines for securing your Lethean wallet, node, and infrastructure.
---

# Security Best Practices

This guide covers security considerations for users, node operators, and developers working with Lethean.

---

## Wallet Security

### Seed Phrase Protection

Your 25-word seed phrase is the master key to your funds. Treat it like cash.

| Do | Don't |
|----|-------|
| Write on paper | Store digitally (files, photos, cloud) |
| Store in fireproof safe | Share with anyone |
| Make multiple copies in separate locations | Enter on websites |
| Verify backup works before depositing | Send via email, chat, or SMS |

!!! danger "No Recovery"
    If you lose your seed phrase and wallet password, your funds are **permanently inaccessible**. There is no recovery mechanism.

### Password Guidelines

| Requirement | Recommendation |
|-------------|----------------|
| Length | 16+ characters |
| Complexity | Mix of uppercase, lowercase, numbers, symbols |
| Uniqueness | Never reuse from other services |
| Storage | Use a password manager |

### Environment Security

Before handling significant funds:

- [ ] Use a clean, updated operating system
- [ ] Scan for malware
- [ ] Disable browser extensions when accessing crypto
- [ ] Use a dedicated device for large holdings
- [ ] Enable full-disk encryption

### Remote Node Considerations

When connecting to a remote node (`--daemon-host`):

| What's Exposed | What's Protected |
|----------------|------------------|
| Your IP address | Your spend key |
| Transaction queries | Your ability to spend |
| Incoming transaction visibility | Outgoing transaction signing |

**For maximum privacy**: Run your own node.

---

## Node Security

### Network Hardening

| Port | Exposure | Recommendation |
|------|----------|----------------|
| 48772 (P2P) | Public | Open for full network participation |
| 48782 (RPC) | Private | Only expose if needed, with restrictions |

### RPC Security

If exposing RPC publicly:

```shell
# Restrict to read-only methods
letheand --rpc-bind-ip=0.0.0.0 --confirm-external-bind --restricted-rpc
```

Never expose unrestricted RPC to the internet without authentication.

### Firewall Configuration

=== "Linux (ufw)"

    ```shell
    # Allow P2P
    sudo ufw allow 48772/tcp

    # Allow RPC only from localhost
    sudo ufw allow from 127.0.0.1 to any port 48782
    ```

=== "Linux (iptables)"

    ```shell
    # Allow P2P
    iptables -A INPUT -p tcp --dport 48772 -j ACCEPT

    # Allow RPC from localhost only
    iptables -A INPUT -p tcp -s 127.0.0.1 --dport 48782 -j ACCEPT
    iptables -A INPUT -p tcp --dport 48782 -j DROP
    ```

### Running as Non-Root

Never run the daemon as root:

```shell
# Create dedicated user
sudo useradd -r -m -s /bin/false lethean

# Set ownership
sudo chown -R lethean:lethean /opt/lethean /var/lib/lethean

# Run as lethean user
sudo -u lethean /opt/lethean/letheand --data-dir=/var/lib/lethean
```

### System Monitoring

Monitor for:

- Unusual CPU/memory usage
- Unexpected network connections
- Disk space depletion
- Log anomalies

```shell
# Watch daemon logs
tail -f $HOME/Lethean/data/lethean.log | grep -E "(ERROR|WARN)"
```

---

## Developer Security

### API Security

When building applications:

1. **Validate all inputs** from the blockchain API
2. **Don't trust block data** until sufficient confirmations
3. **Handle errors gracefully** - network issues are common
4. **Rate limit** your API calls to avoid overwhelming nodes

### Secret Management

| Secret Type | Storage Recommendation |
|-------------|------------------------|
| Wallet files | Encrypted filesystem, never in repos |
| Private keys | Hardware security modules for production |
| API endpoints | Environment variables, not hardcoded |

### Dependency Security

```shell
# Regularly update dependencies
git pull
git submodule update --recursive

# Verify checksums of downloaded binaries
sha256sum lethean-*.tar.gz
```

### Build Verification

For production deployments:

1. Clone from official repository
2. Verify GPG signatures (when available)
3. Build from source rather than using pre-built binaries
4. Compare checksums with published values

---

## Operational Security

### Transaction Privacy

Maximize transaction privacy:

| Practice | Effect |
|----------|--------|
| Run your own node | Hides your queries from third parties |
| Use default mixin | Blends with network traffic |
| Avoid address reuse | Prevents linking transactions |
| Use subaddresses | One per sender/purpose |

### Timing Considerations

- Avoid predictable transaction patterns
- Don't immediately spend received funds
- Consider network activity correlation

### Physical Security

For significant holdings:

- [ ] Use a dedicated, air-gapped device for signing
- [ ] Store seed phrase in multiple secure locations
- [ ] Consider multi-signature setups for organizational funds
- [ ] Have a secure succession plan

---

## Incident Response

### If You Suspect Compromise

1. **Stop** - Don't make additional transactions
2. **Assess** - Check transaction history for unauthorized activity
3. **Move** - If seed is compromised, create new wallet and transfer funds
4. **Investigate** - Check system for malware
5. **Report** - Notify community if you discover vulnerabilities

### Reporting Security Issues

For responsible disclosure of vulnerabilities:

- **GitHub**: [Security tab](https://github.com/LetheanNetwork/blockchain/security) for private reports
- **Discord**: Contact maintainers directly

Do not publicly disclose vulnerabilities before they're patched.

---

## Checklist

### For Users

- [ ] Seed phrase written down and secured
- [ ] Backup verified by test restore
- [ ] Strong, unique wallet password
- [ ] Clean operating system
- [ ] Understanding of remote node tradeoffs

### For Node Operators

- [ ] Running as non-root user
- [ ] Firewall configured
- [ ] RPC access restricted
- [ ] Monitoring in place
- [ ] Regular updates applied

### For Developers

- [ ] No secrets in source code
- [ ] Dependencies regularly updated
- [ ] Input validation implemented
- [ ] Error handling for network issues
- [ ] Build verification process

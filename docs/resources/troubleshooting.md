---
title: Troubleshooting
description: Solutions to common issues with Lethean wallet, daemon, and development.
---

# Troubleshooting Guide

Quick solutions to common issues. For component-specific details, see:

- [Wallet Troubleshooting](../getting-started/wallet.md#troubleshooting)
- [Node Troubleshooting](../getting-started/chain.md#troubleshooting)

---

## Daemon Issues

### Daemon Won't Start

**Symptoms**: `letheand` exits immediately or shows errors on startup.

**Solutions**:

1. **Check for existing process**
   ```shell
   # Linux/macOS
   pgrep letheand

   # Windows
   tasklist | findstr letheand
   ```
   Kill any existing process before starting a new one.

2. **Check disk space**
   ```shell
   df -h  # Linux/macOS
   ```
   The blockchain requires 50GB+ free space.

3. **Check permissions**
   ```shell
   ls -la $HOME/Lethean/data
   ```
   Ensure the data directory is writable.

4. **Try with verbose logging**
   ```shell
   letheand --log-level=4
   ```

### Sync Stuck at Specific Height

**Solutions**:

1. **Add seed nodes**
   ```shell
   letheand --add-priority-node=seed.lethean.io:48772
   ```

2. **Check peer connections**
   Look for `outgoing_connections_count` in daemon output. Should be 8+.

3. **Pop blocks and resync**
   ```shell
   letheand --pop-blocks 100
   ```
   This removes the last 100 blocks and resyncs.

### Database Corruption

**Symptoms**: LMDB errors, crashes during sync, "Failed to open database".

**Solutions**:

1. **Try database salvage**
   ```shell
   letheand --db-salvage
   ```

2. **If salvage fails, resync from scratch**
   ```shell
   # Backup first!
   mv $HOME/Lethean/data/lmdb $HOME/Lethean/data/lmdb.bak

   # Restart daemon - will resync
   letheand
   ```

3. **Use blockchain import for faster recovery**
   Download from `https://seed.lethean.io/blockchain.raw` and import.

---

## Wallet Issues

### Wallet Shows Zero Balance

**Causes**: Wallet not synced, wrong restore height, or using wrong seed.

**Solutions**:

1. **Wait for sync to complete**
   Check that wallet height matches daemon height.

2. **Rescan blockchain**
   ```
   rescan_bc
   ```
   Run this command inside the wallet CLI.

3. **Restore with earlier height**
   When restoring from seed, use a restore height before your first transaction.

### "Daemon is busy" Error

The daemon is processing and can't respond to wallet requests.

**Solutions**:

1. Wait for daemon to finish syncing
2. Try again in a few minutes
3. Check daemon is actually running

### Transaction Stuck as "Pending"

**Causes**: Low fee, network congestion, or daemon issues.

**Solutions**:

1. **Wait** - Most transactions confirm within 20 minutes
2. **Check transaction status** on a block explorer
3. **If daemon restarted**, the wallet may need to rescan

### Can't Connect to Remote Node

**Solutions**:

1. **Check node address**
   ```shell
   lethean-wallet-cli --daemon-host=seed.lethean.io
   ```

2. **Try alternative nodes**
   - `seed.lethean.io`
   - `nodes.hashvault.pro`

3. **Check firewall**
   Ensure outbound connections to port 48772 are allowed.

---

## Build Issues

### CMake Errors

**"CMakePresets.json includes missing file"**

```shell
make clean
```

Never manually delete build folders—always use `make clean`.

**"Could not find Conan"**

The build system installs Conan automatically. If it fails:
```shell
pip install conan
```

### Compilation Fails

1. **Check dependencies**
   See [Build Guide](../getting-started/developer/build.md) for required versions.

2. **Clean and rebuild**
   ```shell
   make clean
   make mainnet
   ```

3. **Check compiler version**
   - GCC: 8.4.0+ (recommended 9.4.0+)
   - MSVC: 2017+ (recommended 2022)
   - XCode: 12.3+ (recommended 14.3+)

### "Recursive clone" Errors

Submodules not initialized:
```shell
git submodule update --init --recursive
```

---

## Network Issues

### No Incoming Connections

Your node works but doesn't receive connections from others.

**Solutions**:

1. **Forward port 48772** in your router
2. **Check firewall** allows incoming TCP on 48772
3. **Verify with external port checker**

### High Latency / Slow Responses

**Solutions**:

1. **Check bandwidth** - Node requires consistent connectivity
2. **Reduce max connections** if resources limited
3. **Check system resources** - CPU/RAM usage

---

## SDK / API Issues

### "Connection Refused"

**Causes**: Daemon not running, wrong port, or RPC not enabled.

**Solutions**:

1. **Verify daemon is running**
   ```shell
   curl http://127.0.0.1:48782/info
   ```

2. **Check RPC is enabled**
   Default is enabled. If you used custom flags, ensure RPC wasn't disabled.

3. **For remote access**, daemon needs:
   ```shell
   letheand --rpc-bind-ip=0.0.0.0 --confirm-external-bind
   ```

### Empty or Unexpected API Responses

1. **Check daemon is synchronized**
   ```shell
   curl http://127.0.0.1:48782/info | grep synchronized
   ```

2. **Verify API version**
   ```shell
   curl http://127.0.0.1:48782/info/version
   ```

---

## Getting More Help

If these solutions don't resolve your issue:

1. **Check logs**
   - Daemon: `$HOME/Lethean/data/lethean.log`
   - Look for ERROR or WARN messages

2. **Search existing issues**
   [GitHub Issues](https://github.com/LetheanNetwork/blockchain/issues)

3. **Ask the community**
   [Discord](https://discord.com/invite/lethean-lthn-379876792003067906)

When reporting issues, include:
- Operating system and version
- Lethean version (`letheand --version`)
- Relevant log excerpts
- Steps to reproduce

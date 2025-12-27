---
title: Blockchain Node
description: Run a Lethean node to support the network and maintain your own copy of the blockchain.
---

# Lethean Blockchain Node

Running your own node strengthens the network and provides maximum privacy for your transactions.

## Requirements

### Hardware

| Component | Minimum | Recommended |
|-----------|---------|-------------|
| **CPU** | 2 cores | 4+ cores |
| **RAM** | 4 GB | 8 GB |
| **Storage** | 50 GB SSD | 100 GB SSD |
| **Network** | 10 Mbps | 50+ Mbps |

!!! tip "SSD Recommended"
    The blockchain database performs many random reads. An SSD significantly improves sync speed and overall performance compared to HDD.

### Network

| Port | Protocol | Purpose |
|------|----------|---------|
| 48772 | TCP | P2P (required for full participation) |
| 48782 | TCP | RPC (optional, for wallet/API access) |

If behind a firewall or NAT, forward port **48772** for incoming connections.

### Sync Time Estimates

| Method | Time | Notes |
|--------|------|-------|
| Fresh sync | 4-12 hours | Depends on connection speed |
| Blockchain import | 30-60 minutes | Download pre-synced data |

## Downloads

!!! info

    === "Windows"

        [Download Windows CLI](https://github.com/LetheanNetwork/blockchain-iz/releases/latest/download/windows.tar){ .md-button }
        [Blockchain Export](https://seed.lethean.io/blockchain.raw){ .md-button }

    === "MacOS"

        [Download macOS CLI](https://github.com/LetheanNetwork/blockchain-iz/releases/latest/download/lethean-cli-macos.zip){ .md-button }
        [Blockchain Export](https://seed.lethean.io/blockchain.raw){ .md-button }
      

    === "Linux"

        [Download Linux CLI](https://github.com/LetheanNetwork/blockchain-iz/releases/latest/download/linux.tar){ .md-button }
        [Blockchain Export](https://seed.lethean.io/blockchain.raw){ .md-button }
        


## Data Location



=== "Windows"
    
    ``` shell
    %USERPROFILE%\\Lethean\\data\\lmdb 
    ```

=== "MacOS"

    ``` shell
    $HOME/Lethean/data/lmdb 
    ```

=== "Linux"

    ``` shell
    $HOME/Lethean/data/lmdb
    ```



## Using the CLI

!!! example

    === "Windows"

        1. Press the Windows key
        2. type `cmd.exe` + Press Enter
        3. change directory to Lethean user data `cd %USERPROFILE%\\Lethean\\`

    === "MacOS"

        1. Press the `CMD` + `SPACE` 
        2. type `Terminal` + Press Enter
        3. change directory to Lethean user data `cd $HOME/Lethean`

    === "Linux"

        1. Open your preferred Terminal
        2. change directory to Lethean user data `cd $HOME/Lethean`
        

### Stopping a running daemon


=== "Windows"
    
    ``` shell
    taskkill /IM "letheand.exe" /F
    ```

=== "MacOS"

    ``` shell
    $HOME/Lethean/data/lmdb 
    ```

=== "Linux"

    ``` shell
    $HOME/Lethean/data/lmdb
    ```

### Background Daemon

=== "Windows"
    
    ``` shell
    %USERPROFILE%\\Lethean\\cli\\letheand.exe --detach 
    ```

=== "MacOS"

    ``` shell
    $HOME/Lethean/cli/letheand --detach 
    ```

=== "Linux"

    ``` shell
    $HOME/Lethean/cli/letheand --detach 
    ```
<img width="1184" alt="image" src="https://user-images.githubusercontent.com/631881/171013324-7bd68896-0eb1-4c74-b91a-fdaccaa1041c.png">
    
### Interactive

=== "Windows"
    
    ``` shell
    %USERPROFILE%\\Lethean\\cli\\letheand.exe 
    ```

=== "MacOS"

    ``` shell
    $HOME/Lethean/cli/letheand
    ```

=== "Linux"

    ``` shell
    $HOME/Lethean/cli/letheand
    ```
<img width="1184" alt="image" src="https://user-images.githubusercontent.com/631881/171013058-6035dfe8-65e1-4f4c-9e06-c0c95afa1f0b.png">

### Exporting Chain data


=== "Windows"
    
    ``` shell
    %USERPROFILE%\\Lethean\\cli\\lethean-blockchain-export.exe --data-dir=%USERPROFILE%\\Lethean\\data --output-file=%USERPROFILE%\\Lethean\\data\\blockchain.raw
    ```

=== "MacOS"

    ``` shell
    $HOME/Lethean/cli/lethean-blockchain-export --data-dir=$HOME/Lethean/data --output-file=$HOME/Lethean/data/blockchain.raw
    ```

=== "Linux"

    ``` shell
    $HOME/Lethean/cli/lethean-blockchain-export --data-dir=$HOME/Lethean/data --output-file=$HOME/Lethean/data/blockchain.raw
    ```
<img width="1188" alt="image" src="https://user-images.githubusercontent.com/631881/171013450-62460e66-6813-450d-a868-40bc1761ebb9.png">

### Importing Chain data

=== "Windows"
    
    ``` shell
    %USERPROFILE%\\Lethean\\cli\\lethean-blockchain-export.exe --data-dir=%USERPROFILE%\\Lethean\\data --input-file=%USERPROFILE%\\Lethean\\data\\blockchain.raw
    ```

=== "MacOS"

    ``` shell
    $HOME/Lethean/cli/lethean-blockchain-export --data-dir=$HOME/Lethean/data --input-file=$HOME/Lethean/data/blockchain.raw
    ```

=== "Linux"

    ``` shell
    $HOME/Lethean/cli/lethean-blockchain-import --data-dir=$HOME/Lethean/data --input-file=$HOME/Lethean/data/blockchain.raw
    ```

---

## Monitoring Your Node

### Check Status

While the daemon is running, you can check its status:

```shell
# In a separate terminal, use the RPC interface
curl http://127.0.0.1:48782/getinfo
```

Or connect to a running daemon:
```shell
letheand status
```

### Key Metrics

| Metric | Healthy Value |
|--------|---------------|
| `height` | Should match network height |
| `outgoing_connections_count` | 8+ peers |
| `incoming_connections_count` | 0+ (depends on port forwarding) |
| `synchronized` | `true` |

---

## Troubleshooting

### Sync Stuck or Slow

1. **Check connections**: Ensure port 48772 is accessible
2. **Add seed nodes**: Restart with `--add-priority-node=seed.lethean.io:48772`
3. **Use blockchain import**: Download and import the chain file (faster for initial sync)

### Database Errors

If you encounter LMDB errors:

1. Stop the daemon
2. Backup your data directory
3. Try running with `--db-salvage`
4. If issues persist, delete `data/lmdb` and resync

### Out of Disk Space

The blockchain grows over time. If you run out of space:

1. Stop the daemon
2. Move the data directory to a larger drive
3. Update paths or create symlinks
4. Restart the daemon

### Connection Refused

If wallet can't connect to your local daemon:

1. Verify daemon is running
2. Check it's listening on the expected port
3. Ensure no firewall blocking localhost connections

---

## Advanced Configuration

### Command Line Options

| Option | Description |
|--------|-------------|
| `--data-dir=<path>` | Custom data directory |
| `--log-level=<0-4>` | Logging verbosity |
| `--rpc-bind-ip=0.0.0.0` | Allow remote RPC (use with caution) |
| `--confirm-external-bind` | Required for non-localhost RPC binding |
| `--max-concurrency=<n>` | Limit CPU threads |

### Running as a Service

For production deployments, run the daemon as a system service:

=== "Linux (systemd)"

    Create `/etc/systemd/system/letheand.service`:
    ```ini
    [Unit]
    Description=Lethean Daemon
    After=network.target

    [Service]
    Type=simple
    User=lethean
    ExecStart=/opt/lethean/letheand --non-interactive --data-dir=/var/lib/lethean
    Restart=always

    [Install]
    WantedBy=multi-user.target
    ```

    Then enable and start:
    ```shell
    sudo systemctl enable letheand
    sudo systemctl start letheand
    ```

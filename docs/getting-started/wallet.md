---
title: Wallet
description: Set up and secure your Lethean wallet for sending, receiving, and storing LTHN.
---

# Lethean Wallet

This guide covers setting up the CLI wallet, security best practices, and common operations.

## Quick Start

Choose your platform and download the CLI tools. You can connect to a remote node immediately—no blockchain download required.

!!! info

    === "Windows"

        [Download Windows CLI](https://github.com/LetheanNetwork/blockchain-iz/releases/latest/download/windows.tar){ .md-button }
        [Blockchain Export](https://seed.lethean.io/blockchain.raw){ .md-button }

        Remote Hosts: `seed.lethean.io`, `nodes.hashvault.pro`

    === "MacOS"

        [Download macOS CLI](https://github.com/LetheanNetwork/blockchain-iz/releases/latest/download/lethean-cli-macos.zip){ .md-button }
        [Blockchain Export](https://seed.lethean.io/blockchain.raw){ .md-button }

        Remote Hosts: `seed.lethean.io`, `nodes.hashvault.pro`
      

    === "Linux"

        [Download Linux CLI](https://github.com/LetheanNetwork/blockchain-iz/releases/latest/download/linux.tar){ .md-button }
        [Blockchain Export](https://seed.lethean.io/blockchain.raw){ .md-button }

        Remote Hosts: `seed.lethean.io`, `nodes.hashvault.pro`

## Data Location



=== "Windows"
    
    ```shell
    %USERPROFILE%\\Lethean\\wallets 
    ```

=== "MacOS"

    ``` shell
    $HOME/Lethean/wallets
    ```

=== "Linux"

    ``` shell
    $HOME/Lethean/wallets
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
        

### New Wallet 


=== "Windows"
    
    ```shell
    cd %USERPROFILE%\\Lethean\\wallets && ..\\cli\\lethean-wallet-cli.exe --daemon-host=seed.lethean.io --generate-new-wallet=wallet
    ```

=== "MacOS"

    ``` shell
    cd $HOME/Lethean/wallets && ../cli/lethean-wallet-cli --daemon-host=seed.lethean.io --generate-new-wallet=wallet
    ```

=== "Linux"

    ``` shell
    cd $HOME/Lethean/wallets && ../cli/lethean-wallet-cli --daemon-host=seed.lethean.io --generate-new-wallet=wallet
    ```

### Restore Wallet from Seed


=== "Windows"
    
    ```shell
    cd %USERPROFILE%\\Lethean\\wallets && ..\\cli\\lethean-wallet-cli.exe --daemon-host=seed.lethean.io -restore-deterministic-wallet --generate-new-wallet=wallet
    ```

=== "MacOS"

    ``` shell
    cd $HOME/Lethean/wallets && ../cli/lethean-wallet-cli --daemon-host=seed.lethean.io -restore-deterministic-wallet --generate-new-wallet=wallet
    ```

=== "Linux"

    ``` shell
    cd $HOME/Lethean/wallets && ../cli/lethean-wallet-cli --daemon-host=seed.lethean.io -restore-deterministic-wallet --generate-new-wallet=wallet
    ```


### Restore Wallet From Keys


=== "Windows"
    
    ```shell
    cd %USERPROFILE%\\Lethean\\wallets && ..\\cli\\lethean-wallet-cli.exe --daemon-host=seed.lethean.io --generate-new-keys=wallet
    ```

=== "MacOS"

    ``` shell
    cd $HOME/Lethean/wallets && ../cli/lethean-wallet-cli --daemon-host=seed.lethean.io --generate-new-keys=wallet
    ```

=== "Linux"

    ``` shell
    cd $HOME/Lethean/wallets && ../cli/lethean-wallet-cli --daemon-host=seed.lethean.io --generate-new-keys=wallet
    ```



### Open Wallet

=== "Windows"
    
    ```shell
    cd %USERPROFILE%\\Lethean\\wallets &&  ..\\cli\\lethean-wallet-cli --daemon-host=seed.lethean.io --wallet-file=wallet 
    ```

=== "MacOS"

    ``` shell
    cd $HOME/Lethean/wallets && ../cli/lethean-wallet-cli --daemon-host=seed.lethean.io --wallet-file=wallet
    ```

=== "Linux"

    ``` shell
    cd $HOME/Lethean/wallets && ../cli/lethean-wallet-cli --daemon-host=seed.lethean.io --wallet-file=wallet
    ```

---

## Security Best Practices

### Protect Your Seed Phrase

When you create a wallet, you'll receive a **25-word seed phrase**. This is the master key to your funds.

!!! danger "Critical Security"

    - **Write it down on paper**—not digitally
    - Store in a secure, fireproof location
    - Never share it with anyone
    - Never enter it on websites or send via email/chat
    - Anyone with your seed phrase has full control of your wallet

### Verify Your Backup

After writing down your seed phrase, verify it works:

1. Create a test wallet with a small amount
2. Close the wallet
3. Restore from your seed phrase
4. Confirm the balance appears correctly

### Use Strong Passwords

When prompted for a wallet password:

- Use at least 16 characters
- Mix uppercase, lowercase, numbers, and symbols
- Don't reuse passwords from other services
- Consider a password manager

### Secure Your Environment

| Risk | Mitigation |
|------|------------|
| Malware | Use a clean, updated operating system |
| Keyloggers | Consider a hardware wallet for large holdings |
| Phishing | Only download from official sources |
| Physical access | Encrypt your disk, lock your computer |

### Remote Node Security

When using `--daemon-host` with a remote node:

- Your **view key** is shared with the remote node
- The node can see your incoming transactions
- Your **spend key** remains local—funds cannot be stolen
- For maximum privacy, run your own node

### Recommended Remote Nodes

| Host | Location |
|------|----------|
| `seed.lethean.io` | Official seed node |
| `nodes.hashvault.pro` | Community node |

---

## Troubleshooting

### Wallet Won't Sync

1. Check your internet connection
2. Verify the daemon host is reachable
3. Try an alternative remote node
4. Check firewall settings (port 48772)

### Lost Password

If you forget your wallet password but have your seed phrase:

1. Create a new wallet file
2. Restore from seed phrase
3. Set a new password

!!! warning
    If you lose both your password AND seed phrase, your funds are **permanently inaccessible**.

### Balance Shows Zero

After restoring from seed, you may need to rescan:

```shell
rescan_bc
```

This command (run inside the wallet CLI) rescans the blockchain for your transactions.


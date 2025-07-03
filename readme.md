# Datagram Alpha Testnet 
A step-by-step guide to run Datagram node via CLI
---

## Contents
- [Requirements](#requirements) 
- [Step 1: Sign Up & Get License Key](#step-1-sign-up--get-license-key)  
- [Step 2: Login to your VPS or WSL](#step-2-login-to-your-vps-or-wsl)  
- [Step 3: Import Datagram CLI](#step-3-import-datagram-cli)  
- [Step 4: Run Datagram Node](#step-4-run-datagram-node)  

---
## Requirements

| Component | Minimum | Recommended |
|----------|---------|-------------|
| **CPU**  | 2 cores | 4+ cores     |
| **RAM**  | 4 GB    | 8 GB         |
| **Storage** | 20 GB SSD | 50 GB+ SSD |
| **Network** | 10 Mbps | Stable broadband |
| **OS**   | Ubuntu 20.04/22.04 | Any Linux (incl. WSL) |


## Step 1: Sign Up & Get License Key

- [Sign up here](https://dashboard.datagram.network?ref=568154876 ) 
- Get a free **license key** from **Wallet > License Key**

---

## Step 2: Login to your VPS or WSL

- Connect to your Linux environment (VPS or WSL):

```bash
ssh root@your-vps-ip
````

---

## Step 3: Import Datagram CLI

* Download the latest CLI binary directly:

```bash
wget https://github.com/Datagram-Group/datagram-cli-release/releases/latest/download/datagram-cli-x86_64-linux -O datagram-cli
chmod +x datagram-cli
```

---

## Step 4: Run Datagram Node

* Start a screen session:

```bash
screen -S datagram
```

* Run the node with your license key (replace `YOUR_LICENSE_KEY`):

```bash
./datagram-cli run -- -key YOUR_LICENSE_KEY
```

* Detach from screen (node keeps running):

```
Ctrl + A, then D
```

* To reattach later:

```bash
screen -r datagram
```

---

Your node will run continuously in the background and start earning points.

---

Follow [Alpha Drops](https://x.com/myAlphaDrops) on X

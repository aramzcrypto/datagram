
# Datagram Node CLI Setup Guide  
*Supports: Ubuntu VPS, Linux, and Windows WSL*

---

## Requirements

- **Linux VPS / Native Linux:**  
  - Ubuntu 20.04 or 22.04 (root or sudo access)  
  - Terminal / SSH access (Mac Terminal, VS Code Terminal, or other)  
  - Basic tools: `wget`, `screen`, `chmod`

- **Windows:**  
  - Windows 10/11 with [WSL2 installed and set up](https://learn.microsoft.com/en-us/windows/wsl/install)  
  - Linux distro installed (Ubuntu recommended)  
  - VS Code or Windows Terminal configured to use WSL shell

---

## Step 1: Sign Up & Get License Key

1. Sign up here (use your referral link):  
   👉 https://dashboard.datagram.network?ref=568154876

2. After logging in, go to **Wallet > License Key** section.

3. Copy your **Full Core license key** and save it securely for later.

---

## Step 2: Download Datagram CLI Installer

From your Linux environment (VPS or WSL), download the latest Linux CLI binary:

```bash
wget https://github.com/Datagram-Group/datagram-cli-release/releases/latest/download/datagram-cli-x86_64-linux -O datagram-cli
chmod +x datagram-cli
```

*(If on a VPS and prefer to upload from local machine, use `scp` as shown below.)*

---

## Step 3: Connect to Your Linux Environment

- **Linux VPS:**  
  SSH in from Mac Terminal, VS Code Terminal, or any SSH client:

```bash
ssh root@your-vps-ip
```

- **Windows (WSL):**  
  Open your WSL terminal directly (Ubuntu app or VS Code Terminal with WSL shell).

---

## Step 4: (Optional VPS) Upload Installer via SCP

From your **local machine** (Mac or Windows PowerShell/Git Bash), if you downloaded the CLI locally:

```bash
scp /path/to/datagram-cli root@your-vps-ip:/root/
```

Then on VPS:

```bash
cd /root/
chmod +x datagram-cli
```

---

## Step 5: Fix DNS Issues (Linux VPS Only)

If you get DNS errors on your VPS, fix by:

```bash
sudo nano /etc/systemd/resolved.conf
```

Add or edit:

```ini
[Resolve]
DNS=8.8.8.8 1.1.1.1
FallbackDNS=1.1.1.1 8.8.4.4
```

Save file, then restart resolver and fix resolv.conf:

```bash
sudo systemctl restart systemd-resolved
sudo ln -sf /run/systemd/resolve/resolv.conf /etc/resolv.conf
```

Test DNS:

```bash
dig rbq-prod.datagram.network
```

*WSL usually has working DNS out of the box, so no action needed there.*

---

## Step 6: Run Datagram Node in a Screen Session

Start a `screen` session to keep the process alive after logout:

```bash
screen -S datagram
```

Run the node with your license key:

```bash
./datagram-cli run -- -key YOUR_LICENSE_KEY
```

Replace `YOUR_LICENSE_KEY` with the key from step 1.

To detach from screen without stopping the process, press:

```
Ctrl + A, then D
```

To reattach later:

```bash
screen -r datagram
```

---

## Step 7: Confirm Node Status & Earn Points

- Visit your [Datagram Dashboard](https://dashboard.datagram.network?ref=568154876)  
- Confirm your node is **connected and online**  
- Your node will start accumulating points automatically while running

---

## Notes

- On **Windows WSL**, treat your shell exactly like Linux for these steps.
- On **Linux VPS**, remember to restart the node manually after VPS reboots unless you set up an auto-start service.
- Need help setting up auto-start or troubleshooting? Just ask!

---

*Feel free to open issues or submit pull requests for improvements!*  
*Happy node running! 🚀*

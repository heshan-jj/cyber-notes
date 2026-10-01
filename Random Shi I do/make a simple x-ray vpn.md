---
tags:
  - vpn
  - xray
  - x-ui
  - vless
  - proxy
  - networking
  - devops
  - vps
aliases:
  - Simple X-Ray VPN Setup Guide
  - Xray-UI VPN Setup
  - 3x-ui VPS Installation
---

> [!abstract] Personal Xray-UI (VLESS / TLS / REALITY) VPN Setup Guide
> A step-by-step guide to deploying a high-speed, self-hosted **Xray VPN server** using **X-UI / 3x-ui panel** on a low-cost Cloud VPS. This setup bypasses ISP bandwidth throttling, unblocks restricted protocols, and spoofs traffic using modern proxy protocols (**VLESS**, **REALITY**, and **gRPC/WebSocket**).

---

# Prerequisites & Architecture Overview

```
┌─────────────────────────────────────────────────────────────────────────┐
│                       XRAY PROXY ARCHITECTURE                           │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                         │
│   [ Client Device ]                                                     │
│   (v2rayNG / NekoBox / v2rayN)                                          │
│         │                                                               │
│         │ Encrypted VLESS / REALITY Traffic (Port 443)                  │
│         ▼                                                               │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │  Cloud VPS (Ubuntu 22.04 LTS / Debian 12)                       │   │
│   │                                                                 │   │
│   │  • Xray-Core Service ──────► Proxies Traffic Outward            │   │
│   │  • Web Admin Panel   ──────► Listens on Port 6000-6100           │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│         │                                                               │
│         ▼                                                               │
│   [ Open Internet / Target Websites ]                                   │
│                                                                         │
└─────────────────────────────────────────────────────────────────────────┘
```

### Server Specifications
- **CPU:** 1 vCPU (minimum).
- **RAM:** 512 MB – 1 GB RAM (Requires Swap file setup on 1GB nodes).
- **OS:** Ubuntu 22.04 LTS or Debian 11/12 (64-bit).
- **Cloud Providers:** AWS Free Tier, Linode / Akamai, DigitalOcean, Vultr, Hetzner.
- **Location Selection:** Choose a VPS datacenter region closest to your physical location (e.g., Singapore, Tokyo, Frankfurt) to achieve minimum ping/latency.

---

# Step 1: Provisioning the Cloud VPS

1. Log into your preferred cloud provider (AWS, Linode, DigitalOcean, Vultr, etc.).
2. Create a new Linux instance/droplet:
   - **OS:** Ubuntu 22.04 LTS.
   - **Plan:** Smallest standard shared CPU tier ($4–$6/month or AWS Free Tier).
   - **Region:** Nearest location (e.g., Singapore).
3. Record the assigned **Public IPv4 Address** and root credentials/SSH key.

> [!image] Placeholder: VPS Creation & Region Selection
> ![Screenshot: Cloud VPS Instance Creation](placeholder_vps_creation.png)
> *[Place screenshot here showing VPS instance creation and IP address assignment]*

---

# Step 2: Configuring Cloud Firewall / Security Groups

Before connecting to your server, you must configure your cloud provider's network firewall (Security Group / Firewall Rules) to permit inbound traffic on specific ports:

| Port | Protocol | Purpose | Access Level |
| :--- | :--- | :--- | :--- |
| **`22`** | TCP | SSH Server Access | Restricted / Public |
| **`80`** | TCP | HTTP Traffic / ACME SSL Validation | Public |
| **`443`** | TCP | HTTPS Traffic / VLESS REALITY Proxy | Public |
| **`6000-6100`** | TCP | Custom X-UI Web Admin Panel (e.g. `6060`) | Public / Restricted |

> [!warning] Security Rule Tip
> Keep your panel port (e.g. `6060`) randomized within the `6000-6100` range to prevent automated scanning bots from discovering your administrative Web UI.

> [!image] Placeholder: Cloud Firewall Inbound Rules
> ![Screenshot: Cloud Firewall Inbound Rules Configuration](placeholder_firewall_rules.png)
> *[Place screenshot here showing inbound firewall rules for ports 22, 80, 443, and 6000-6100]*

---

# Step 3: Connecting to VPS & Initial Environment Setup

Connect to your VPS via terminal (or an SSH client like Termius / PuTTY / PowerShell):

```bash
ssh root@YOUR_SERVER_IP
```

### 1. System Package Updates
Refresh system software repositories and apply system updates:

```bash
sudo apt update && sudo apt upgrade -y
```

### 2. Configure a Swap File (Crucial for 1GB RAM Servers)
On low-resource VPS instances (1 GB RAM or less), intensive tasks or memory spikes can trigger Out-Of-Memory (OOM) kernel crashes. Creating a 2 GB swap file ensures server stability:

```bash
# Allocate a 2GB swap file
sudo fallocate -l 2G /swapfile

# Set restrictive permissions
sudo chmod 600 /swapfile

# Format and activate swap
sudo mkswap /swapfile
sudo swapon /swapfile

# Make swap persistent across reboots
echo '/swapfile none swap sw 0 0' | sudo tee -a /etc/fstab
```

Verify swap is active:
```bash
free -h
```

> [!image] Placeholder: Terminal Output of Swap Creation & Verification
> ![Screenshot: Swap File Creation Terminal Command Output](placeholder_swap_setup.png)
> *[Place screenshot here showing successful swap file creation and `free -h` output]*

---

# Step 4: Installing the Xray-UI / 3X-UI Admin Panel

Elevate to full root privileges if not already logged in as root:

```bash
sudo -i
```

### Execute the One-Click 3X-UI Installation Script

Run the automated installation script (using the actively maintained 3X-UI panel fork):

```bash
bash <(curl -Ls https://raw.githubusercontent.com/mhsanaei/3x-ui/master/install.sh)
```

During installation, the script will present interactive prompts:

1. **Confirm Installation:** Type `y` and press Enter.
2. **Set Admin Username:** Enter a custom admin username (avoid default `admin`).
3. **Set Admin Password:** Enter a strong password.
4. **Set Panel Port:** Enter your chosen custom port within the `6000-6100` range (e.g., `6080`).
5. **Set Web Web Root Path (Optional):** Enter a custom URI path (e.g., `/mysecretpanel/`) for added security.

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    3X-UI INSTALLATION PROMPT SUMMARY                    │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                         │
│   • Username:   custom_admin                                            │
│   • Password:   <Strong_Password>                                       │
│   • Port:       6080                                                    │
│   • Web Path:   /panel/                                                 │
│                                                                         │
└─────────────────────────────────────────────────────────────────────────┘
```

> [!image] Placeholder: Installation Script Terminal Output
> ![Screenshot: X-UI Terminal Script Completion Output](placeholder_script_install.png)
> *[Place screenshot here showing script output with panel URL and login details]*

---

# Step 5: Web Panel Login & Node Configuration

Open a web browser and navigate to your admin panel:

```
http://YOUR_SERVER_IP:6080/
```

Log in using the username and password defined during installation.

> [!image] Placeholder: X-UI Panel Login Screen
> ![Screenshot: X-UI Web Login Interface](placeholder_panel_login.png)
> *[Place screenshot here showing the panel login screen]*

---

## Creating a VLESS-REALITY Inbound Node

1. In the left navigation menu, go to **Inbounds** &rarr; **Add Inbound**.
2. Configure the inbound node settings:

| Setting | Recommended Value | Explanation |
| :--- | :--- | :--- |
| **Remark / Name** | `My-VLESS-Node` | Identifying label for your proxy profile |
| **Protocol** | `vless` | Modern lightweight, fast proxy protocol |
| **Listening Port** | `443` | Standard HTTPS port (bypasses restrictive firewalls) |
| **Client ID (UUID)** | *Auto-generated* | Unique authentication key for your client |
| **Network / Transport** | `tcp` or `grpc` | Transport protocol |
| **Security** | `REALITY` | Next-gen stealth technology replacing standard TLS |
| **Target Website (Dest)** | `www.microsoft.com:443` | Target domain for SNI certificate spoofing |
| **SNI (Server Name)** | `www.microsoft.com` | Domain name visible to external DPI inspectors |

3. Click **Create / Save**.

> [!image] Placeholder: Inbound Node Configuration Modal
> ![Screenshot: Creating VLESS REALITY Inbound Node](placeholder_inbound_config.png)
> *[Place screenshot here showing the filled inbound node creation form]*

---

# Step 6: Exporting & Configuring Client Apps

Once the inbound node is created, locate it in your panel list:

1. Click **QR Code** or **Copy Link** (`vless://...`).
2. Import the configuration into your client device:

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    RECOMMENDED CLIENT APPLICATIONS                      │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                         │
│   • Android:          v2rayNG / NekoBox                             │
│   • iOS:              Shadowrocket / Streisand / FoXray               │
│   • Windows:          v2rayN / NekoRay / V2rayGCS                     │
│   • macOS:            NekoRay / V2rayU / FoXray                       │
│   • Linux:            NekoRay / v2ray-core CLI                        │
│                                                                         │
└─────────────────────────────────────────────────────────────────────────┘
```

3. In your client app:
   - Choose **Import from Clipboard** or **Scan QR Code**.
   - Select the node and click **Connect**.
   - Perform a connection test (Ping / IP check at `https://ipinfo.io`).

> [!image] Placeholder: Client App QR Code Scan & Active Connection
> ![Screenshot: Client App Connection Status](placeholder_client_connect.png)
> *[Place screenshot here showing client application connected with successful ping]*

---

# Troubleshooting & Maintenance

### 1. Panel Unreachable (`Connection Refused`)
- Verify that your VPS cloud provider firewall permits inbound TCP on your custom panel port (e.g. `6080`).
- Verify the service status inside SSH:
  ```bash
  x-ui status
  ```
- Restart the panel service:
  ```bash
  x-ui restart
  ```

### 2. Connected but No Internet Access
- Ensure ports `443` and `80` are open in your cloud firewall.
- Check that the SNI domain (e.g., `www.microsoft.com`) supports HTTP/2 or TLS 1.3 and is accessible from your server location.

### 3. X-UI Service Management Commands
```bash
x-ui           # Opens the interactive management menu
x-ui start     # Starts the panel
x-ui stop      # Stops the panel
x-ui status    # Checks service status
x-ui log       # Displays system error logs
```

---

# Key Summary Checklist

> [!important] Operational Checklist
> - **Server Security:** Keep OS updated (`apt update && apt upgrade`) and change default root passwords.
> - **Port Randomization:** Use custom, non-standard ports for the admin panel UI (`6000-6100`).
> - **Stealth Protocol:** Use **VLESS + REALITY** over port `443` for maximum anti-blocking performance.
> - **Resource Guard:** Always maintain a swap file (`/swapfile`) on 1GB VPS nodes to avoid out-of-memory service kills.
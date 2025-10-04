---
title: "Setting up Cloudflare WARP with WireGuard"
date: 2025-10-03 21:06:00 -0400 # October 3, 2025 | 9:06 PM | UTC-4 (EDT)
categories: [Networking, VPN]
tags: [Cloudflare, Cloudflare WARP, WireGuard, VPN]
---

This article will guide you through the process of setting up Cloudflare WARP in WireGuard on Windows.

### What is Cloudflare WARP?

Cloudflare WARP is Cloudflare’s free VPN service designed to make your internet connection more private and secure. Unlike a traditional VPN that routes your traffic through remote servers to hide things such as your location, WARP focuses on security and speed by securely connecting you to the nearest server in Cloudflare's large global network. This prevents snooping from other third parties, and offers better performance and latency than traditional VPNs. There are some downsides to WARP, such as the inability to change server locations, making this not ideal for bypassing geo-restrictions, but it is a fantastic solution for improving security and privacy with very little impact on network performance.

### Prerequisites
- Windows 10/11
- Basic technical knowledge
- Somewhat recent version of WireGuard installed
- Python 3.11 or newer
- Git

### Setting up `simple-wgcf`
`simple-wgcf` is a tool that I made that allows you to easily generate WireGuard profiles for Cloudflare WARP. It is a fork of `@ViRb3`'s popular tool `wgcf`.

#### Project Setup
1. Open up a PowerShell window and type `cd ~` to enter your home directory.
2. Clone the Git repository by running: `git clone https://github.com/PowerPCFan/simple-wgcf.git`
3. Navigate into the project's directory: `cd simple-wgcf`
4. Create a virtual environment for dependency management: `py -m venv venv`
5. Activate the venv: `.\venv\Scripts\Activate.ps1`
6. Install the required Python packages: `pip install -r requirements.txt`
7. Type `cd app` to enter the application directory.

#### Running the tool
1. Register your WARP account by running `py main.py register`. You will need to accept Cloudflare's ToS.
2. Generate the WireGuard configuration file by running `py main.py generate`.
    - This command has a few options:
        - `--mtu <value>`: Sets the MTU for the WireGuard interface. Default value is 1280. If you don't know what this is, leave it as is. If you experience connectivity issues, try lowering this value. Do not lower it too much as it will cause performance issues and higher CPU usage.
        - `--output <file>`: Specifies the filename for the generated WireGuard config file. Default is `cloudflare-warp-profile`.
3. In the terminal output, you should see a green message like "WireGuard profile saved to `C:\Users\Charlie\.simple-wgcf\cloudflare-warp-profile.conf`" (the path shown will be different for you). Copy this path, as you will need it soon.
3. Open WireGuard, and go to the "Tunnels" tab.
4. In the bottom left corner, click on the dropdown menu next to "Add Tunnel" and select "Import tunnel(s) from file". (Alternatively, you can just press <kbd>Ctrl</kbd>+<kbd>0</kbd>.)
5. In the file selection window, paste in the path you copied in step 3. Paste it into the "File name" field at the bottom of the window, not the 'path bar' at the top. Press <kbd>Enter</kbd> or the "Open" button to import the profile.
6. You're done! Click the "Activate" button to connect to Cloudflare WARP.
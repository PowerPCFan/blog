---
title: "Setting up Cloudflare WARP with WireGuard"
date: 2025-10-04 09:30:00 -0400
categories: [Networking, VPN]
tags: [Cloudflare, Cloudflare WARP, WireGuard, VPN]
---

This article will guide you through the process of setting up Cloudflare WARP in WireGuard on Windows.

## What is Cloudflare WARP?

Cloudflare WARP is Cloudflare’s free VPN service designed to make your internet connection more private and secure. Unlike a traditional VPN that routes your traffic through remote servers to hide things such as your location, WARP focuses on security and speed by securely connecting you to the nearest server in Cloudflare's large global network. This prevents snooping from other third parties, and offers better performance and latency than traditional VPNs. There are some downsides to WARP, such as the inability to change server locations, making this not ideal for bypassing geo-restrictions, but it is a fantastic solution for improving security and privacy with very little impact on network performance.

## Why should I use WARP with WireGuard instead of Cloudflare's official client?
Cloudflare's official client is easy to use and works well for most people, but it has some downsides. Here are some reasons why WireGuard is better than the official client:

- **Open Source**: WireGuard is FOSS (Free + Open Source Software), and the official Cloudflare WARP client is closed source. Cloudflare is a trusted company but it's nice to know exactly what an app is doing if you care about privacy. WireGuard is considered extremely safe and has a great security track record.
- **Compatibility**: The official client is only available for Windows, macOS, Linux, iOS, and Android. That's a lot, but WireGuard works on basically everything. So if you want to use WARP on more obscure platforms or operating systems that Cloudflare doesn't support, WireGuard is the way to go.
- **Speed**: WireGuard is pretty lightweight, and the official client isn't as lightweight as it could be. If you want to run WARP on a low-end device, WireGuard might be faster.
- **Control**: Using WireGuard gives you tons of control over your setup. You can just import the profile and go, but if you're a bit more technical, you can customize things such as MTU, DNS servers, and what apps use the VPN.
- **Automation and scripting**: If you're a power user, you can manage WARP using scripts or automation tools if you use WireGuard. This is not possible with the official client.

However, if you're just a regular user who wants a simple VPN solution, the official client is probably the better choice than having to set up WireGuard.

## Setting up simple-wgcf
`simple-wgcf` is a tool that I made that allows you to easily generate WireGuard profiles for Cloudflare WARP. It is a fork of `@ViRb3`'s popular tool `wgcf`.

### Project Setup (Windows)
1. Open up the [Latest Releases](https://github.com/PowerPCFan/simple-wgcf/releases/latest) page in your browser.
2. Download the `simple-wgcf.exe` file.
3. Make sure that this file is in your home directory to make things easier. Your home directory is `C:\Users\YOUR-USERNAME`. (If you have more technical knowledge, you can put it anywhere and adjust the commands below accordingly.)
4. Open up PowerShell and navigate to your home directory by running `cd ~` (replace `~` with the path you downloaded the file to if you didn't choose your home directory).

### Project Setup (Linux)
Since you're using Linux, I'm assuming you probably have some technical knowledge.
1. Open up the [Latest Releases](https://github.com/PowerPCFan/simple-wgcf/releases/latest) page in your browser.
2. Download the `simple-wgcf` file.
3. Open up your terminal and navigate to the directory you downloaded the file to.
4. Run `chmod +x simple-wgcf` to make the file executable.

### Running the tool (All platforms)
1. Register your WARP account by running `./simple-wgcf register`. You will need to accept Cloudflare's ToS.
2. Generate the WireGuard configuration file by running `./simple-wgcf generate`.
    - This command has a few options:
        - `--mtu <value>`: Sets the MTU for the WireGuard interface. Default value is 1280. If you don't know what this is, leave it as is. If you experience connectivity issues, try lowering this value. Do not lower it too much as it will cause performance issues and higher CPU usage.
        - `--output <file>`: Specifies the filename for the generated WireGuard config file. Default is `cloudflare-warp-profile`.
3. In the terminal output, you should see a green message like "WireGuard profile saved to `C:\Users\Charlie\.simple-wgcf\cloudflare-warp-profile.conf`" (the path shown will be different for you). Copy this path, as you will need it soon.

### Setting up the generated profile in WireGuard (Windows)
1. Download the [WireGuard client for Windows](https://www.wireguard.com/install/) ([direct download link](https://download.wireguard.com/windows-client/wireguard-installer.exe)) and install it.
2. Open the WireGuard client, and go to the "Tunnels" tab.
3. In the bottom left corner, click on the dropdown menu next to "Add Tunnel" and select "Import tunnel(s) from file". (Alternatively, you can just press <kbd>Ctrl</kbd>+<kbd>0</kbd>.)
4. In the file selection window, paste in the path you copied in step 3. Paste it into the "File name" field at the bottom of the window, not the 'path bar' at the top. Press <kbd>Enter</kbd> or the "Open" button to import the profile.
5. You're done! Click the "Activate" button to connect to Cloudflare WARP.

### Setting up the generated profile in WireGuard (Linux)
I don't use Linux myself, so I can't provide exact instructions, but here's a general guide:
1. Install a WireGuard client of your choice
2. Import the .conf profile you copied in the "Running the tool" section.
3. Activate the profile to use WARP.

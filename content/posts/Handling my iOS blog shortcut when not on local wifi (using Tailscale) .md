---
title: "Handling my iOS blog shortcut when not on local wifi (using Tailscale) "
date: 2023-09-10T19:46:39-04:00
draft: true
---
# How I update my blog via Tailscale

To start, this is made possible using [Tailscale](https://tailscale.com/)

As shown in my [previous post](https://blog.alfredoautomation.com/posts/my-first-real-post-from-ios/), my iOS shortcut uses a mapped network directory to a local 10.0 IP address. Which obviously means it won't work when I'm not on WiFi or VPN for my home network.  Using Tailscale I can setup a secondary network location on the Files app but set to my Tailscale  IP

1. First you need to setup Tailscale VPN On-Demand. I have it set to disable Tailscale when on home WiFi but on data or another WiFi to enable. 
2. Next I am updating my shortcut to have an if condition based on network name. Eg: if WiFi is connected to home network, save new blog files to internal 10.0 IP. Otherwise save new blog files to my Tailscale IP. 

Once I finish the shortcut and test I'll share it here. 
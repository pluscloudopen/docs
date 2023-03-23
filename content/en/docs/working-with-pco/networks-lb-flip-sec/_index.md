---
title: "Networks, Loadbalancers, Floating IPs and Security Groups"
weight: 50
date: 2023-02-24
description: >
  Create networks, use Loadbalancers, Floating IPs and Security Groups 
---
## Networking
For your convenience new projects in pluscloud open are created with a preconfigured network setup, which contains a private network and a router, which connects that private network to the internet. All networking configuration in Horizon is done in the "Network" menu.

![screenshot of the network menu](./image2020-10-16_8-54-52.png)

"**Network Topology**" gives you a diagram of your current network setup. "**Networks**" lists all currently configured networks in your project and allows you to manage existing, delete existing and create new networks. "**Routers**" lists all configured routers in your project and allow management, creation and deletion of routers. "**Security Groups**" are basically firewall rules which are used to allow or deny traffic to or from your infrastructure. "**Load Balancers**" lets you create, delete and manage loadbalancers, members, pools in your environment. "**Floating IPs" lets you manage, attach, detach, acquire public IP addresses for your instances.

### Network Topology
In the network topology menu entry you can get an overview about the networking setup inside your project. The diagram shows your current setup and is updated with every change of the environment. 

<img src="image2020-10-16_9-33-31.png" alt="screenshot of a network topology" width="30%" height="30%" title="Network Diagram">

The above diagram shows two private networks which are connected to a public network ("provider network" in OpenStack language) with two routers. Hovering with your mouse over the diagram shows more information and shortcuts to other functions.
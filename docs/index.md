# About

Welcome to NodeTunnel’s documentation website.

NodeTunnel is an open-source multiplayer peer for **Godot**, created by **curtjs**, focused on making “host/join” multiplayer feel simple even when players are behind NATs or restrictive networks. citeturn1view0

## Why NodeTunnel exists

Godot’s high-level multiplayer is great once players can connect — the hard part is *getting* that connection working for real players without:
- NAT traversal headaches
- port forwarding
- dedicated servers just to get started

NodeTunnel’s goal is to remove those setup barriers by routing traffic through a relay server so peers can communicate regardless of network setup. citeturn1view0

## How it works (concept)

NodeTunnel’s basic flow looks like this:
1. Connect to a relay server
2. Receive an **Online ID** (example: `ABC12345`)
3. One player hosts, the other joins using that ID
4. From there, you use **normal Godot multiplayer** (RPCs, authority, spawners, etc.) citeturn1view0

In other words: the relay forwards packets between players so they can connect even when they can’t directly reach each other. citeturn1view0

## Project status

NodeTunnel is currently **early / experimental**. Expect bugs, breaking changes, and API changes. It’s not recommended for production use yet. citeturn1view0

## Free public relay

curtjs provides a **free public relay** for testing:

- Host: `relay.nodetunnel.io`
- Port: `9998`

Don’t rely on it for anything important — uptime is not guaranteed, and self-hosting resources are still evolving. citeturn1view0

## License and community

NodeTunnel is released under the **MIT License**. citeturn1view0

For help, bug reports, and updates, use:
- GitHub Issues
- the project’s Discord server citeturn1view0

---

There will be more stuff here soon.

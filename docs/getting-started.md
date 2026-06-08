# Getting Started with Yggdrasil in the NovaNet Context

This guide helps you set up a working Yggdrasil node and begin experimenting as part of the yggdrasil-novanet research.

## 1. Installation

### Linux (Debian/Ubuntu example)
```bash
# Official packages or build from source
# See https://yggdrasil-network.github.io/installation.html for current options
```

### Docker
See `prototypes/docker/` for example Dockerfiles and Compose setups.

### Other Platforms
Official support exists for macOS, Windows, Android, iOS, and more.

## 2. Configuration Basics

Generate a persistent config:

```bash
yggdrasil -genconf > /etc/yggdrasil.conf
```

Key sections to edit:
- `Peers`: Add public peers (from the community list) or your own nodes.
- `Listen`: If you want to accept incoming peerings.
- `AllowedPublicKeys`: Whitelist specific peers for higher security.
- Private key handling (keep stable for persistent address).

Run with:

```bash
yggdrasil -useconffile /etc/yggdrasil.conf
```

## 3. Firewalling (Essential)

Yggdrasil makes your node reachable from the entire mesh by default.

Example (nftables / ip6tables):

```bash
# Allow only specific services on the Yggdrasil interface
ip6tables -A INPUT -i tun0 -p tcp --dport 22 -j ACCEPT
ip6tables -A INPUT -i tun0 -j DROP
```

Always start restrictive and open only what you need.

## 4. Verifying Connectivity

```bash
yggdrasilctl getPeers
yggdrasilctl getTree
ping6 <other-mesh-ipv6-address>
```

## 5. Next Experiments

- Advertise a /64 prefix for your LAN
- Set up a multi-node Docker testbed
- Explore service discovery on the mesh
- Test mobility / link failure recovery

See the roadmap and architecture documents for planned directions.
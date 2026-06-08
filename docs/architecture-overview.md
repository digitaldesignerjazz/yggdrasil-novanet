# Architecture Overview — Yggdrasil as NovaNet Foundation

## High-Level Layers

1. **Underlay Network** (existing Internet, LANs, point-to-point links, IPv4/IPv6)
2. **Yggdrasil Overlay Mesh** (this layer)
   - Cryptographic identities
   - Self-organizing peering
   - Compact routing (spanning tree + Bloom filters + greedy)
   - E2E encrypted IPv6 transport
3. **Higher Layers** (to be prototyped in this repo)
   - Service discovery & naming
   - Pub/sub or messaging
   - Blockchain / consensus node connectivity
   - AI agent swarm coordination
   - Application-specific protocols

## Why Yggdrasil Fits the NovaNet Vision

- **Zero-config friendly** on local networks (multicast peering)
- **Global reach** via public peers or self-hosted well-connected nodes
- **Stable cryptographic addresses** — perfect for long-lived node identity
- **Low state** — suitable for edge devices and large meshes
- **Self-healing** — good resilience for dynamic or mobile components
- **E2E encryption** — strong baseline confidentiality

## Key Trade-offs

- Routing is compact but not always shortest-path optimal (depends on peering)
- No built-in strong anonymity (use additional layers if required)
- Tree-based elements mean well-connected "core" nodes improve global performance

## Integration Opportunities

- Run Yggdrasil alongside or instead of other mesh solutions
- Use Yggdrasil IPv6 for direct P2P between blockchain nodes
- Layer higher-level routing or DHTs on top for specific use cases
- Combine with hardware (routers, single-board computers) for physical mesh extensions

Further technical details are in the research/ directory.
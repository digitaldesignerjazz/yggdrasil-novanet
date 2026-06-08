# Yggdrasil Routing Notes & Research Summary

## Core Routing Mechanism (as of v0.5.x)

Yggdrasil uses a **hybrid compact routing** scheme designed for scalability in large or sparse meshes:

### 1. Spanning Tree
- Provides synchronization and a global reference frame.
- Nodes self-assign tree coordinates relative to a dynamically determined root.
- Used for bootstrap, path setup messages, and fallback routing.
- Self-arranging and can re-form on topology changes.

### 2. Bloom Filters
- Nodes exchange compact Bloom filters describing reachable keyspace neighbors via each tree link.
- Enables efficient probabilistic indication of reachability without full routing tables.
- Low memory overhead (~1 KB per on-tree link in analyses).

### 3. Greedy + Tree-Assisted Forwarding
- Packets are forwarded using a combination of:
  - Tree coordinates for structured progress toward the destination.
  - Greedy local decisions (choose the peer that brings the packet "closer" in the metric space).
  - Previously established source-routed paths that persist until broken.

This keeps per-node state very small compared to traditional link-state or distance-vector protocols.

## Addressing

- Derived directly from the node's Ed25519 public key.
- Results in a stable IPv6 address in the `200::/7` range.
- Nodes can additionally announce a `/64` prefix for subnet routing.

## Encryption Model

- **End-to-end** for the payload: encrypted to the destination's public key.
- Intermediate nodes see only routing headers and encrypted data.
- Cryptographic identity provides source/destination verifiability.

## Performance Characteristics (from studies & observations)

- Memory usage remains low even as network size grows (scales with degree/tree depth rather than global size).
- Good self-healing behavior for mobility and link failures.
- Large MTU support reduces per-packet overhead.
- Path quality is highly dependent on the quality and connectivity of peering relationships.

## Edge Cases & Considerations

- **High churn / mobility**: Handled well but can cause temporary suboptimal paths during re-convergence.
- **Poor peering topology**: Can lead to longer paths or higher latency if the spanning tree becomes deep or unbalanced.
- **Large scale**: Promising due to compact state, but real-world results depend on having a healthy set of well-connected nodes.
- **NAT / CGNAT**: Mostly works because peering is usually outbound-initiated.
- **Firewalling**: Mandatory on the Yggdrasil interface.

## Comparison Highlights

- **vs CJDNS**: Different routing algorithm; Yggdrasil was partly motivated by scaling observations in CJDNS.
- **vs BATMAN-adv / OLSR / Babel**: Yggdrasil is an overlay (works over any IP transport) and designed for global/sparse meshes rather than primarily local Wi-Fi.
- **vs orchestrated meshes (Tailscale, etc.)**: Fully decentralized, no control plane server required.
- **vs anonymity networks (Tor/I2P)**: Different goals — Yggdrasil prioritizes routability and low latency over strong anonymity.

## Open Research Questions for NovaNet Context

- Optimal strategies for maintaining a healthy peering topology at scale.
- Integration patterns for blockchain node discovery and P2P traffic.
- Performance under AI agent swarm workloads (many short-lived or bursty connections).
- Potential future enhancements (link metrics, congestion awareness, better multicast support).

These notes are living documents. Experiments and measurements will be added as prototypes are built.
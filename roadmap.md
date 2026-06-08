# Roadmap — yggdrasil-novanet

## Phase 1: Foundation & Documentation (Current)

- [x] Create repository and initial structure
- [ ] Comprehensive README and project vision
- [ ] Detailed getting-started guide with reproducible setups (Linux, Docker, multi-node)
- [ ] Architecture overview and Yggdrasil routing deep-dive notes
- [ ] Firewall and security hardening templates
- [ ] Public peer recommendations and testing notes

## Phase 2: Prototyping & Integration Experiments

- [ ] Docker Compose multi-node Yggdrasil testbed
- [ ] Subnet advertisement + LAN bridging examples (radvd + Yggdrasil)
- [ ] Service discovery / name resolution patterns on the mesh (mDNS, CoreDNS, custom)
- [ ] Basic pub/sub or message bus experiments over Yggdrasil IPv6
- [ ] Initial integration notes with blockchain node connectivity
- [ ] Mobile / edge device considerations (Android/iOS builds, battery, roaming)

## Phase 3: Scaling, Performance & Research

- [ ] Controlled scaling tests (node count, churn, mobility, tree depth impact)
- [ ] Performance benchmarking (throughput, latency, CPU/memory under load)
- [ ] Analysis of peering topology effects and recommendations for well-connected nodes
- [ ] Exploration of link quality / dynamic metrics (future Yggdrasil improvements)
- [ ] Comparison studies and hybrid approaches (Yggdrasil + other meshes)

## Phase 4: Higher-Layer Systems & Advanced Use Cases

- [ ] AI agent swarm connectivity patterns over the mesh
- [ ] Blockchain / distributed ledger integration layer (discovery, P2P, consensus-friendly routing)
- [ ] Privacy enhancements (Tor/I2P layered peering or selective traffic)
- [ ] Hardware / embedded prototypes (routers, sensors, IoT gateways)
- [ ] Production-grade deployment patterns and monitoring

## Phase 5: Community & Long-Term

- [ ] Well-documented public testbed participation
- [ ] Contribution guidelines and issue templates
- [ ] Potential upstream contributions or collaboration with Yggdrasil core team
- [ ] Integration with broader NovaNet / xMesh / QNET ecosystem components

---

**Priorities can shift based on experiments and feedback.**  
Current focus: Solid documentation + reproducible prototypes.
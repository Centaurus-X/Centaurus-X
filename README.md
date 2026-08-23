<!--
Centaurus-X GitHub Profile README
Version: 1.2.1
Updated: 2026-08-23
Purpose: Public GitHub profile README
-->

# Centaurus-X

<!-- Tux image by Larry Ewing (lewing@isc.tamu.edu), created with The GIMP -->
<a href="https://github.com/Centaurus-X/linux-engineering-playbook"><img src="https://upload.wikimedia.org/wikipedia/commons/a/af/Tux.png" alt="Tux, the Linux mascot" align="right" width="118"></a>

### Industrial Automation · OT Security · Distributed Systems · Linux Systems Engineering

I design and build **evidence-backed industrial software and secure infrastructure** for systems that interact with real plants, field devices, networks and operational constraints.

My current public engineering portfolio connects four layers that are often treated separately:

**plant engineering → HMI/SCADA → local automation runtime → distributed orchestration**

with explicit attention to **authority, failure behavior, security boundaries, reproducibility and technical validation**.

> The repositories published here represent current public engineering lines and release snapshots of systems and architectures that have been developed and iteratively refined over multiple years. Public Git history therefore does not necessarily represent the complete development history.

**Germany / EU · Remote-first**

> Open to selected remote engineering, architecture, integration and security projects.

<br clear="right">

---

## What I Build

I focus on technically demanding systems at the intersection of:

- **Industrial Automation / OT**
- **HMI / SCADA and plant engineering**
- **Linux systems engineering**
- **Distributed and event-driven systems**
- **Network and infrastructure security**
- **Secure gateways and protocol integration**
- **Reliability and failure-mode engineering**
- **Engineering automation and reproducible validation**

I prefer systems where important behavior is explicit:

- who owns hardware,
- who may mutate state,
- what happens when coordination is unavailable,
- how commands reach terminal results,
- what evidence supports a release,
- and which claims have **not** yet been independently validated.

---

# Centaurus-X Automation Stack

The current public flagship work forms a connected automation engineering stack.

```text
                         ┌──────────────────────────┐
                         │      Plant Factory       │
                         │   engineering & design   │
                         └────────────┬─────────────┘
                                      │
                         semantic plant / HMI /
                           runtime-ready exports
                                      │
                    ┌─────────────────┴─────────────────┐
                    │                                   │
                    ▼                                   ▼
        ┌───────────────────────┐          ┌────────────────────────┐
        │  Automation Control   │          │ Automation System      │
        │      HMI / SCADA      │◄────────►│ Runtime                │
        │ operator visibility   │  state / │ local field authority  │
        │ and command lifecycle │  intent  │ and execution          │
        └───────────────────────┘          └────────────┬───────────┘
                                                       │
                                                       │ field I/O
                                                       ▼
                                            PLC · fieldbus · sensors
                                                   · actuators

        ┌────────────────────────────────────────────────────────────┐
        │              Automation Control Plane                    │
        │ deterministic deployment · fleet orchestration · GitOps │
        │ evidence · audit · rollout                              │
        └──────────────────────────┬─────────────────────────────────┘
                                   │
                      deploys / observes platform workloads
                      without becoming field-I/O authority
                                   │
                                   └──────────────► Runtime / services
```

The repositories remain independently usable and have their own maturity, validation and deployment boundaries.

---

## 1. Automation System Runtime — EXECUTE

### Local-first industrial control with explicit hardware authority

[**View Automation System Runtime →**](https://github.com/Centaurus-X/Automation_System_Runtime)

A distributed industrial automation runtime designed so that **field control remains local to the node that owns the hardware**.

Key engineering areas:

- local-first sensor, rule, state-machine and automation execution
- explicit node ownership and authority fencing
- safety-authorized write paths
- actuator readback confirmation
- durable SQLite journals and mirror outboxes
- MQTT/MQTTS coordination
- TLS / mTLS and PKI boundaries
- Modbus TCP
- S7 / TIA integration boundaries
- OPC UA and additional field-protocol adapter boundaries
- deterministic regression testing
- release validation
- SHA-256 manifests
- SPDX SBOM

### Core principle

> The node that owns the field hardware remains the final authority for that hardware.

Distributed coordination can provide registry, relay, mirroring and audit without becoming a mandatory dependency of the local field-control path.

**Public maturity:** pre-production, technically validated release snapshot.

The project does **not** claim independent safety certification, real-time certification or regulatory compliance.

[Architecture](https://github.com/Centaurus-X/Automation_System_Runtime/blob/main/docs/ARCHITECTURE.md) ·
[Deployment](https://github.com/Centaurus-X/Automation_System_Runtime/blob/main/docs/DEPLOYMENT.md) ·
[Security](https://github.com/Centaurus-X/Automation_System_Runtime/blob/main/SECURITY.md) ·
[Commercial Engineering](https://github.com/Centaurus-X/Automation_System_Runtime/blob/main/COMMERCIAL_LICENSE.md)

---

## 2. Plant Factory — ENGINEER

### Visual plant engineering with reusable semantic automation models

[**View Plant Factory →**](https://github.com/Centaurus-X/Plant_Factory)

Plant Factory connects the visual engineering model with machine-readable automation semantics instead of treating them as unrelated artifacts.

Engineering areas include:

- reusable semantic SVG plant components
- structured plant assemblies
- P&ID-style engineering
- process, medium, signal and energy connections
- explicit ports and I/O assignments
- HMI bindings
- alarms and event-driven animations
- typed functional logic
- IEC timers and counters
- Automation System runtime exports
- Siemens SCL export paths
- deterministic template and logic libraries
- visual and machine-readable release evidence

The current public engineering line includes a **71-template deterministic symbol library** and **33 logic blocks**, with release evidence covering model, server, browser and export behavior.

**Public maturity:** engineering release; not an independently certified safety system.

[Documentation](https://github.com/Centaurus-X/Plant_Factory/tree/main/docs) ·
[Security](https://github.com/Centaurus-X/Plant_Factory/blob/main/SECURITY.md) ·
[Commercial Engineering](https://github.com/Centaurus-X/Plant_Factory/blob/main/COMMERCIAL_LICENSE.md)

---

## 3. Automation Control — OPERATE

### Data-driven HMI/SCADA with a traceable command lifecycle

[**View Automation Control →**](https://github.com/Centaurus-X/Automation_Control)

Automation Control turns Automation System state and Plant Factory exports into an operator-facing browser interface.

The HMI/SCADA layer is generated from a generic state register and structured contracts rather than being hard-coded screen by screen.

Engineering areas include:

- semantic live SVG plant views
- dynamically generated process and actuator controls
- command lifecycle correlation
- trends and historical values
- alarms
- operation history
- diagnostics and logs
- Prometheus and end-to-end metrics
- event-driven WS/WSS updates
- bounded client queues and backpressure handling
- simulator and Proxy Gateway integration
- local, Docker and Kubernetes deployment paths
- multilingual runtime UI

The project records functional tests, browser screenshots, integrity evidence and explicit deployment gates rather than converting untested targets into production claims.

**Public maturity:** integration / pilot release.

[Documentation](https://github.com/Centaurus-X/Automation_Control/tree/main/docs) ·
[Security](https://github.com/Centaurus-X/Automation_Control/blob/main/SECURITY.md) ·
[Commercial Engineering](https://github.com/Centaurus-X/Automation_Control/blob/main/COMMERCIAL_LICENSE.md)

---

## 4. Automation Control Plane — ORCHESTRATE

### Deterministic fleet orchestration while preserving node-local authority

[**View Automation Control Plane →**](https://github.com/Centaurus-X/Automation_Control_Plane)

Automation Control Plane provides the management and rollout layer for distributed automation services without moving real hardware authority into the orchestration plane.

Engineering areas include:

- immutable SHA-256-bound rollout plans
- deterministic target placement
- resumable multi-step rollout workflows
- separate operator and approver identities
- evidence and append-only audit trails
- direct Helm deployment
- Argo CD and Flux GitOps paths
- outbound-only cluster agents
- Kubernetes orchestration
- rollout pause / resume / rollback boundaries
- observability and health inspection
- explicit write ownership
- external runtime digest binding

A central design boundary is deliberate:

> The management plane may deploy and observe automation workloads, but the machine-owning node remains the final field-I/O authority.

The public release records passed source, integrity, functional and runtime-binding gates while leaving real-cluster, PKI, storage, registry, CNI, GitOps and recovery acceptance gates explicitly open where they were not executed.

**Public maturity:** pre-production with target acceptance still required.

[Documentation](https://github.com/Centaurus-X/Automation_Control_Plane/tree/main/docs) ·
[Security](https://github.com/Centaurus-X/Automation_Control_Plane/blob/main/SECURITY.md) ·
[Commercial Engineering](https://github.com/Centaurus-X/Automation_Control_Plane/blob/main/COMMERCIAL_LICENSE.md)

---

# Security Engineering Line

The automation stack is complemented by lower-level network and application-security engineering.

## NxtGenAppliance — SECURE

### Fail-closed application security for OPNsense / FreeBSD

[**View NxtGenAppliance →**](https://github.com/Centaurus-X/os-nxtgenappliance)

Engineering areas include:

- OPNsense / FreeBSD
- outbound TLS inspection
- inline Suricata IPS
- inbound reverse proxy / WAF
- DNS-over-TLS enforcement
- identity-aware scoped policy
- explicit fail-closed firewall states
- application-security policy
- package reproducibility
- release evidence and integrity verification

The project deliberately distinguishes implemented behavior, project-maintained validation and still-open assurance work.

**Public maturity:** Alpha / Pre-Production; isolated lab use.

---

## Phimantic IPS Security Appliance — INSPECT

### Experimental Suricata-based TLS inspection and verdict enforcement

[**View Phimantic →**](https://github.com/Centaurus-X/Phimantic-IPS-Security-Appliance)

Engineering areas include:

- C11 networking components
- Suricata IDS / IPS
- TLS interception
- HMAC-protected FlowBus verdict enforcement
- fail-closed inspection
- reverse-proxy architecture
- bounded queueing and inflight control
- ruleset validation and runtime reload
- Docker deployment
- web-based Suricata monitoring
- smoke and EICAR-path testing

This repository demonstrates lower-level network and security engineering beyond application-layer integration.

---

# Supporting Engineering Labs

These repositories support testing, infrastructure visibility and systems engineering.

### Network Asset Discovery

[advanced_network_scanner](https://github.com/Centaurus-X/advanced_network_scanner)

Cross-platform network discovery and scanning prototype covering concurrent discovery, service detection, mDNS, LLMNR, SSDP, topology and structured output.

Long-term positioning:

> infrastructure and asset visibility for technical, security and industrial environments.

### Modbus Simulation & Testing

[advanced_modbus_server_dummy_endpoint](https://github.com/Centaurus-X/advanced_modbus_server_dummy_endpoint)

Modbus TCP simulation and testing environment for client development, OT integration, failure simulation and automation-system validation without requiring a complete physical plant.

### Linux Engineering Playbook

[linux-engineering-playbook](https://github.com/Centaurus-X/linux-engineering-playbook)

Practical Linux systems-engineering documentation covering Linux administration, systemd, Proxmox VE, Python environments, PostgreSQL, GPU/CUDA and service integration.

---

# Engineering Capabilities

| Domain | Technologies & Engineering Areas |
|---|---|
| **Industrial / OT** | Modbus TCP, MQTT/MQTTS, S7/TIA boundaries, OPC UA boundaries, fieldbus integration, hardware I/O, plant engineering |
| **HMI / SCADA** | semantic SVG, dynamic controls, alarms, trends, diagnostics, operator workflows, process visualization |
| **Distributed Systems** | authority models, event-driven architecture, durable convergence, orchestration, GitOps, Kubernetes |
| **Security** | Suricata IDS/IPS, TLS inspection, PKI, mTLS, fail-closed design, trust boundaries, secure gateways |
| **Networking** | TCP/IP, MQTT, WebSockets, proxies, service discovery, network scanning, asset discovery |
| **Systems** | Linux, systemd, FreeBSD, OPNsense, Proxmox VE, containers |
| **Languages** | Python, C, Rust, Bash, JavaScript |
| **Persistence** | PostgreSQL, SQLite |
| **Observability** | metrics, Prometheus, health models, structured logs, release evidence |
| **Validation** | regression tests, browser tests, release gates, SHA-256 verification, SBOM, reproducible artifacts |
| **Deployment** | systemd, Docker/Compose, Helm, Kustomize, Argo CD / Flux integration boundaries |

---

# Engineering Principles

## Local authority before unnecessary central dependency

Critical local functionality should continue where technically possible when a higher-level coordinator, broker or management plane is unavailable.

## Explicit boundaries

Authority, authentication, write ownership, trust and failure behavior should be visible in the architecture rather than emerging accidentally from implementation details.

## Fail safely

Security-sensitive and control-sensitive paths should prefer explicit rejection over ambiguous or uncontrolled behavior.

## Evidence over claims

I distinguish between:

- implemented functionality,
- project-maintained validation,
- target-system qualification,
- independent certification,
- and assumptions that have not yet been validated.

These are not interchangeable.

## Reproducibility

Where appropriate, releases include or work toward:

- automated regression tests,
- release validation,
- deterministic artifacts,
- SHA-256 manifests,
- SBOMs,
- known limitations,
- target-acceptance gates,
- and documented deployment boundaries.

## Honest maturity labeling

Experimental, prototype, pilot, alpha, pre-production and production-qualified are different engineering states.

Repository-specific documentation is the authoritative source for maturity and validation scope.

---

# Engineering Services

I am open to selected **remote-first engineering and consulting engagements**, particularly where software development meets infrastructure, industrial systems, distributed control or security.

Typical areas include:

### Industrial & OT Engineering

- industrial software architecture
- distributed automation architecture
- Modbus / MQTT integration
- protocol and gateway integration
- Linux-based automation systems
- HMI/SCADA integration
- plant-model and runtime integration
- simulator and test-environment development
- failure-mode engineering

### Platform & Distributed Systems

- Linux platform architecture
- worker / control-plane separation
- deterministic rollout concepts
- Kubernetes integration
- GitOps integration
- infrastructure automation
- deployment engineering
- observability and health models

### Security Engineering

- network-security architecture
- secure gateway design
- TLS / PKI / mTLS integration
- Suricata IDS / IPS integration
- security-boundary analysis
- fail-closed architecture
- security hardening
- logging and detection architecture

### Architecture & Technical Review

- architecture reviews
- authority and trust-boundary reviews
- design validation
- failure-mode review
- integration planning
- technical feasibility analysis
- migration planning
- technical validation strategies
- engineering documentation

### Custom Engineering

For suitable projects:

- custom protocol adapters
- specialized automation tooling
- infrastructure tooling
- proof-of-concept development
- HMI/SCADA integrations
- testing and simulation environments
- release and qualification tooling

---

# NIS2 / KRITIS / OT Security Direction

A growing area of my public positioning is the technical engineering side of security for regulated and critical-infrastructure environments.

Relevant technical areas include:

- asset visibility
- network architecture and segmentation
- identity and access boundaries
- secure communication
- PKI / mTLS
- vulnerability exposure
- security monitoring
- logging and detection
- resilience
- backup and recovery architecture
- incident readiness
- technical evidence and validation

I do **not** claim NIS2, IEC 62443, IEC 61508 or other certifications or regulatory compliance where these have not been independently established.

The objective is to combine deep systems engineering with structured security and compliance knowledge while keeping claims technically precise.

---

# Open Source → Commercial Engineering

Open source makes engineering work inspectable and allows technical evaluation before a commercial conversation.

A typical path can be:

```text
Open Source
    │
    ▼
Technical Evaluation
    │
    ▼
Architecture Review
    │
    ▼
Proof of Concept
    │
    ▼
Integration Engineering
    │
    ▼
Target Validation
    │
    ▼
Deployment / Migration
    │
    ▼
Operational Engineering
```

Commercial availability depends on the project, licensing model, customer environment and required scope.

---

# Good Project Fits

I am especially interested in projects combining several of these areas:

```text
Industrial Automation
        +
Linux Infrastructure
        +
HMI / SCADA
        +
Networking
        +
Cybersecurity
        +
Distributed Systems
        +
Engineering Automation
```

Particularly relevant environments include:

- manufacturing
- process and plant automation
- OT infrastructure
- industrial IoT / edge systems
- secure infrastructure platforms
- critical technical systems
- network-security infrastructure
- Linux-based appliances
- distributed automation fleets
- security-sensitive integration projects

---

# Project Maturity

Not every repository has the same maturity level.

I use explicit maturity boundaries:

**Research / Experimental**  
Architecture, protocol or implementation research.

**Prototype**  
Functional implementation intended for technical evaluation and further engineering.

**Pilot / Integration**  
Integrated functionality suitable for controlled target evaluation with explicit open acceptance gates.

**Pre-Production**  
Substantially implemented and technically validated, but not independently qualified for arbitrary production environments.

**Production-Qualified**  
Reserved for a defined deployment target that has completed the required qualification and acceptance process.

The repository README, security documentation and release evidence define the authoritative scope for each project.

---

# Archived Engineering Work

Older repositories and frozen snapshots remain available where they document earlier architectures or useful technical history.

They should not automatically be interpreted as currently maintained or production-ready.

Examples:

- [fluux_control_runtime](https://github.com/Centaurus-X/fluux_control_runtime)
- [fluux_control_gateway](https://github.com/Centaurus-X/fluux_control_gateway)
- [path-b-external-suricata-ips_v8.0-beta1-r11-preproduction-testing](https://github.com/Centaurus-X/path-b-external-suricata-ips_v8.0-beta1-r11-preproduction-testing)
- [squid-ng](https://github.com/Centaurus-X/squid-ng)

---

# Work With Me

I am open to selected **remote-first engineering and consulting projects in Germany and the EU**.

Strong project fits typically involve one or more of:

- Industrial / OT systems
- plant engineering
- HMI / SCADA
- Linux infrastructure
- distributed automation
- network security
- secure gateways
- protocol integration
- systems architecture
- technical security engineering
- difficult reliability or integration problems

### Open-source questions

For bugs or repository-specific questions, use the issue tracker of the relevant project.

### Technical discussions

For non-confidential architecture or integration discussions, use GitHub Discussions in the relevant flagship repository.

- [Automation System Runtime Discussions](https://github.com/Centaurus-X/Automation_System_Runtime/discussions)
- [Automation Control Plane Discussions](https://github.com/Centaurus-X/Automation_Control_Plane/discussions)
- [Plant Factory Discussions](https://github.com/Centaurus-X/Plant_Factory/discussions)
- [Automation Control Discussions](https://github.com/Centaurus-X/Automation_Control/discussions)

### Commercial engineering

Commercial engineering information is available directly in the flagship repositories:

- [Automation System Runtime](https://github.com/Centaurus-X/Automation_System_Runtime/blob/main/COMMERCIAL_LICENSE.md)
- [Automation Control Plane](https://github.com/Centaurus-X/Automation_Control_Plane/blob/main/COMMERCIAL_LICENSE.md)
- [Plant Factory](https://github.com/Centaurus-X/Plant_Factory/blob/main/COMMERCIAL_LICENSE.md)
- [Automation Control](https://github.com/Centaurus-X/Automation_Control/blob/main/COMMERCIAL_LICENSE.md)

> Do not post credentials, private plant data, customer information or confidential security details in public issues or discussions.

A dedicated private business contact channel and website can be added later without changing the technical positioning of this profile.

---

## Current Focus

```text
ENGINEER
Plant Factory
      │
      ▼
OPERATE
Automation Control
      │
      ▼
EXECUTE
Automation System Runtime
      │
      ▼
ORCHESTRATE
Automation Control Plane

Across every layer:

Linux · OT · Networking · Security · Evidence
```

---

**Centaurus-X — engineering software where plant design, automation, infrastructure and security meet.**

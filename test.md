# EvoSec-Lab
<div align="center">
  <img src="/assets/photos/test2.jpeg" alt="Enterprise Rack Configuration" width="90%" style="border-radius: 12px; box-shadow: 0 6px 20px rgba(0,0,0,0.25);"/>
</div>

<div align="center" style="margin-top: 16px;">
  <img src="https://img.shields.io/badge/Status:-Active-brightgreen?style=for-the-badge&logo=proxmox&logoColor=white" alt="Lab Status"/>
  <img src="https://img.shields.io/badge/Built:-Solo-blue?style=for-the-badge&logo=github&logoColor=white" alt="Built Solo"/>
  <img src="https://img.shields.io/badge/Nerd_Factor:-11/10-pink?style=for-the-badge&logo=dependabot&logoColor=white" alt="Nerd Factor"/>
  <img src="https://img.shields.io/badge/License-MIT-lightgrey?style=for-the-badge&logo=github&logoColor=white" alt="MIT License"/>
  <img src="https://img.shields.io/badge/LinkedIn-Florian_Stuettgen-blue?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"/>
</div>

---

> [!NOTE]  
> Engineered with **production-level standards**, fully documented, and executed on authentic enterprise-grade hardware.

> [!WARNING]  
> All sensitive information, credentials, or production network data are **obfuscated or excluded**. This lab is fully sanitized.

---

## **Table of Contents**
1. [Key Highlights](#key-highlights)  
2. [At a Glance (Dec 2025)](#at-a-glance-december-2025)  
3. [Physical Platform](#physical-platform)  
    - [Compute & Storage](#compute--storage)  
    - [Network & OOB Management](#network--oob-management)  
    - [Security & SOC Node](#security--soc-node)  
4. [System Architecture](#system-architecture)  
5. [Logical Architecture & Zones](#logical-architecture--zones)  
6. [Professional Impact](#professional-impact)  
7. [100% Solo Operator](#100-solo-operator)  

---

## **Key Highlights**
- **Enterprise-Grade Simulation**  
  Realistic network environments with racks, switches, firewalls, and segmented topologies mirroring production infrastructure.

- **Project Controls Workflows**  
  Structured processes for planning, monitoring, and managing complex IT, networking, and change-controlled operations.

- **Security Experimentation**  
  Controlled deployment of honeypots, tar pits, and monitoring systems for safe adversarial research.

- **Automation & Orchestration**  
  LLM-assisted SaltStack workflows dynamically manage VM topology, deploy states, and ensure operational consistency.

- **Isolated Testing Environment**  
  Fully contained lab environment for risk-free experimentation without touching live systems.

- **Thorough Documentation**  
  Diagrams, notes, and reproducible procedures ensure clarity, repeatability, and transparency.

---

## **At a Glance (December 2025)**
<details open>
<summary><em>Component summary, specifications, and operational status</em></summary>

| Component       | Specification                            | Description                                                                 | Status |
|-----------------|-----------------------------------------|----------------------------------------------------------------------------|--------|
| **Hypervisor**      | Proxmox VE on Dell R710 — 128 GB RAM | Core virtualization platform supporting clustered VM deployments. | 🟩 **Operational** |
| **Storage**         | EqualLogic FS7610 + Avid 18-bay NAS  | Redundant, high-performance iSCSI/NFS storage backbone. | 🟦 **Fully Redundant** |
| **Core Switch**     | Dell X1052P — 52-port VLAN trunking  | Central L2 switching plane for all segments and management networks. | 🟩 **Active** |
| **Perimeter**       | Cisco ASA 5510/5515-X + SonicWall SRA | Boundary firewalls and VPN endpoints enforcing strict zone policies. | 🟩 **Hardened** |
| **SOC Node**        | Panasonic Toughbook running SELKS     | Dedicated IDS/IPS telemetry node with Suricata and ELK stack. | 🟧 **Live DPI** |
| **Network Model**   | Multi-zone, ASA-only L3 routing       | Zero-trust segmentation with strict L3 enforcement. | 🟩 **Zero Trust** |
| **OOB Management**  | OpenGear CM4148 + Rack KVM + HP TFT5600 | Out-of-band remote access for emergency maintenance. | 🟩 **Always Accessible** |

</details>

---

## **Physical Platform**
The EvoSec-Lab is divided into three primary domains: **Compute & Storage**, **Network & OOB Management**, and **Security & SOC Node**.  
Each domain is designed to mirror enterprise operations while remaining fully isolated for experimentation.

### Compute & Storage
<details>
<summary>Click to expand</summary>

<img src="/assets/photos/Compute1.jpg" alt="R710" loading="lazy" width="100%"/>
<img src="/assets/photos/Compute2.png" alt="EqualLogic" loading="lazy" width="100%"/>
<img src="/assets/photos/Storage1.png" alt="Avid" loading="lazy" width="100%"/>

**Compute:**  
- Dell R710 servers with dual Xeon CPUs and 128GB RAM.  
- Hosts Proxmox VE for clustered VMs and containerized workloads.  
- Designed for high availability and resource-intensive simulations.

**Storage:**  
- Dual EqualLogic FS7610 arrays with 18-bay Avid chassis.  
- Provides high-speed, redundant NAS storage for VMs, logs, and backups.  
- Supports iSCSI and NFS protocols for seamless integration.

</details>

### Network & OOB Management
<details>
<summary>Click to expand</summary>

<img src="/assets/photos/switch.jpg" loading="lazy" width="100%"/>
<img src="/assets/photos/patch.jpg" loading="lazy" width="100%"/>
<img src="/assets/photos/console3.jpg" loading="lazy" width="100%"/>
<img src="/assets/photos/console1.jpg" loading="lazy" width="100%"/>

**Network Core:**  
- Dell X1052P switches providing VLAN segmentation and high-throughput L2 switching.  
- Supports lab, DMZ, management, honeypot, and guest networks.  
- PoE for peripheral devices.

**OOB Management:**  
- OpenGear CM4148 and Rack KVMs with HP TFT5600 for console-level access.  
- Provides full control and recovery even during network outages.

</details>

### Security & SOC Node
<details>
<summary>Click to expand</summary>

<img src="/assets/photos/sec1.jpg" loading="lazy" width="100%"/>
<img src="/assets/photos/sec3.jpg" loading="lazy" width="100%"/>
<img src="/assets/photos/sec2.jpg" loading="lazy" width="100%"/>
<img src="/assets/photos/monitor1.jpg" loading="lazy" width="100%"/>
<img src="/assets/photos/monitor2.jpg" loading="lazy" width="100%"/>

**SOC Node:**  
- Panasonic Toughbook running SELKS/NST with Suricata for IDS/IPS.  
- ELK stack integration for real-time analysis.  
- Monitors honeypots and tar pits, feeding data to automation scripts.  

**Honeypots & Tar Pits:**  
- Isolated traps for attacker engagement.  
- Dynamic responses via SaltStack and LLM-driven log analytics.

</details>

---

## **System Architecture**
The lab’s operational behavior is complex; the diagram below represents a **simplified high-level overview**:

<div align="center">
  <img src="https://github.com/FlorianStuettgen/digital-infrastructure-lab/blob/main/assets/photos/diagram.svg" alt="System Diagram" width="1000"/>
  <p><i>
  Shows compute, storage, and network topology. Application VMs run on isolated VLANs; honeypots detect adversaries.  
  SaltStack automates dynamic network adjustments; LLM analytics monitor logs and anticipate attacks in real-time.
  </i></p>
</div>

---

## **Logical Architecture & Zones**
The lab enforces a **zero-trust, segmented model**, with zones categorized by trust level, purpose, and visual identifier:

| Zone       | Trust     | Color  | Purpose                              |
|------------|-----------|--------|--------------------------------------|
| Management | Highest   | 🔵 Blue | Crown jewels & consoles              |
| Core       | High      | 🟢 Green | Proxmox + storage                    |
| DMZ        | Medium    | 🟡 Yellow| Controlled exposure                  |
| Lab        | Medium    | 🟠 Orange| General workloads                    |
| Honeypots  | Low       | 🔴 Red   | Attack surface bait                  |
| Guest      | Lowest    | ⚫ Black | Untrusted devices                     |

---

## **Professional Impact**
| Discipline                | Real-World Skills Demonstrated                                      |
|---------------------------|---------------------------------------------------------------------|
| Network Engineering       | Zone-based firewall design, ASA object-group mastery, VLAN planning |
| Security Engineering      | Suricata tuning, honeypot deployment, attack traffic analysis       |
| SRE / Platform Engineering| Observability, reproducibility, runbook discipline                 |
| DevOps & Automation       | Ansible playbooks, config-as-code, documentation-as-code           |
| Technical Leadership      | End-to-end ownership, systems thinking, risk-aware architecture     |

---

## **100% Solo Operator**
Every cable pulled, ACL written, diagram drawn, and line of Markdown — **one human**.

- Sourced & refurbished all enterprise hardware  
- Designed every security zone & policy from scratch  
- Stood up Proxmox, ASA, SonicWall, Suricata, SELKS  
- Authored full documentation & runbooks  
- Continually iterating features at 2 a.m. for fun  

<p align="center">
  <strong>Built with precision.<br>Documented with obsession.<br>Operated with fire.</strong>
  <br><br>
  <img src="https://img.shields.io/badge/Level-Over_9000-ff0066?style=for-the-badge&logo=dependabot"/>
  <br><br>
  <a href="#evosec-lab">Back to Top</a>
</p>

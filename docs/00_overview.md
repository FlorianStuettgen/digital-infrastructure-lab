\# Digital Fortress Lab – Overview



This document provides a high-level narrative overview of the Digital Fortress Lab: a self-hosted security lab built on enterprise hardware and operated as a small production-style environment. It expands on the README and is intended for anyone who wants to understand how the lab is put together before diving into specific configs or runbooks.



\## Goals



\- Build a compact but realistic enterprise-style network for experimentation

\- Combine Proxmox virtualization, Dell storage, Cisco/SonicWall firewalls, and Suricata/SELKS into one coherent platform

\- Use segmentation, firewall policy, and DPI to control and observe traffic

\- Keep enough documentation that the environment can be understood and rebuilt from scratch



\## Physical Platform (Summary)



\- \*\*Compute:\*\* Dell PowerEdge R710 and Dell EqualLogic FS7610 nodes

\- \*\*Storage:\*\* Avid 18-bay chassis with mixed SAS/SATA, EqualLogic-backed storage

\- \*\*Network:\*\* Dell X1052P core switch, patch panels, OpenGear console manager, rackmount KVM

\- \*\*Security:\*\* Cisco ASA 5510/5515-X, SonicWall SRA 4200

\- \*\*Monitoring:\*\* Toughbook CF-30 with NST/SELKS and Suricata



More detailed hardware breakdown lives in `docs/01\_hardware-inventory.md` (to be expanded).



\## Logical Architecture (Summary)



The lab is divided into management, core services, DMZ, lab, honeypot, and guest zones. Each zone maps to its own VLAN and firewall policy. Most inter-zone traffic is routed and inspected at the firewalls; the core switch primarily handles Layer-2 segmentation and mirroring towards Suricata where needed.



Additional details on addressing, VLANs, and flows live in `docs/02-network-architecture.md`.




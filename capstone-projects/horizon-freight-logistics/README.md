# Capstone Project A – Horizon Freight & Logistics

## Overview
A complete 3-site company network built from scratch, applying every
switching and routing skill from Phase 1 and Phase 2 in a single
integrated design: headquarters plus two independent branch offices,
5 departments, hub-and-spoke OSPF routing.

## Business Scenario
Horizon Freight & Logistics is a shipping and logistics company.
Headquarters houses IT/Admin, Finance, and Operations. Branch A
(Hargeisa) handles Sales and Warehouse. Branch B (Bosaso) is a small,
single-department Customer Support office.

## Topology
See `topology.svg` in this folder — shows all 7 network devices and
all 12 PCs across all 3 sites.

## Network Design

### Sites & Departments
| Site | Department | VLAN | Subnet |
|---|---|---|---|
| HQ | IT/Admin | 10 | 192.168.10.0/29 |
| HQ | Finance | 20 | 192.168.20.0/28 |
| HQ | Operations | 30 | 192.168.30.0/27 |
| HQ | Management | 99 | 192.168.99.0/30 |
| Branch A | Sales | 40 | 192.168.40.0/28 |
| Branch A | Warehouse | 50 | 192.168.50.0/29 |
| Branch A | Management | 99 | 192.168.199.0/30 |
| Branch B | Support | 60 | 192.168.60.0/29 |
| Branch B | Management | 99 | 192.168.201.0/30 |

### WAN Links
| Link | Subnet |
|---|---|
| HQ ↔ Branch A | 192.168.100.0/30 |
| HQ ↔ Branch B | 192.168.102.0/30 |

## Key Design Decisions
- **Hub-and-spoke OSPF topology** — HQ-R1 maintains two independent
  OSPF neighbor relationships (Branch A and Branch B), rather than
  one neighbor over redundant links
- **Router-on-a-stick deployed at a branch office**, not just HQ —
  Branch A's router carries two department VLANs over a single
  trunked link to its own switch
- **Deliberately no WAN redundancy** — neither branch has a backup
  link. This reflects a real business tradeoff: redundancy has a
  cost, and a small single-department office may not justify it
  the way a multi-department HQ does
- **Management VLANs remain fully unrouted at all three sites**,
  preserving the same security boundary established in Lab 07

## Skills Applied (Phase 1 + Phase 2, integrated)
VLANs, 802.1Q trunking, STP root bridge control, port security,
BPDU Guard, EtherChannel (LACP), router-on-a-stick, OSPF single-area
dynamic routing, subnetting sized to actual host counts across a
range of subnet sizes (/27 through /30)

## Verification Commands

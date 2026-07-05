# LAB 03 – Trunking Between Switches

## Overview
Connected two Cisco 2960 switches using an 802.1Q trunk link, extending
VLANs 10 (HR), 20 (Sales), and 99 (Management) consistently across
both switches so departments split across two floors function as one
logical network per department.

## Scenario
Company expanded to a second floor. HR and Sales now have staff on
both floors, but must remain logically unified per department across
both switches.

## Topology
See `topology.svg` in this folder.

## VLANs & Addressing
| VLAN | Name | Subnet |
|---|---|---|
| 10 | HR | 192.168.10.0/29 |
| 20 | Sales | 192.168.20.0/28 |
| 99 | Management | 192.168.99.0/30 |

| Device | IP |
|---|---|
| HQ-SW1 (mgmt) | 192.168.99.1 |
| HQ-SW2 (mgmt) | 192.168.99.2 |

## Skills Practiced
- 802.1Q trunk configuration (`switchport mode trunk`)
- Restricting allowed VLANs on a trunk (`switchport trunk allowed vlan`)
- Native VLAN security (moved off default VLAN 1)
- Manual VLAN consistency across multiple switches (no VTP)

## Verification Commands
\`\`\`
show interfaces trunk
show vlan brief
\`\`\`

## Result
PCs in the same VLAN can now communicate across both switches through
the trunk link. PCs in different VLANs still cannot reach each other,
confirming segmentation is preserved even across multiple switches.

## Files
- `lab-03.pkt` — open in Cisco Packet Tracer
- `topology.svg` — visual topology reference

## Status
✅ Completed — Phase 1 in progress (3 of 6 labs uploaded)

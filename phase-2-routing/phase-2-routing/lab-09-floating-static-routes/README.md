# LAB 09 – Default Routing, Routing Tables & Floating Static Routes

## Overview
Added a redundant WAN link between HQ and the branch office using
floating static routes, so the network automatically fails over to
a backup path if the primary link goes down — no manual
intervention required.

## Scenario
Manager raised a redundancy concern: if the single cable connecting
HQ and the branch office (from Lab 08) failed, the branch would lose
all connectivity. Required: a second physical path that activates
automatically only when needed.

## Topology
See `topology.svg` in this folder.

## Addressing
| Network | Subnet | Purpose |
|---|---|---|
| VLAN 10 (HR) | 192.168.10.0/29 | Existing |
| VLAN 20 (Sales) | 192.168.20.0/28 | Existing |
| VLAN 99 (HQ Mgmt) | 192.168.99.0/30 | Existing, unrouted |
| Primary WAN Link | 192.168.100.0/30 | Existing from Lab 08 |
| **Backup WAN Link** | **192.168.101.0/30** | New — second physical path |
| Branch LAN | 192.168.30.0/29 | Existing |
| Branch Mgmt | 192.168.199.0/30 | Existing, unrouted |

## Key Concepts
- Administrative Distance (AD) — how a router decides which route
  to trust when it learns about the same destination more than
  one way
- Floating static routes — a backup static route with a
  deliberately raised AD (5), so it stays inactive unless the
  primary route (AD 1) disappears from the table
- Reading and interpreting `show ip route` output field by field
  (route code, AD/metric, next-hop)

## Verification Commands

# LAB 11 – OSPF Multi-Area

## Overview
Reorganized the existing single-area OSPF network from Lab 10 into
three areas (0, 1, 2), making both HQ-R1 and BRANCH-R1 Area Border
Routers (ABRs) — without changing any physical cabling or IP
addressing. Demonstrates fault isolation and scalability benefits of
multi-area OSPF over a flat single-area design.

## Scenario
Manager raised a scaling concern after reading about how large
networks avoid putting everything into one OSPF area. The goal was
to understand and demonstrate why area segmentation matters as a
network grows, even though the physical topology stays identical.

## Topology
See `topology.svg` in this folder.

## Area Design
| Network | Area | Reasoning |
|---|---|---|
| HQ LAN (HR, Sales) | Area 1 | HQ's own local networks |
| Branch LAN | Area 2 | Branch's own local network, isolated from HQ changes |
| WAN links (primary + backup) | Area 0 | Mandatory backbone — only path connecting Area 1 and Area 2 |

## Key Concepts
- Area Border Routers (ABRs) and the mandatory Area 0 backbone
- Inter-area routes (`O IA`) vs intra-area routes (`O`)
- Fault isolation — a local topology change in one area no longer
  forces routers in other areas to fully recalculate their tables
- Multi-area OSPF as a scalability technique, not just added
  complexity for its own sake

## Verification Commands

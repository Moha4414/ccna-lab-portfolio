# LAB 04 – Spanning Tree Protocol (STP)

## Overview
Built a redundant link between two Cisco 2960 switches and used STP
to prevent a Layer 2 loop, with HQ-SW1 deliberately configured as the
root bridge through manual priority control.

## Scenario
Manager wanted a backup cable between two switches for redundancy, but
was concerned that adding a second physical link between the same two
switches could cause instability. Solution: implement STP correctly so
one link forwards, the redundant link stays in standby, and failover
happens automatically if the primary link fails.

## Topology
See `topology.svg` in this folder.

## Addressing
Unchanged from Lab 03 — VLANs 10 (HR), 20 (Sales), 99 (Management),
same subnets.

## Key Concepts
- Root bridge election (manual priority control via `spanning-tree vlan priority`)
- Root port / designated port / blocking port roles
- Failover behavior when the primary link fails
- Why unmanaged Layer 2 loops cause broadcast storms

## Verification Commands

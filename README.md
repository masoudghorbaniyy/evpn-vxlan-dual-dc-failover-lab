# EVPN/VXLAN Dual Data Center Failover Lab

This repository documents my EVPN/VXLAN dual data center lab.

The goal of this lab is to understand how VXLAN, BGP, NAT, and application VIP failover work together in a multi-site design.

## Lab Overview

The lab simulates two data centers:

- Vancouver DC
- Kelowna DC

The design uses FortiGate firewalls as edge/VTEP devices, an underlay network between the sites, Linux servers as application nodes, and a third Linux host as the client/traffic generator.

## What I Tested

- VXLAN overlay between two DCs
- L2 subnet extension across sites
- MAC learning and VXLAN FDB validation
- Linux-based application testing
- Floating internal VIP using keepalived
- Active/standby VIP failover between DC1 and DC2
- DNAT from a public service IP to an internal floating VIP
- SNAT fix for asymmetric return path
- FortiGate sniffer, bridge table, ARP, and BGP verification

## Key Learning

VXLAN provides the stretched L2 domain that allows the same internal VIP to exist in either data center.

The VIP ownership is handled by keepalived in this lab.

BGP controls the external traffic path, while FortiGate DNAT maps the public service IP to the internal floating VIP.
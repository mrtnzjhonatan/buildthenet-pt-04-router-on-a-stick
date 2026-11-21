# Router-on-a-Stick Office

_Level: foundation — Enterprise Campus & LAN — Subinterfaces · 802.1Q Encapsulation · Inter-VLAN Routing_

**Status: Verified.** Completed on 2026-11-21; every requirement was machine-checked against the network built in BuildTheNet and passed.

Snapshot taken 2026-11-21. Built in a simulation — no physical or production equipment was involved.

## Scenario

Pemberton's departments are separated, and now Sales needs the Engineering file share. The office has one router with one spare port. Route between the three VLANs over a single 802.1Q trunk to that router.

### Why it matters

Router-on-a-stick is the cheapest inter-VLAN routing there is, and it is the configuration that teaches what a trunk actually carries.

## Requirements

| # | Requirement | Status | Checked by |
|---|---|---|---|
| 1 | Trunk the link between the switch and the router. | Passed | Sandbox check |
| 2 | Create one subinterface per VLAN with dot1Q encapsulation. | Passed | Sandbox check |
| 3 | Give each subinterface the gateway address for its VLAN. | Passed | Sandbox check |
| 4 | Confirm a host in one VLAN reaches a host in another. | Passed | Sandbox check |

## Topology

![Topology diagram](topology.svg)

## Addressing

| Device | Interface | Address | Mask | Mode | Gateway |
|---|---|---|---|---|---|
| Router-1 | Gi0/0.10 | 192.168.1.2/24 | 255.255.255.0 | routed |  |
| Router-1 | Gi0/0.20 | 192.168.2.2/24 | 255.255.255.0 | routed |  |
| PC-1 | Eth0 | 192.168.1.4/24 | 255.255.255.0 | VLAN 1 | 192.168.1.2 |
| PC-2 | Eth0 | 192.168.2.4/24 | 255.255.255.0 | VLAN 1 | 192.168.2.2 |

## Device configurations

Running-configs as `show running-config` prints them in the BuildTheNet sandbox. Passwords, secrets, keys and SNMP communities are replaced with `<removed>`.

- [Router-1](configs/Router-1.txt)
- [Switch-1](configs/Switch-1.txt)

---

Built on [BuildTheNet](https://www.buildthenet.io/projects/proj-pt-04-router-on-a-stick)

# Ka-Chow Net: The Radiator Springs Network

A Cisco Packet Tracer network designed for seven units of Radiator Springs as part of CSE421 – Computer Networks.

## Project Overview

The project connects seven different LANs using VLSM, RIPv2, static routing, DHCP, DNS, web and email services, and redundant backup routes.

### Units

- Sheriff Station (SS)
- Luigi Casa-Della Tires (LCT)
- Doc-Hudson Clinic (DC)
- Flo V8 Café (FVC)
- Ramone Body Art (RBA)
- Mater Tow Yard (MTY)
- Wheel Well Motel (WWM)

## Network Base

Base network:

`11.10.0.0/16`

VLSM was used to allocate different subnet sizes according to host requirements.

## Technologies and Concepts Used

- IPv4 Addressing
- VLSM
- Cisco Packet Tracer
- RIPv2
- Static Routing
- Default Static Route
- Exit-Interface Static Routes
- Recursive Static Route
- Floating Static Route
- Route Redistribution
- DHCP
- DHCP Relay (`ip helper-address`)
- DNS
- HTTP
- SMTP / POP3
- ICMP Ping
- Traceroute
- Failover Testing

## Routing Design

SS, RBA, and DC form the RIPv2 Gossip Loop.

LCT and MTY use specific static routes.

WWM uses a default route through FVC.

FVC uses exit-interface static routes.

Two backup mechanisms were implemented:

- FVC → LCT → SS recursive backup path
- LCT → DC → SS floating static backup path

## Network Services

- Central DNS server at Sheriff Station
- DHCP provided by SS router for SS, RBA, and DC
- Dedicated LCT DHCP server for LCT and MTY
- Dedicated FVC DHCP server for FVC and WWM
- Web servers at Sheriff Station and Flo V8 Café
- Local email server for each unit
- Cross-domain email between Sheriff and Flo

## Testing

The network was verified using:

- End-to-end ping tests
- DHCP address allocation
- DNS resolution
- HTTP web access
- Two-way email communication
- RIP routing-table verification
- Recursive static-route failover
- Floating static-route failover

## Failover Example

When the direct FVC–SS serial link was disabled, FVC automatically used its backup route through LCT.

Normal path:

`FVC → SS`

Backup path:

`FVC → LCT → SS`

The backup route was verified using `show ip route`, `ping`, and `traceroute`.

## Tools

- Cisco Packet Tracer
- Cisco IOS CLI


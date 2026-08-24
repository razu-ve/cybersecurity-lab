# Network Basics

## Objective

Understand the basic network configuration of the CyberLab host,
including network interfaces, IP addressing, routing, DNS, and
basic connectivity testing.

## Network Interfaces

### Loopback

- Interface: `lo`
- IPv4: `127.0.0.1/8`
- Purpose: Local communication within the host.

### Wi-Fi

- Interface: `wlp1s0`
- IPv4: `10.x.x.x/24`
- Status: UP
- Address assigned dynamically via DHCP.

### VMware Networks

#### VMnet1

- Interface: `vmnet1`
- IPv4: `172.16.x.x/24`
- Purpose: VMware virtual/host-only networking.

#### VMnet8

- Interface: `vmnet8`
- IPv4: `172.16.x.x/24`
- Purpose: VMware NAT networking.

## Default Gateway

The host uses a private IPv4 gateway in the `10.x.x.x` range.

The default route is associated with the `wlp1s0` interface.

## DNS

DNS configuration is managed by NetworkManager.

A private/local DNS resolver is configured for hostname resolution.

## Routing

The host has:

- A default route through the Wi-Fi interface.
- A directly connected Wi-Fi network.
- A VMware VMnet1 network.
- A VMware VMnet8 network.

## Connectivity Tests

### IPv4 Connectivity

Command:

```bash
ping -c 4 8.8.8.8

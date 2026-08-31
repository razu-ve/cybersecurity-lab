# ARP & Local Network

## Objective

Understand how ARP maps IPv4 addresses to MAC addresses
on a local network and how Linux maintains a neighbor cache.

---

## 1. What is ARP?

ARP (Address Resolution Protocol) is used on IPv4 networks
to discover the MAC address associated with a local IPv4 address.

When a Linux host needs to communicate with another device
on the same local IPv4 network, it needs the destination
device's MAC address to deliver the Ethernet frame.

Linux stores discovered mappings in a neighbor cache.

---

## 2. View the Neighbor Table

Command:

    ip neigh

Purpose:

Displays the Linux neighbor table, including:

- IPv4 addresses
- MAC addresses
- Network interfaces
- Neighbor states

Observed entry:

    10.xx.xxx.45 dev wlp1s0 lladdr 16:9x:3c:xx:x7:2e STALE

This shows that the gateway IPv4 address
10.xx.xxx.45 is associated with the MAC address
16:9x:3c:xx:x7:2e on interface wlp1s0.

---

## 3. View the Routing Table

Command:

    ip route

Purpose:

Displays how the system decides where network traffic
should be sent.

Relevant route:

    default via 10.xx.xxx.45 dev wlp1s0

This shows that 10.xx.xxx.45 is the default gateway
for the host.

The local Wi-Fi network is:

    10.xx.xxx.0/24

The host's IPv4 address is:

    10.xx.xxx.236

---

## 4. View Network Interfaces

Command:

    ip addr

Purpose:

Displays network interfaces, IP addresses, MAC addresses,
and interface states.

The primary wireless interface is:

    wlp1s0

The host IPv4 address is:

    10.xx.xxx.236/24

The interface is currently UP.

VMware virtual interfaces are also present:

- vmnet1
- vmnet8

---

## 5. Test Gateway Connectivity

Command:

    ping -c 1 10.xx.xxx.45

Purpose:

Tests connectivity between the CyberLab host and its
local network gateway.

Result:

- 1 packet transmitted
- 1 packet received
- 0% packet loss
- Round-trip time: approximately 4.09 ms

This confirms that the host can successfully communicate
with the local gateway.

---

## 6. Observe the Neighbor Table Again

Command:

    ip neigh

After sending the ping, the neighbor table showed:

    10.xx.xxx.45 dev wlp1s0 lladdr 16:92:3cxx.xxx7:2e DELAY

The IPv6 neighbor entry was also present:

    fe80::1492:3xx.xxx672e dev wlp1s0
    lladdr 16:92:xx.xxx:2e router REACHABLE

The neighbor state can change depending on recent network
activity.

---

## 7. Commands Used

The following commands were used during this experiment:

    ip neigh
    ip route
    ip addr
    ping -c 1 10.14.xx.xxx
    ip neigh

---

## 8. Key Observations

- The primary network interface is wlp1s0.
- The host IPv4 address is 10.1xx.xxx36/24.
- The default gateway is 10.xx.xxx.
- The gateway MAC address is 16:xx.xxx9:67:2e.
- The gateway was present in the Linux neighbor table.
- The initial neighbor state was STALE.
- After the ping, the IPv4 neighbor state changed to DELAY.
- The gateway responded successfully to the ICMP ping.
- No packet loss was observed during the gateway test.
- An IPv6 neighbor entry for the gateway was also observed.

---

## 9. Important Concepts

### IPv4 Address

Identifies a device/interface at the IP layer.

Example:

    10xx.xxx236

### MAC Address

Identifies a network interface at the Ethernet/link layer.

Example:

    16:9xx.xxx7:2e

### Default Gateway

The device used to forward traffic outside the local network.

Example:

    10xx.xxx.45

### Neighbor Cache

Linux maintains recently learned IP-to-MAC mappings
in its neighbor cache.

The command:

    ip neigh

can be used to inspect these mappings.

---

## 10. Learning Outcome

This experiment demonstrated how Linux discovers and stores
local network neighbor information.

The experiment covered:

- ARP fundamentals
- IPv4-to-MAC mapping
- Linux neighbor cache
- Default gateway
- MAC addresses
- Network interfaces
- Neighbor states
- Local gateway connectivity
- IPv6 neighbor information

---

## Methodology

Learn → Build → Investigate → Document → Share

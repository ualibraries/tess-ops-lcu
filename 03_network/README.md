# Network Capacity

## Overview

Primary networking capacity in the LCU is supplied by a pair of [Dell S4048-ON
top-of-rack switches][s4048], configured as a redundant pair via Dell's Virtual
Link Trunking (VLT) technology.  All LCU capacity is dual-connected to the "A"
and "B" side switches; as much as possible, those links are configured in 
active/active Link Aggregation Groups (LAGs).  Each S4048 uplinks to the
building routers via a single 10 GbE connection (with planned capacity for
adding additional 10 GbE uplinks if needed).

An additional (non-redundant) [Netgear GS748T][gs748t] switch is used to support
an out-of-band management subnet; any LCU gear with an administrative or
management port (IPMI etc.) is single-connected to this switch.  The Netgear
switch uplinks to the building routers via a single 1 GbE uplink port.

## VLAN Information

| Purpose                   | Tag | Name                  | CIDR              | Network        | Netmask         | Gateway        | Broadcast      | Private? | Routed? | VRF      |
| ------------------------- | --- | --------------------- | ----------------- | -------------- | --------------- | -------------- | -------------- | -------- | ------- | -------- |
| Out-of-Band Management    | 104 | OOB-management        | 10.130.143.128/25 | 10.130.143.128 | 255.255.255.128 | 10.130.143.129 | 10.130.143.255 | yes      | yes     | LIB-MPLS |
| Qumulo NAS                | 110 | scale-out_NAS_Cluster | 10.131.90.0/23    | 10.130.90.0    | 255.255.254.0   | 10.131.90.1    | 10.131.91.255  | yes      | yes     | LIB-MPLS |
| SimpliVity HCI Management | 111 | MainLibDC_Mgmt        | 10.130.146.128/25 | 10.130.146.128 | 255.255.255.128 | 10.130.146.129 | 10.130.146.255 | yes      | yes     | LIB-MPLS |
| SimpliVity HCI Federation | 112 | MainLibDC_Fed         | 10.130.147.0/25   | 10.130.147.0   | 255.255.255.128 | 10.130.147.1   | 10.130.147.127 | yes      | yes     | LIB-MPLS |
| SimpliVity HCI Storage    | 113 | MainLibDC_Storage     | 10.130.147.128/25 | 10.130.147.128 | 255.255.255.128 | 10.130.147.129 | 10.130.147.255 | yes      | yes     | LIB-MPLS |

## Issues

*   Not an issue per se, but Network Services has offered us a big block of
    10.x space within which we could do all of our own subnetting, routing, etc.,
    rather than having them manage our individual VLANs -- sounds like a good idea,
    but it means there's a big re-IP'ing task coming before we get too far down
    the road. (mgs, 3/24/2017)



[s4048]: http://www.dell.com/us/business/p/networking-s-series-10gbe/pd "Dell Networking S-Series Switches"
[gs748t]: https://www.netgear.com/support/product/GS748Tv1.aspx?cid=wmt_netgear_organic "Netgear GS748T Smart Switch"

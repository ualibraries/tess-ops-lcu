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

## Issues

(tbd)


[s4048]: http://www.dell.com/us/business/p/networking-s-series-10gbe/pd "Dell Networking S-Series Switches"
[gs748t]: https://www.netgear.com/support/product/GS748Tv1.aspx?cid=wmt_netgear_organic "Netgear GS748T Smart Switch"

# Management Subnet

## Overview

The out-of-band management subnet connects any of the LCU gear that has a management port
(e.g., IPMI etc.), and puts it on a private campus-routed subnet.  It also provides a pathway
for automation code to query and react to things like the environmental sensors, the power
distribution systems, and so on.

## Allocation

| IP Address     | Hostname      | Purpose                                       |
| -------------- | ------------- | --------------------------------------------- |
| 10.130.143.129 | -             | (default gateway)                             |
| 10.130.143.130 | gs748-1a      | Netgear GS748 Switch, LCU1, "A" Enclosure     |
| 10.130.143.131 | s4048-1a      | Dell S4048-ON Switch, LCU1, "A" Enclosure     |
| 10.130.143.132 | s4048-1b      | Dell S4048-ON Switch, LCU1, "B" Enclosure     |
||||
| 10.130.143.133 | ups-1a        | TrippLite UPS, LCU1, "A" Enclosure            |
| 10.130.143.134 | ups-1b        | TrippLite UPS, LCU1, "B" Enclosure            |
| 10.130.143.135 | pdu-1a-a      | TrippLite PDU, LCU1, "A" Enclosure, "A" Power |
| 10.130.143.136 | pdu-1a-b      | TrippLite PDU, LCU1, "A" Enclosure, "B" Power |
| 10.130.143.137 | pdu-1b-a      | TrippLite PDU, LCU1, "B" Enclosure, "A" Power |
| 10.130.143.138 | pdu-1b-b      | TrippLite PDU, LCU1, "B" Enclosure, "B" Power |
| 10.130.143.139 | watchdog-1a   | Watchdog Monitoring, LCU1, "A" Enclosure      |
| 10.130.143.140 | watchdog-1b   | Watchdog Monitoring, LCU1, "B" Enclosure      |
||||
| 10.130.143.141 | qnas1-1-ipmi  | Qumulo QC40, LCU1, Node 1, IPMI Port          |
| 10.130.143.142 | qnas1-2-ipmi  | Qumulo QC40, LCU1, Node 2, IPMI Port          |
| 10.130.143.143 | qnas1-3-ipmi  | Qumulo QC40, LCU1, Node 3, IPMI Port          |
| 10.130.143.144 | qnas1-4-ipmi  | Qumulo QC40, LCU1, Node 4, IPMI Port          |
| 10.130.143.145 | qnas1-5-ipmi  | Qumulo QC40, LCU1, Node 5, IPMI Port          |
| 10.130.143.146 | qnas1-6-ipmi  | Qumulo QC40, LCU1, Node 6, IPMI Port          |
| 10.130.143.147 | -             | (reserved)                                    |
| 10.130.143.148 | -             | (reserved)                                    |
| 10.130.143.149 | -             | (reserved)                                    |
| 10.130.143.150 | -             | (reserved)                                    |
| 10.130.143.151 | -             | (reserved)                                    |
| 10.130.143.152 | -             | (reserved)                                    |
| 10.130.143.153 | -             | (reserved)                                    |
| 10.130.143.154 | -             | (reserved)                                    |
| 10.130.143.155 | -             | (reserved)                                    |
| 10.130.143.156 | -             | (reserved)                                    |
||||
| 10.130.143.157 | -             | (unused)                                      |
| 10.130.143.158 | -             | (unused)                                      |
| 10.130.143.159 | -             | (unused)                                      |
| 10.130.143.160 | -             | (unused)                                      |
||||
| 10.130.143.161 | smplv1-1-ipmi | SimpliVity Appliance, LCU1, Node 1, IPMI Port |
| 10.130.143.162 | smplv1-2-ipmi | SimpliVity Appliance, LCU1, Node 2, IPMI Port |
| 10.130.143.163 | -             | (reserved)                                    |
| 10.130.143.164 | -             | (reserved)                                    |
| 10.130.143.165 | -             | (reserved)                                    |
| 10.130.143.166 | -             | (reserved)                                    |
| 10.130.143.167 | -             | (reserved)                                    |
| 10.130.143.168 | -             | (reserved)                                    |
| 10.130.143.169 | -             | (reserved)                                    |
| 10.130.143.170 | -             | (reserved)                                    |
| 10.130.143.171 | -             | (reserved)                                    |
| 10.130.143.172 | -             | (reserved)                                    |
| 10.130.143.173 | -             | (reserved)                                    |
| 10.130.143.174 | -             | (reserved)                                    |
| 10.130.143.175 | -             | (reserved)                                    |
| 10.130.143.176 | -             | (reserved)                                    |
||||
| 10.130.143.177 | -             | (unused)                                      |
| to             | -             | -                                             |
| 10.130.143.253 | -             | (unused)                                      |
||||
| 10.130.143.254 | -             | (reserved - UITS Network Services)            |
| 10.130.143.255 | -             | (broadcast address)                           |

## Issues

*   We need to look at how we're firewalling the management subnet, pick some logical way
    of locking it down (maybe w/VPN?), and then implement it. (mgs, 3/27/2017)

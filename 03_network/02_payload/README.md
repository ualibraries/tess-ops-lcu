# Payload Subnets

## Overview

The four payload subnets interconnect the primary LCU capacity (HCI and scale-out NAS capacity) 
using private campus-routed subnets, and (along with the top-of-rack switches) provide 
connectivity outside the server room.  One subnet is used for the Qumulo NAS appliances 
(both data and management); the SimpliVity HCI gear uses three subnets (management, 
federation, and storage).

## Allocations

### Qumulo NAS Subnet

| IP Address     | Hostname      | Purpose                                                                                            |
| -------------- | ------------- | -------------------------------------------------------------------------------------------------- |
| 10.131.90.1    | -             | (default gateway)                                                                                  |
||||
| (rr)           | qnas1-adm     | Qumulo Cluster 1, Administration Address (round-robin "A" records for 10.130.90.11 - 10.130.90.16) |
| 10.130.90.11   | qnas1-1       | Qumulo Cluster 1, Node 1, Permanent Address                                                        |
| 10.130.90.12   | qnas1-2       | Qumulo Cluster 1, Node 2, Permanent Address                                                        |
| 10.130.90.13   | qnas1-3       | Qumulo Cluster 1, Node 3, Permanent Address                                                        |
| 10.130.90.14   | qnas1-4       | Qumulo Cluster 1, Node 4, Permanent Address                                                        |
| 10.130.90.15   | qnas1-5       | Qumulo Cluster 1, Node 5, Permanent Address                                                        |
| 10.130.90.16   | qnas1-6       | Qumulo Cluster 1, Node 6, Permanent Address                                                        |
| 10.130.90.17   | -             | (reserved)                                                                                         |
| 10.130.90.18   | -             | (reserved)                                                                                         |
| 10.130.90.19   | -             | (reserved)                                                                                         |
| 10.130.90.20   | -             | (reserved)                                                                                         |
| 10.130.90.21   | -             | (reserved)                                                                                         |
| 10.130.90.22   | -             | (reserved)                                                                                         |
| 10.130.90.23   | -             | (reserved)                                                                                         |
| 10.130.90.24   | -             | (reserved)                                                                                         |
| 10.130.90.25   | -             | (reserved)                                                                                         |
| 10.130.90.26   | -             | (reserved)                                                                                         |
||||
| (rr)           | qnas1        | Qumulo Cluster 1, Access Address (round-robin "A" records for 10.130.90.31 - 10.130.90.60)         |
| 10.130.90.31   | -            | Qumulo Cluster 1, Floating Address 1                                                                |
| to             | -            |                                                                                                     |
| 10.130.90.60   | -            | Qumulo Cluster 1, Floating Address 30                                                               |
| 10.130.90.61   | -            | (reserved)                                                                                          |
| to             | -            |                                                                                                     |
| 10.130.90.111  | -            | (reserved)                                                                                          |
||||
| 10.130.90.112  | -            | (unused)                                                                                            |
| to             | -            |                                                                                                     |
| 10.130.90.252  | -            | (unused)                                                                                            |
||||
| 10.131.91.253  | -            | VLAN interface IP Address, S4048-1B                                                                 |
| 10.131.91.254  | -            | VLAN interface IP Address, S4048-1A                                                                 |
| 10.131.91.255  | -            | (broadcast address)                                                                                 |

### SimpliVity Management Subnet

### SimpliVity Federation Subnet

### SimpliVity Storage Subnet



## Issues

*   We need to look at how we're firewalling these subnets, pick some logical way
    of locking it down (maybe w/VPN?), and then implement it. (mgs, 3/27/2017)

*   We'll eventually need to add a publically-routed subnet, so that services we
    deploy can be seen off-campus.

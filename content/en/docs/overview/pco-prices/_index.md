---
title: "PCO Prices"
weight: 20
date: 2023-04-26
---

# Introduction

This pricing table provides an overview of the server plans, load balancers, and storage options available, along with their respective costs. To calculate the hourly and monthly prices for each server plan, multiply the number of VCPUs and the amount of RAM (in GB) by their respective unit prices. As of April 2023, the unit prices are as follows:

* vCPU: €0.0205 per hour
* RAM: €0.007 per GB per hour
* Storage: €0.09 per GB per month
* Load balancer: €0.068 per hour

To calculate the monthly cost for a server plan, multiply the hourly cost by the number of hours in a month (assuming 720 hours per month). For example, for the SCS-1V:0.5 plan with 1 VCPU and 0.5 GB RAM, the hourly cost would be ```(1*€0.0205) + (0.5*€0.007) = €0.024```, and the monthly cost would be ```€0.024 * 720 = €17.28```.

The pricing information was last updated in April 2023 and is subject to change.

## Compute

| Name       | VCPUs | RAM (GB) | hourly | monthly |
|------------|-------|----------|--------|---------|
| SCS-1V:0.5 | 1     | 0.5      | €0.024 | €17.28  |
| SCS-1L:1   | 1     | 1        | €0.027 | €19.44  |
| SCS-1V:1   | 1     | 1        | €0.027 | €19.44  |
| SCS-1V:2   | 1     | 2        | €0.030 | €21.60  |
| SCS-1V:4   | 1     | 4        | €0.036 | €25.92  |
| SCS-1V:8   | 1     | 8        | €0.051 | €36.72  |
| SCS-2V:2   | 2     | 2        | €0.037 | €26.64  |
| SCS-2V:4   | 2     | 4        | €0.043 | €30.96  |
| SCS-2V:8   | 2     | 8        | €0.058 | €41.76  |
| SCS-2V:16  | 2     | 16       | €0.086 | €61.92  |
| SCS-4V:8   | 4     | 8        | €0.065 | €46.80  |
| SCS-4V:16  | 4     | 16       | €0.093 | €66.96  |
| SCS-4V:32  | 4     | 32       | €0.158 | €113.76 |
| SCS-8V:8   | 8     | 8        | €0.093 | €66.96  |
| SCS-8V:16  | 8     | 16       | €0.121 | €87.12  |
| SCS-8V:32  | 8     | 32       | €0.186 | €133.92 |
| SCS-16V:32 | 16    | 32       | €0.309 | €222.48 |
| SCS-16V:64 | 16    | 64       | €0.555 | €399.60 |

{{% alert title="Info" %}}
Please note that the prices shown in the table are for plans with 0 Disk storage.
{{% /alert %}}

## Storage

| Name          | units | monthly |
|---------------|-------|---------|
| Block Storage | 1 GB  | €0.09   |

{{% alert title="Object Storage on PCO Fair Use Policy" %}}
Object Storage on PCO is based on Ceph RadosGW and is not subject to additional charges. The quota is limited to 20 GB / 20,000 objects.
{{% /alert %}}

## Network

| Name                | hourly     | monthly    |
| --------------------| -----------| -----------|
| Cloud Load Balancer | €0.068     | €48.96     |

{{% alert title="Traffic Fair Use Policy" %}}
Incoming and Outgoing Standard network usage is not subject to additional charges.
{{% /alert %}}

---
title: MongoDB Capabilities and Limitations
slug: mongodb/capabilities
excerpt: Find out what are the capabilities and limitations of the Public Cloud Databases for MongoDB offer
section: MongoDB
order: 1
---

**Last updated September 3<sup>rd</sup>, 2021**

## Objective

This page provides the technical capabilities and limitations of the Public Cloud Databases for MongoDB offer.

## Capabilities and limitations

### Supported regions

The Public Cloud Databases offer is available in the following regions:

- `BHS` (Beauharnois, Canada)
- `DE` (Frankfurt, Germany)
- `GRA` (Gravelines, France)
- `UK` (London, United Kingdom)
- `WAW` (Warsaw, Poland)

### MongoDB version

The Public Cloud Databases offer supports the following MongoDB versions:

- MongoDB 4.2
- MongoDB 4.4

MongoDB recommends always installing and using the latest stable version of MongoDB. See [MongoDB Versioning](https://docs.mongodb.com/manual/reference/versioning/){.external} for more information.

### Drivers

You can use any one of the [MongoDB-recommended driver](https://docs.mongodb.com/drivers/){.external} to access your cluster.

### Plans

Three plans are available:

- *Essential*
- *Business*
- *Enterprise* (coming soon - stay tuned!)

Here is an overview of the various plans capabilities:

| Plan         | Number of nodes | MongoDB License | BI Connector  | Compass       |
| ------------ | --------------- | --------------- | ------------  | -------       |
| *Essential*  | 1               | Community       | Not Available | Not Available |
| *Business*   | 3 to 8          | Community       | Not Available | Not Available |
| *Enterprise* | 3 to 8          | Enterprise      | Available     | Available     |

Your choice of plan affects the number of nodes your cluster can run as well as the MongoDB license type.

#### Nodes

- *Essential*: The cluster supports at most one node.
- *Business* or *Enterprise*: The cluster can support 3 to 8 nodes.

##### License type

- *Essential* and *Business* plans use the MongoDB Community license.
- *Enterprise* plans upgrade your cluster so that it uses the MongoDB Enterprise license, giving you the capability to use the [MongoDB BI Connector](https://www.mongodb.com/products/bi-connector){.external} as well as [MongoDB Compass](https://www.mongodb.com/products/compass){.external}.

### Hardware resources

Here are the node types you can choose from:

| Name    | Disk (GB) | Cores | Memory (GB) |
| ------- | --------- | ----- | ----------- |
| db1-7   | 50        | 2     | 7           |
| db1-15  | 100       | 4     | 15          |
| db1-30  | 200       | 8     | 30          |
| db1-60  | 400       | 16    | 60          |
| db1-120 | 400       | 32    | 120         |

Right now, all nodes of a given cluster should be of the same type and live in the same regions.

#### Effective storage

The disk size listed above is the total disk size of the underlying machine, however, a small part of it goes towards the OS install.

We try hard to avoid "disk full" situations that could be harmful to cluster health. Therefore, the cluster will become read-only before actually reaching full physical disk capacity. You should aim for no more than 80% disk space usage.

### Networking

MongoDB clusters are reachable through port 27017.

Public networking can be used for all the offers.

Private Networking (vRack) is available for *Business* and *Enterprise*.

When using private networking, some network ports get created in the private network of your choice. Thus, further operations on that network might suffer from some restrictions - e.g. you won't be able to delete the network if you didn't stop the Public Cloud Databases services first.

### Backups

*Essential* plan clusters are automatically backed up daily during their maintenance window. Backup retention is 2 days.

*Business* plan clusters are automatically backed up daily during their maintenance window. Backup retention is 7 days.

*Enterprise* plan clusters are automatically backed up daily during their maintenance window, with [PITR](https://en.wikipedia.org/wiki/Point-in-time_recovery){.external} support. Backup retention is 7 days.

### Users

In order to properly manage your MongoDB cluster, some MongoDB users are set up in your clusters:

- `admin@admin` is your initial user
- `mms-automation@admin` is a technical user required for automation purposes
- `backup-*@admin` are used to perform backups

Furthermore, user creation from the MongoDB Shell is **not** supported: You need to use the OVHcloud API or the OVHcloud Control Panel in order to manage your clusters' users. Any user created through the mongo shell will be deleted by the automation mechanism.

## We want your feedback!

We would love to help answer questions and appreciate any feedback you may have. Join our community of users on <https://community.ovh.com/en/>.

Are you on Discord? Connect to our channel at <https://discord.gg/PwPqWUpN8G> and interact directly with the team that builds our databases service!

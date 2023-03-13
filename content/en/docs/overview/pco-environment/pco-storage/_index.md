---
title: "PCO Storage"
weight: 30
date: 2023-03-10
---

# What are the pluscloud open storage options?

{{% alert title="Note" color="info" %}}
Unless stated otherwise Storage within a pluscloud open environment is High availabile
{{% /alert %}}

## Block Storage

pluscloud open provides block storage based on Ceph. It provides a cost-effective and reliable storage solution for applications that require persistent storage. In addition to the basic block storage functionality, pluscloud open also offers the ability to create snapshots and backups of the volumes, making it easier to manage and restore data. Snapshots allow for point-in-time backups of volumes, while backups provide full copies of the volumes that can be used for disaster recovery or other purposes. 

## Local Storage

{{% alert title="Note" color="info" %}}
pluscloud open will soon offer a local storage option. 
{{% /alert %}}
{{% alert title="Note" color="warning" %}}
Keep in mind that local storage is not replicated, so it's important to ensure data backups are regularly performed.
{{% /alert %}}

pluscloud open offers local storage as an option for storing data on instances. Local storage is non-shared storage that is physically attached to the instance and provides high input/output operations per second (IOPS) and low latency. It is ideal for applications that require high-performance and low latency.

However, local storage has some caveats. It is limited to the size of the instance and cannot be resized. If the instance is deleted or crashes, the data stored in the local storage is lost. Therefore, it is recommended to use local storage only for non-persistent data or temporary workloads that do not require data to be stored for a long period. For persistent data, it is recommended to use distributed block storage or object storage. Additionally, using local storage can limit the ability to scale horizontally as the data stored on local storage is not available on other instances.

## Object Storage on pco

{{% alert title="Note" color="info" %}}
"Object Storage on pco" is designed for moderate amounts of data and file storage needs. However, for larger-scale data storage requirements, PlusServer provides a dedicated solution called "S3 Storage". This solution offers highly scalable, cost-effective object storage with maximum availability, as well as optional georedundancy features. With S3 Storage, users can easily store and retrieve large amounts of data, ensuring data availability and accessibility in case of any infrastructure failure or other disruptions.
{{% /alert %}}
---
title: "Images and Instances"
weight: 50
date: 2023-02-24
description: >
  Creating Instances from Images, Logging in and Grouping them
---
## Overview
When you want to work with Images and Instances (aka virtual machines) in the Horizon web gui you choose "compute" from the menu.
<img src="image2020-10-19_10-42-35.png" alt="screenshot of the compute overview" width="50%" height="50%" title="Compute Overview">

The overview shows your current consumption of cloud ressources and the current limits.

## Instances
The instances menu shows details about all your virtual machines and their current state. From here you can manage you virtual machines and create new ones. Managing your instances covers various aspects which are covered below. 
### Instance Actions Menu
The "Action" menu shows options, which might render your instance unavailable or have impact on its security in red colour:
<img src="image2020-10-19_10-51-36.png" alt="screenshot of the instances action menu" width="60%" height="60%" title="Instances Action Menu">
#### Disassociate Floating IP
Seperate a floating IP address, which is currently attached to your instance, from the instance. Depending on how you access that instance, it might become unreachable via network after this.
#### Attach Interface
Add an additional network interface to your instance. That option will open a requester, which will let you choose the network you want to connect the interface with. If you don't choose a static IP address there, the interface will fetch one via DHCP (as long as that has been enabled for the network). Please be aware, that the new interface might have to be added to the network configuration of your instance (if it doesn't happen automatically).
#### Edit Instance
Here you can change the name of your instance (and its description). Furthermore you can add or remove security groups. If you have different security groups on different network interfaces of your instance choose "Edit Port Security Groups" to edit them seperately.
#### Attach Volume
Volumes, which you have created in the "Volumes" menu, can here be attached to your instance. Be aware, that this only makes the volume available to your instance (e. g. as /dev/sdb in a Linux instance). You have to crate a filesystem on it, add it to /etc/fstab and mount it manually in order to use it.
#### Detach Volume
Volumes which are no longer needed or which should be mounted on another instance can here be detached from an instance. Volumes that are to be detached from an instance should be unmounted from the instance first and applications should no longer access them.
#### Update Metadata
Here you can manage metadata for your instance. There is a set of example metadata from the Glance metadata catalog already available on the left. If you want to use one of the keys just click on "+" to move it to the right. You can create your own metadata keys via the "custom" option.
#### Edit Security Groups
Here you can manage the security groups for your instance. If your instance has more than one network interface changes will be applied to all of them. If you want to manage different security groups for different network interfaces please use "Edit Port Security Groups" from the menu.
#### Edit Port Security Groups
 

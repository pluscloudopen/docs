---
title: "Object Storage"
weight: 50
date: 2023-02-24
description: >
  Manage containers and objects
---

## Overview

Pluscloud open provides [object storage](https://en.wikipedia.org/wiki/Object_storage) compatible to Openstacks [Swift](https://wiki.openstack.org/wiki/Swift) and Amazons [S3](https://docs.aws.amazon.com/AmazonS3/latest/API/Welcome.html) protocols. 
It is basically provided for "cloud native" use cases: 

* as a backend for infrastructure as code scenarios (like backend storage for terraform state files), which can be used by a group of developers.
* as a file/content repository for scale-out scenarios, where cloud instances, spawned from images, would load current content from object storage (instead of mounting an NFS volume, what would be considered as "bad design" in cloud contexts).


---
#https://gohugo.io/content-management/page-bundles/
title: "OpenStack Object Storage as a Backend for Terraform Statefiles"
date: 2023-03-14
description: >
  Manage your Infrastructure as Code (IaC) with Hashicorp Terraform and use OpenStack Object Storage as a Backend
---

## Get your S3 credentials

In order to get your s3 credentials you need your OpenStack client set up correctly. If that's the case, you can enter

``$ openstack ec2 credentials create``

The output of that command should be similar to this:
``
+------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
| Field      | Value                                                                                                                                               |
+------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
| access     | 5aen4quuuQu8ci7aoceeyaek8oodohgh                                                                                                                    |
| links      | {'self': 'https://prod1.api.pco.get-cloud.io:5000/v3/users/poashohhe9eo8EeQuez3ochaeWaeBoiR/credentials/OS-EC2/5aen4quuuQu8ci7aoceeyaek8oodohgh'}   |
| project_id | Eine8Jai4hohzieShoo1iem0yai7fair                                                                                                                    |
| secret     | iek1aechaequa8pheitahNgeizai3eig                                                                                                                    |
| trust_id   | None                                                                                                                                                |
| user_id    | poashohhe9eo8EeQuez3ochaeWaeBoiR                                                                                                                    |
+------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
``

Obviously your credentials should be different (those above are fake). Relevant for S3-access are only the "access" and "secret" values. 

## Create a bucket

With your S3 credentials ready, you need to create a place to store your data in. In S3 terms, this place is called a "bucket". You can either create a bucket via the web ui (Horizon) or on the command line.

### Create a bucket via web ui

Logged in to the web ui (Horizon) you can navigate to "Object Store" in the left menu and then click on "Containers" (that's how buckets are called in Horizon). Click on the "+Container" button then enter a name for your new container, choose a storage policy and choose, whether your new bucket should be accessable publicly or only private (most of the time you would choose private). Click on "Create" to create the new bucket. It should immediately show up in the Container list.

### Create a bucket via s3cmd

To create a bucket in your object storage from the command line you can use the s3cmd cli tool, which should be available as a software package for the workstation you use or from <https://s3tools.org/s3cmd>.
S3cmd needs a configuration file `.s3cfg` like
``
[default]
access_key = 5aen4quuuQu8ci7aoceeyaek8oodohgh
secret_key = iek1aechaequa8pheitahNgeizai3eig
enable_multipart = True
multipart_chunk_size_mb = 50
use_https = True
host_base = https://prod1.api.pco.get-cloud.io:8080
host_bucket = https://prod1.api.pco.get-cloud.io:8080
signurl_use_https = True
socket_timeout = 600
``

Please replace your correct access- and secret-keys and save it to the file `.s3cfg` in your home directory. Using this configuration you should be able to create a bucket in the Object Storage using the command
``
s3cmd mb s3://mytfstate
``

##


``
terraform init \
        -backend-config="key=${S3_BACKEND_KEY}" \
        -backend-config="bucket=${S3_BACKEND_BUCKET}" \
        -backend-config="region=${S3_BACKEND_REGION}" \
        -backend-config="endpoint=${S3_BACKEND_ENDPOINT}" \
        -backend-config="skip_credentials_validation=true"
``

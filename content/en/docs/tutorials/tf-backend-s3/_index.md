---
#https://gohugo.io/content-management/page-bundles/
title: "OpenStack Object Storage as a Backend for Terraform Statefiles"
date: 2023-03-14
description: >
  Manage your Infrastructure as Code (IaC) with Hashicorp Terraform and use OpenStack Object Storage as a Backend
---

## Get your S3 credentials

In order to get your s3 credentials you need your OpenStack client set up correctly. If that's the case, you can enter

``
$ openstack ec2 credentials create
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

With your S3 credentials ready, you need to create a place to store your data in. In S3 terms, this place is called a "bucket".

##


``
terraform init \
        -backend-config="key=${S3_BACKEND_KEY}" \
        -backend-config="bucket=${S3_BACKEND_BUCKET}" \
        -backend-config="region=${S3_BACKEND_REGION}" \
        -backend-config="endpoint=${S3_BACKEND_ENDPOINT}" \
        -backend-config="skip_credentials_validation=true"
``

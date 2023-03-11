---
title: "PCO Environments"
weight: 20
date: 2023-03-10
---

# What is a pluscloud open Environment?

Each pluscloud open environment is designed as a "shared nothing" infrastructure, meaning that each environment is completely independent and does not share any underlying resources or management capabilities with other environments. While this may limit some flexibility in terms of workload placement and management, it enables true geo-redundancy concepts to be implemented by facilitating the isolation of resources and reducing the risk of correlated failures. The management plane within the environment which provides the API endpoints is high-available, ensuring that management operations remain available even in the case of infrastructure failures.

## Public pluscloud open Environments

| Environment | Region   | Availability Zone |
|-------------|----------|-------------------|
| prod1       | DE-WEST  | DE-WEST-1         |
| prod2       | DE-NORTH | DE-NORTH-1        |
| scs1        | DE-WEST  | DE-WEST-2         |

{{% alert title="Note" color="info" %}}
scs1 is a development environment solely provided in the [Sovereign Cloud Stack](https://scs.community) & [GAIA-X](https://gaia-x.eu) context
{{% /alert %}}

### UI/API endpoints

| Environment | horizon/ui                            | keystone                                    |
|-------------|---------------------------------------|---------------------------------------------|
| prod1       | <https://prod1.api.pco.get-cloud.io>  | <https://prod1.api.pco.get-cloud.io:5000>   |
| prod2       | <https://prod1.api.pco.get-cloud.io>  | <https://prod2.api.pco.get-cloud.io:5000>   |
| scs1        | <https://ui.gx-scs.sovereignit.cloud> | <https://api.gx-scs.sovereignit.cloud:5000> |

### terraform provider

The Terraform provider for OpenStack can be found on the Terraform Registry website at <https://registry.terraform.io/providers/terraform-provider-openstack/openstack/latest/docs>. 

This provider enables users to interact with many OpenStack resources. With the Terraform provider for OpenStack, users can create, modify, and delete pluscloud open resources through Terraform configuration files, allowing for streamlined infrastructure management.

### ansible collection

Ansible is a popular automation tool that can be used to configure and manage infrastructure. Ansible provides a collection called `openstack.cloud` which includes a set of Ansible modules to interact with pluscloud open resources. These modules can be used to create, update, delete, and query resources such as virtual machines, networks, security groups, and more. 

The `openstack.cloud` collection is available on the official Ansible website at <https://docs.ansible.com/ansible/latest/collections/openstack/index.html>.
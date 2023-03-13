---
title: "PCO Environments"
weight: 20
date: 2023-03-10
description: >
  Access, URLs, OpenStack CLI preparation, Terraform Provider, Ansible Collections
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

## Access

There are various options to work with pluscloud open environments. You can interact with the webui (Horizon) or with the API.

### credentials

In order to login via Horizon you need the Credentials we provided to you.

* Username 
* Password
* Domain

### OpenStack CLI

There are several options for you to install the OpenStack Client in your environment. Most Linux distributions offer the installation from their package repository (for distributions based on the Debian package >

As the OpenStack Client is written in the Python Programming language, it can be installed via the Python Packaging System, as well (`pip install python-openstackclient`). We would recommend to do this in a Pytho>

A Python venv can be created by executing `python -m venv openstackclient`. Change into the subdirectory and "activate" the virtual environment `cd openstackclient ; . ./bin/activate`. All installation of python >

The third option is to use a Docker container, which includes all required OpenStack Client bits. We would recommend to use the openstackclient Image from [OSISM](https://osism.tech/de). You can pull that contain>

For information using the OpenStack Client we like to refer you to the [upstream documentation](https://docs.openstack.org/python-openstackclient/latest/index.html).

Authentication for the OpenStack Client is configured via files in yaml format. `clouds.yml`, `clouds-public.yml` and `secure.yml` are used to collect the credentials and authentication endpoints of one ore more >

The repository of the SovereignCloudStack (SCS) has two templates for [clouds-public.yml](https://github.com/SovereignCloudStack/docs/blob/main/community/contribute/cloud-resources/clouds-public.yaml) and [clouds>

Using `clouds.yml` and `clouds-public.yml` allows you to specify more than one cloud to login to and choose the cloud you want with the parameter `--os-cloud=` or the environment variable `OS_CLOUD` when using th>

Another option is to download an OpenRC environment file from the Horizon web interface. Being logged into Horizon you click on "<your login name>" in the upper right corner and choose "OpenStack RC File" from th>
Afterwards you 

``source ./<your openstack rc file>-openrc.sh
  Please enter your OpenStack Password for project <yourproject> as user <your login name>``

### terraform provider

The Terraform provider for OpenStack can be found on the Terraform Registry website at <https://registry.terraform.io/providers/terraform-provider-openstack/openstack/latest/docs>. 

This provider enables users to interact with many OpenStack resources. With the Terraform provider for OpenStack, users can create, modify, and delete pluscloud open resources through Terraform configuration files, allowing for streamlined infrastructure management.

### ansible collection

Ansible is a popular automation tool that can be used to configure and manage infrastructure. Ansible provides a collection called `openstack.cloud` which includes a set of Ansible modules to interact with pluscloud open resources. These modules can be used to create, update, delete, and query resources such as virtual machines, networks, security groups, and more. 

The `openstack.cloud` collection is available on the official Ansible website at <https://docs.ansible.com/ansible/latest/collections/openstack/index.html>.

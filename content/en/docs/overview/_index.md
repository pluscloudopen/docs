---
title: "Overview"
weight: 5
date: 2023-02-24
description: >
  Access, URLs, OpenStack CLI preparation
---

# Overview

## URLs

Our regions can be accessed via Horizon Dashboard and OpenStack APIs

| DE-WEST / prod1 | [Horzion Dashboard](https://prod1.api.pco.get-cloud.io/auth/login/) | [OpenStack Auth URL](https://prod1.api.pco.get-cloud.io:5000) | [Object Storage Endpoint S3/Swift)](https://prod1.api.pco.get-cloud.io:8080) |
| DE-NORTH / prod2 | [Horizon Dashboard](https://prod2.api.pco.get-cloud.io/auth/login/) | [OpenStack Auth URL](https://prod2.api.pco.get-cloud.io:5000) | [Object Storage Endpoint S3/Swift)](https://prod2.api.pco.get-cloud.io;8080) |

## credentials

In order to login via Horizon you need the Credentials we provided to you.

* Username 
* Password
* Domain

## OpenStack CLI

There are several options for you to install the OpenStack Client in your environment. Most Linux distributions offer the installation from their package repository (for distributions based on the Debian package system, you could install the package via `apt install python-openstackclient`).

As the OpenStack Client is written in the Python Programming language, it can be installed via the Python Packaging System, as well (`pip install python-openstackclient`). We would recommend to do this in a Python virtual environment (venv) in order to keep this installation seperated from the Python, that might be installed by your Linux distribution.

A Python venv can be created by executing `python -m venv openstackclient`. Change into the subdirectory and "activate" the virtual environment `cd openstackclient ; . ./bin/activate`. All installation of python packages with `pip install` will now take place in the new venv. You can deactivate the venv by executing `deactivate`.

The third option is to use a Docker container, which includes all required OpenStack Client bits. We would recommend to use the openstackclient Image from [OSISM](https://osism.tech/de). You can pull that container, if you have a local Docker or Podman installation on your workstation by executing `docker pull quay.io/osism/openstackclient` or `podman pull quay.io/osism/openstackclient` respectively.

For information using the OpenStack Client we like to refer you to the [upstream documentation](https://docs.openstack.org/python-openstackclient/latest/index.html).

## Authentication

Authentication for the OpenStack Client is configured via files in yaml format. `clouds.yml`, `clouds-public.yml` and `secure.yml` are used to collect the credentials and authentication endpoints of one ore more OpenStack clouds (or pco regions) you want to connect to.

The repository of the SovereignCloudStack (SCS) has two templates for [clouds-public.yml](https://github.com/SovereignCloudStack/docs/blob/main/community/contribute/cloud-resources/clouds-public.yaml) and [clouds.yml](https://github.com/SovereignCloudStack/docs/blob/main/community/contribute/cloud-resources/clouds.yaml.sample).

Using `clouds.yml` and `clouds-public.yml` allows you to specify more than one cloud to login to and choose the cloud you want with the parameter `--os-cloud=` or the environment variable `OS_CLOUD` when using the OpenStack Client.

Another option is to download an OpenRC environment file from the Horizon web interface. Being logged into Horizon you click on "<your login name>" in the upper right corner and choose "OpenStack RC File" from the dropdown menu.
Afterwards you 

``source ./<your openstack rc file>-openrc.sh
  Please enter your OpenStack Password for project <yourproject> as user <your login name>``





---
layout: page
title: DevOps for OPNsense
subtitle: Toolchains for DevOps automation with OPNsense
tags: [ opnsense, devops ]
---

We make automation tools for the rather awesome [OPNsense](https://opnsense.org/) firewall product.

## Configuration Sync for S3 storage
Configuration Sync is a tool designed to one-way synchronize the `config.xml` 
system configuration files from the OPNsense host to S3 compatible object data 
storage in close to real time.  While the tool has the side-effect of being a 
great configuration backup tool the intent is to provide a tool that stores the 
OPNsense system configuration in a location that is readily addressable using 
DevOps automation tools such as through Terraform and others.
 * [verbnetworks.com/2018-08-06-configsync-plugin-for-opnsense/](https://verbnetworks.com/2018-08-06-configsync-plugin-for-opnsense/)


****


## Image Create :: OPNsense on AWS

Terraform module to create an AWS AMI snapshot-image that can subsequently be used to start an OPNsense instance within AWS.
 * [github.com/verbnetworks/terraform-aws-opnsense-image](https://github.com/verbnetworks/terraform-aws-opnsense-image)
 * [registry.terraform.io/modules/verbnetworks/opnsense-image/aws](https://registry.terraform.io/modules/verbnetworks/opnsense-image/aws)

### Example usage
```hcl-terraform
variable "aws_access_key_id" {}       # set via environment value `TF_VAR_aws_access_key_id`
variable "aws_secret_access_key" {}   # set via environment value `TF_VAR_aws_secret_access_key`

module "opnsense-image" {
  source  = "verbnetworks/opnsense-image/aws"

  opnsense_release = "18.7"
  root_passwd = "honeyPot..."

  aws_region = "ap-southeast-1"
  aws_access_key_id = "${var.aws_access_key_id}"
  aws_secret_access_key = "${var.aws_secret_access_key}"

  do_opnsense_install = 1
  do_cleanup_shutdown = 1
  do_image = 1
  do_self_destruct = 1
}
```

NB: the correct behaviour of this module will result in an AMI and the temporary EC2 instance used in the process of 
creating the image will power off.


****


## Image Create :: OPNsense on Digital Ocean

Terraform module to create a Digital Ocean Droplet Image that can subsequently be used to start an OPNsense instance 
within Digital Ocean.
 * [github.com/verbnetworks/terraform-digitalocean-opnsense-image](https://github.com/verbnetworks/terraform-digitalocean-opnsense-image)
 * [registry.terraform.io/modules/verbnetworks/opnsense-image/digitalocean](https://registry.terraform.io/modules/verbnetworks/opnsense-image/digitalocean)

### Example usage
```hcl-terraform
variable "do_token" {}    # set via environment value `TF_VAR_do_token`

module "opnsense-image" {
  source  = "verbnetworks/opnsense-image/digitalocean"

  opnsense_release = "18.7"
  root_passwd = "honeyPot..."

  digitalocean_region = "sgp1"
  digitalocean_token = "${var.do_token}"

  do_opnsense_install = 1
  do_cleanup_shutdown = 1
  do_image = 1
  do_self_destruct = 1
}
```

The correct behaviour of this module will result in a Digital Ocean Droplet image and the temporary Droplet 
used in the process of creating the image will self destruct.


****

## xmlcrudy
Provides a CRUD like interface for manipulating XML files which is useful in interacting with OPNsense XML configuration 
file values.
 * [github.com/verbnetworks/xmlcrudy](https://github.com/verbnetworks/xmlcrudy)

### Example usage
```bash
. /path/to/xmlcrudy.sh
xmlcrudy /conf/config.xml update "//gateways/gateway_item[contains(name,'public4gw')]/gateway" "10.0.0.1"
```

Useful for manipulating values to suit cloud-compute requirements in the boot-process and can be used as a remote-ssh
call for a crude poor-mans API (with caution!) in a pinch.


****

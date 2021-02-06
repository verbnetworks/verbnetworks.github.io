---
layout: post
title: Terraform + Digital Ocean Droplets
---

v0.1.1 of the Terraform + Digital Ocean Droplet has been released.

This Terraform module creates a Digital Ocean Droplet using Terraform with desirable additional features.  The module is 
essentially a wrapper around the Digital Ocean provider using a `cloudinit` script to provide additional features:-
 * remount existing volumes
 * create an initial user with an sshkey


### Code
 * [github.com/verbnetworks/terraform-digitalocean-droplet](https://github.com/verbnetworks/terraform-digitalocean-droplet)

### Terraform Module
 * [registry.terraform.io/modules/verbnetworks/droplet/digitalocean](https://registry.terraform.io/modules/verbnetworks/droplet/digitalocean)

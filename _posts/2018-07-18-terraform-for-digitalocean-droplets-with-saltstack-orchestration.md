---
layout: post
title: Terraform for Digital Ocean Droplets with Saltstack Orchestration
---

Today we release v0.4.1 of our Terraform module for creating Digital Ocean Droplets with Saltstack in a masterless
arrangement.

This release addresses fixes a bug with a hardcoded path bug in the `salt-push` tool and introduces a new variable
`disable_saltminion_service` that (by default) disables the salt-minion service because in the context of a headless
system running the minion serves little purpose.

Plenty more documentation to help describe how to use the module.

### Code
 * [github.com/verbnetworks/terraform-digitalocean-salt-masterless](https://github.com/verbnetworks/terraform-digitalocean-salt-masterless)

### Terraform Module
 * [registry.terraform.io/modules/verbnetworks/salt-masterless/digitalocean](https://registry.terraform.io/modules/verbnetworks/salt-masterless/digitalocean)

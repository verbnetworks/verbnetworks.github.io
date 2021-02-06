---
layout: post
title: Terraform for OPNsense AMI images on AWS and Digital Ocean
---

Today we release the AWS counterpart to our Digital Ocean tool for generating images of OPNsense using Terraform as
the build framework (yes, we know Packer and all).

With the AWS release it is now possible to create AMI images that you can subsequently use to create multi-cloud 
arrangements by establishing cross-cloud VPNs and hence open up the ability to shift your workloads to other cost 
effective providers and regions depending on your requirements.

Alternatively, you may want to consider setting up your own transit links via cloud-compute providers using your onsite 
OPNsense, coupled with your cloud-based OPNsense instances.

In development are the same tool-chains for Google-Cloud-Environment and Microsoft-Azure, at the moment these are on the 
back-burner while we play with other fun tools - if you are interested in GCE or Azure get in touch to give us a reason 
to finish those off.

### AWS
 * [github.com/verbnetworks/terraform-aws-opnsense-image](https://github.com/verbnetworks/terraform-aws-opnsense-image)
 * [registry.terraform.io/modules/verbnetworks/opnsense-image/aws](https://registry.terraform.io/modules/verbnetworks/opnsense-image/aws)

### Digital Ocean
 * [github.com/verbnetworks/terraform-digitalocean-opnsense-image](https://github.com/verbnetworks/terraform-digitalocean-opnsense-image)
 * [registry.terraform.io/modules/verbnetworks/opnsense-image/digitalocean](https://registry.terraform.io/modules/verbnetworks/opnsense-image/digitalocean)


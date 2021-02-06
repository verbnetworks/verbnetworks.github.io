---
layout: post
title: Configuration Sync plugin for OPNsense
---

Today we submitted a [pull-request](https://github.com/opnsense/plugins/pull/777)
for our first public OPNsense plugin, Configuration Sync for OPNsense using S3
compatible storage.

Configuration Sync is a tool designed to one-way synchronize the `config.xml` 
system configuration files from the OPNsense host to S3 compatible object data 
storage in close to real time.  While the tool has the side-effect of being a 
great configuration backup tool the intent is to provide a tool that stores the 
OPNsense system configuration in a location that is readily addressable using 
DevOps automation tools such as through Terraform and others.

## Features
 - Straight-forward setup and configuration that should be easily understood by
   anyone familiar with S3 compatible providers.
 - Configurable duty cycle to detect changes using a low system impact recursive 
   hash mechanism to ensure new configuration files are sync'd out to the S3 
   location with limited delay.
 - All configuration backup files and the current configuration are sync'd to 
   the S3 storage location.
 - S3 object metadata tagging with extra information to ensure your OPNsense 
   configuration files are easily identified, fields include `mtime`, `bytes`,
   `md5`, system `hostid` and `hostname`.
 - Configuration parameter test allowing you confirm your credentials are 
   valid before saving and comitting.
 - Plenty of logging to help you understand what is happening.

## Use cases
 - Cloud compute environments where instances can be destroyed withoutwarning. 
   Because the last running `config.xml` can be collected from a known S3 
   location it becomes possible to respawn the OPNsense instance with the last 
   known configuration using automation tools such as Terraform and others.
 - Configuarion Sync has the side effect of being a very useful configuration 
   backup tool, when combined with S3 storage features such as storage-encryption, 
   access-permissions and access-logging and audit your OPNsense configurations 
   should be well protected.

## Limitations
 - Currently the only S3 storage provider supported is AWS, the underlying 
   boto3 library can support others and this is being worked on.
 - Restoring an OPNsense instance may require more than just the last 
   `config.xml` configuration file, currently there are no known ways to 
   automatically cause required plugins and packages to be downloaded and 
   applied from a base OPNsense image, however this limitation is being worked 
   on as part of another plugin.

## Screen shots
![opnsense-plugin-configsync-01](/img/opnsense-plugin-configsync-01.png "opnsense-plugin-configsync-01")

![opnsense-plugin-configsync-02](/img/opnsense-plugin-configsync-02.png "opnsense-plugin-configsync-02")

![opnsense-plugin-configsync-03](/img/opnsense-plugin-configsync-03.png "opnsense-plugin-configsync-03")

## Pre release binaries
We've packaged the plugin so you can go ahead and try it out before it is 
accepted by the OPNsense team for inclusion as a regular plugin.  All the usual
pre-release warnings apply here, however if you know how to to manually install
a package you can find them [here](https://github.com/verbnetworks/packages/tree/master/opnsense-plugin-configsync).

If you do happen to spot a bug or issue, we'd really like to hear about it,
please submit as an issue [here](https://github.com/verbnetworks/opnsense-plugin-configsync/issues).

## Code repo
Check out code [github.com/verbnetworks/opnsense-plugin-configsync](https://github.com/verbnetworks/opnsense-plugin-configsync)

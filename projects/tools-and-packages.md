---
layout: page
title: Tools and Packages
subtitle: Assorted useful tools and packages
tags: [ arpwitch, arpwatch, oui-database, mac-address, digital-ocean, cakephp ]
---

We are often creating tools and packages that are useful and helpful to others, here is a 
collection of the ones we like.


## ARP Witch
A modern arpwatch tool with JSON formatted oututs and easy options to exec commands when network 
changes are observed.  Optionally integrates with ouilookup to insert vendor data if available.  
 * [github.com/verbnetworks/arpwitch](https://github.com/verbnetworks/arpwitch)
 * [pypi.org/project/arpwitch](https://pypi.org/project/arpwitch/)

**Installation**
```bash
pip install arpwitch
```
<br/>

----
  
## OUI lookup
A console tool and Python library for looking up hardware MAC addresses in the OUI list from ieee.org. 
 * [github.com/verbnetworks/ouilookup](https://github.com/verbnetworks/ouilookup)
 * [pypi.org/project/ouilookup](https://pypi.org/project/ouilookup/)

**Installation**
```bash
pip install ouilookup
```
<br/>

----

## xmlcrudy
xmlcrudy provides a CRUD(+upsert) like shell interface for manipulating XML files.
 * [github.com/verbnetworks/xmlcrudy](https://github.com/verbnetworks/xmlcrudy)

**Usage example** - update the value of an xpath in the file `/conf/config.xml`
```bash
. /path/to/xmlcrudy.sh
xmlcrudy /conf/config.xml update "//gateways/gateway_item[contains(name,'public4gw')]/gateway" "10.0.0.1"
```
<br/>

----

## AWS local-instancedata
This tool is a simple `/bin/sh` tool that uses `curl` (*nix) or `fetch` (BSD) to walk the AWS instancedata 
from http://169.254.169.254 and create a local copy of that data.
 * [github.com/verbnetworks/aws-local-instancedata](https://github.com/verbnetworks/aws-local-instancedata)

**Usage example** - make a local copy of the AWS instance data at `/var/lib/cloud/instance/instance-data`
```bash
. aws-local-instancedata.sh
aws_local_instancedata
```
<br/>

----

## Digital Ocean API Query
A simple bash tool issuing queries to Digital Ocean returning JSON data that can be easily pipe-chained 
through JQ to obtain required data.  Plays well with Terraform.
 * [github.com/verbnetworks/digitalocean-api-query](https://github.com/verbnetworks/digitalocean-api-query)
 
**Usage example** - obtain a list of Digital Ocean droplets in your account 
```bash
digitalocean-api-query droplets | jq .droplets[].id
```
<br/>

----

## SSH knownhost
A dead-simple bash tool for safely adding known fingerprints for SSH servers.  Originally created to 
close-the-loop in automation scenarios that pull code from AWS CodeCommit repositories.
 * [github.com/verbnetworks/ssh-knownhost](https://github.com/verbnetworks/ssh-knownhost)

**Usage example** - add the known ssh-fingerprint to the ./ssh/known_hosts if the remote host matches
```bash
ssh-knownhost git-codecommit.us-east-2.amazonaws.com 3lBlW2g5xn/NA2Ck6dyeJIrQOWvn7n8UEs56fG6ZIzQ >> ~/.ssh/known_hosts
```
<br/>

----

## CakePHP Autocache Plugin
CakephpAutocachePlugin is a CakePHP 2.x Plugin that makes query caching as easy as adding a 
`'autocache'=>true` condition to your Model query - CakePHP is now beyond release v3.6 however this 
Plugin is still in broad use among legacy 2.x based CakePHP web-apps.
 * [plugins.cakephp.org/p/1307-CakephpAutocachePlugin](https://plugins.cakephp.org/p/1307-CakephpAutocachePlugin)
 * [packagist.org/packages/ndejong/cakephp-autocache-plugin](https://packagist.org/packages/ndejong/cakephp-autocache-plugin)
 * [github.com/verbnetworks/CakephpAutocachePlugin](https://github.com/verbnetworks/CakephpAutocachePlugin)  
  ![github_forks](https://img.shields.io/github/forks/verbnetworks/CakephpAutocachePlugin.svg?style=social&label=Fork "Github Forks")
  ![github_stars](https://img.shields.io/github/stars/verbnetworks/CakephpAutocachePlugin.svg?style=social&label=Stars "Github Stars")
<br/>

----

## CakePHP Emogrifier Plugin
CakephpEmogrifierPlugin is a CakePHP 2.x Plugin that makes of using Emogrify on your HTML output easy.  Very
helpful for rendering HTML emails in a way that is consistient among browsers and web-mail clients.
 * [plugins.cakephp.org/p/1309-CakephpEmogrifierPlugin](https://plugins.cakephp.org/p/1309-CakephpEmogrifierPlugin)
 * [github.com/verbnetworks/CakephpEmogrifierPlugin](https://github.com/verbnetworks/CakephpEmogrifierPlugin)  
  ![github_forks](https://img.shields.io/github/forks/verbnetworks/CakephpEmogrifierPlugin.svg?style=social&label=Fork "Github Forks")
  ![github_stars](https://img.shields.io/github/stars/verbnetworks/CakephpEmogrifierPlugin.svg?style=social&label=Stars "Github Stars")
<br/>

----


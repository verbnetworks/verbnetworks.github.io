---
layout: page
title: FauxAPI for pfSense
subtitle: A REST API interface for pfSense to facilitate devops
tags: [ fauxapi, rest, pfsense, devops ]
---

FauxAPI started as a personal project to provide a programmatic interface to pfSense for managing 
changes to the `config.xml` file that defines a pfSense system.  The project has been running for 
2 years and has remained stable across pfSense releases 2.3.x and 2.4.x and has attracted a reasonable
following.

### From the documentation  
> ## Approach
> At its core FauxAPI simply reads the core pfSense config.xml file, converts it to JSON and returns to the API 
> caller. Similarly it can take a JSON formatted configuration and write it to the pfSense config.xml and handles 
> the required reload operations. The ability to programmatically interface with a running pfSense host(s) is enormously 
> useful however it should also be obvious that this provides the API user the ability to create configurations that 
> can break your pfSense system.
>
> FauxAPI provides easy backup and restore API interfaces that by default store configuration backups on all 
> configuration write operations thus it is very easy to roll-back even if the API user manages to deploy a "very 
> broken" configuration.
>
> Multiple sanity checks take place to make sure a user provided JSON config will correctly convert into the (slightly 
> quirky) pfSense XML config.xml format and then reload as expected in the same way. However, because it is not a 
> real per-action application-layer interface it is still possible for the API caller to create configuration changes 
> that make no sense and can potentially disrupt your pfSense system - as the package name states, it is a "Faux" API 
> to pfSense filling a gap in functionality with the current pfSense product.

### Github
 * [github.com/ndejong/pfsense_fauxapi](https://github.com/ndejong/pfsense_fauxapi)
![alt_text](https://img.shields.io/github/forks/ndejong/pfsense_fauxapi.svg?style=social&label=Fork "Github Forks")
![alt_text](https://img.shields.io/github/stars/ndejong/pfsense_fauxapi.svg?style=social&label=Stars "Github Stars")

### Releases
 * [v1.3 announcement](https://www.reddit.com/r/PFSENSE/comments/8vt1zt/fauxapi_v13_released_a_rest_api_interface_for/)
 * [v1.2 announcement](https://www.reddit.com/r/PFSENSE/comments/6wjeyi/fauxapi_a_rest_api_interface_for_pfsense_to/)
 * [v1.1 announcement](https://forum.netgate.com/topic/108433/fauxapi-a-rest-based-api-for-pfsense)

The project is alive and well with an ecosystem of projects appearing around it:-
 * [www.softfire.eu/](https://www.softfire.eu/)
 * [github.com/EpaL/kindercontrol](https://github.com/EpaL/kindercontrol)
 * [community.home-assistant.io/t/pfsense-stat-monitor/61070](https://community.home-assistant.io/t/pfsense-stat-monitor/61070)
 * [github.com/ndejong/pfsense_fauxapi_client_python](https://github.com/ndejong/pfsense_fauxapi_client_python)
 * [github.com/ndejong/pfsense_fauxapi_client_bash](https://github.com/ndejong/pfsense_fauxapi_client_bash)
 * [github.com/Elucidia/faux-api-client](https://github.com/Elucidia/faux-api-client)
 * [npmjs.com/package/pfsense-fauxer](https://www.npmjs.com/package/pfsense-fauxer)
 * [github.com/travisghansen/pfsense_fauxapi_php_client](https://github.com/travisghansen/pfsense_fauxapi_php_client)
 
### Screenshots
**FauxAPI - System Menu**  
![alt text](/img/projects/fauxapi-screenshot-01.png "menu-screenshot")

**FauxAPI - Package Manager**  
![alt text](/img/projects/fauxapi-screenshot-02.png "packages-screenshot")

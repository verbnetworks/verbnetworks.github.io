---
layout: post
title: Arpwitch release v0.2.2
---

v0.2.2 of the arpwitch tool has been released.

Arpwitch is a a modern arpwatch replacement with JSON formatted outputs and easy options to exec commands when 
network changes are observed.

Included is a hard coded convenience `--exec` definition that invokes nmap when new network-addresses are observed 
which nicely demonstrates the usefulness of `arpwitch`.

Legacy versions based on year-date (eg v2018.2) have been hard-deprecated in favour of a backward incompatible 
standard version scheme (eg v0.2.0) and with this major revision change the CLI arguments are quite different to 
previous versions, however they are based on what-works-well in the field.

To get started, install arpwitch using pip and start firing off nmap for each new ip/hw address seen on your network
```bash
pip3 install arpwitch
sudo arpwitch --debug --nmap --datafile /tmp/arpwitch.dat | jq .
```

### Code
 * [github.com/verbnetworks/arpwitch](https://github.com/verbnetworks/arpwitch)

### Python Package
 * [pypi.org/project/arpwitch](https://pypi.org/project/arpwitch/)

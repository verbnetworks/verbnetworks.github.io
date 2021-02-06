---
layout: page
title: Store Forward Networks
subtitle: Message delivery networks based on adhoc peer-node availability
tags: [ mesh-network ]
---

Store-and-forward networks are the original mesh-networks that are well suited to high-latency, uncertain-connectivity 
situations found in extreme remote locations, developing nations and even deep-space communication situations.  

At Verb Networks we've spent a good deal of time working with, examining and experimenting among a wide range of such 
networks, this page captures details of the ones we've learnt from.

Before going further however it's worth describing scope.  There are a wide range of existing tools and protocols that 
happen to work nicely in high-latency, uncertain-connectivity situations that may not typically be associated with the 
lower-level protocol layer implementations that exist or are being developed.  So for the sake of things we define as 
being in-scope we define it as any system that provides a mechanism to deliver a message from node-A to node-Z without
a direct connection existing between node-A and node-Z.

The purpose of opening up the definition so broadly is to discover applications for methods of communication that may 
not be obvious or clear.  For example, a file-sync tool such as [Syncthing](https://syncthing.net) provides an excellent 
mechanism for transporting files (aka messages) from node to node in an opportunistic way, yet the tool was not likely 
designed as a message-delivery framework.  When deployed among nodes with intermittent communications Syncthing does a 
great job of delivering messages (aka files in folders) among all nodes.

This means we are not focused on systems and mechanisms that provide a real-time network socket connection, although 
the in-scope solutions do tend to leverage IP as part of the transport in some manner or another.  It's worth noting 
that much of the more recent systems and tools in this area are more-or-less implementations of a nicely 
defined [named data networking](http://named-data.net/project/archoverview/) concept.

# Motivation
The original motivation and interest in this area came from needing/wanting to provide data-transport telemetry data and 
control signals from to and from mobile plant equipment in very remote locations (think mining).  The lessons learnt in 
this area have led to considering what applications exist in other areas.


## CouchDB with replication
CouchDB with replication is perhaps an odd place to start, certainly it is left field.  This mechanism was a reminder 
at Verb Networks that store-and-forward systems can be very effective indeed.  CouchDB happens to be a very flexible 
key-store database written in Erlang with a data control layer that executes user-defined javascript.  What sets CouchDB
apart from other key-store databses is the very effective data replication engine which can be leveraged to create a
system that receives messages, and stores and forwards them to other nodes until either (a) a delivery-conformation is 
observed (b) message-storage limits are hit or (c) message-storage time to live limits are reached.  CouchDB is well 
suited to the task however there are no standards in this area so it's an exercise for the reader.


## Delay/Disruption Tolerant Networking (DTN)
DTN is a term that came up in the early 2000's when the Interplanetary Internet (IPN) architecture was being developed 
with internet pioneer Vint Cerf.  In 2007 two IETF documents ([RFC4838](https://tools.ietf.org/html/rfc4838) and 
[RFC5050](https://tools.ietf.org/html/rfc5050)) were published describing a shared framework for algorithm and 
application development in DTNs.  DTN standards continue to be actively developed:-
 - [datatracker.ietf.org/wg/dtn/documents/](https://datatracker.ietf.org/wg/dtn/documents/)

Using the same DTN tools and protocols designed for space-communications in terrestrial settings is be a great idea 
becasue you get to leverage all the research/time/energy that has already gone into this area.  However getting a stable 
implementation of these stacks has been tough to until recently with Ubuntu 18.04 now making available the NASA 
implementation of Delay-Tolerant Networking (ION) as a binary apt package to install.

**Ubuntu apt repo packages**
```text
ion - NASA implementation of Delay-Tolerant Networking (DTN)
ion-doc - Interplanetary Overlay Network - examples and documentation
libion-dev - NASA implementation of Delay-Tolerant Networking (DTN) - development files
libion0 - NASA implementation of Delay-Tolerant Networking (DTN) - main libraries
```

Plenty of links and reading material on DTNs:-
 - [www.nasa.gov/content/dtn](https://www.nasa.gov/content/dtn)
 - [en.wikipedia.org/wiki/Delay-tolerant_networking](https://en.wikipedia.org/wiki/Delay-tolerant_networking)
 - [sourceforge.net/projects/ion-dtn/](https://sourceforge.net/projects/ion-dtn/)


## Others

 - [Syncthing](https://syncthing.net/), at Verb Networks we like Syncthing a lot, so much so we even wrote a [Terraform module](https://registry.terraform.io/modules/verbnetworks/strelaysrv-node/digitalocean)
to spin up a Syncthing relay server up in Digital Ocean due to the cheap, low cost traffic available through Digital 
Ocean.  We've also been experimenting with the running of a relay server on [cheap embedded hardware](https://forum.syncthing.net/t/additional-build-target-mips-without-fpu/11739)
attached to wifi-mesh networks using the BMX7 protocol which provides a promising use case in otherwise disconnected 
remote environments - it's a rich area of exploration, and quite a time-sink, if you have an interest or would like to
share experiences we'd be happy to get involved. 

- [BitTorrent Sync](https://www.resilio.com/) was "a thing" before Syncthing, it's something we experimented with for 
more than a year - in our setting with node-A <> node-B <> node-C <> node-D communication we found a high rate of
file conflicts that were difficult to resolve, the experience with Syncthing has been much better in this regard.  Of
note here is that way back in 2013, the BT Sync engineers were already talking about leveraging their platform as a
[message delivery platform](https://www.resilio.com/blog/sync-hacks-secure-messaging-with-bittorrent-sync) 

- [CJDNS](https://github.com/cjdelisle/cjdns) this is another one that we've written a [Terraform module](https://github.com/verbnetworks/terraform-digitalocean-cjdns-node) 
to spin up and experiment with, although the crypto/anarchy/darknet thing that pervades the the main Hyperboria 
network using CJDNS is less than ideal in our view - of note are the IPFS gateway nodes that interconnect with the 
Hyperboria network.


## Others to experiment with
 - [IPFS](https://ipfs.io/) - shows a lot of promise in our view.
 - [DAT](https://datproject.org/) - equally as interesting as IPFS but seems to have stalled in their progress.
 - [Zeronet](https://zeronet.io/) - has a crypto/anarchy/darknet thing going on that they could do without.
 - [Tahoe-LAFS](https://www.tahoe-lafs.org/trac/tahoe-lafs)

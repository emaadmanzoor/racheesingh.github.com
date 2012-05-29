---
layout: post
title: "About CERN VM File System"
description: ""
category: 
tags: [cvmfs, DNS, PowerDNS]
---
{% include JB/setup %}
## What is CERN VM File System?
CERN VM File System is a client server file system developed to deliver software distributions onto virtual machines in a fast, scalable and reliable way. 

## Reliability and Load Balancing in CVMFS
CVMFS can use multiple mirror servers while accessing files from repositories. To configure which mirror servers to use and in which order, the CVMFS_SERVER_URL parameter in /etc/cvmfs/default.local file can be set to a semicolon separated list of mirror servers enclosed in double quotes. From the CVMFS technical report:

"When-ever download of files fails from a server, CernVM-FS automatically switches to the
next mirror server. Additionally, on the first download and after every 1000 down-
loads, CernVM-FS orders the list of servers according to the round trip time for
downloading a file; it then switches automatically to the closest server."

Currently, this helps handle load balancing and reliability.

## Bringing DNS into the Equation
The idea is to help CVMFS clients connect to the mirror server closest to them, allowing lowest latency access to files. When a client attempts to connect to a server, the name resolution process would lead to the authoritative nameserver for CVMFS. This DNS server can be configured such that it replies with the A (address) record of the mirror server closest to the client. After reading up online, I ended up on [this](http://serverfault.com/questions/30567/geo-dns-providers) post. According to the answers, there are 2 possible ways to achieve this:

* __PowerDNS with geobackend__


* __BIND with ACL__

I now require to read about both these implementations and weigh the pros and cons of both.


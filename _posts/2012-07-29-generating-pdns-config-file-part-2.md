---
layout: post
title: "Generating PDNS Config File: Part 2"
description: ""
category: 
tags: [PDNS]
---
{% include JB/setup %}
In this post I will describe recent changes to the Flask webapp. On clicking the `Plot Voronoi` button, it also generates the map file `pdns.config` that maps networks to mirror servers' pseudo IPs.

This is how the generated file looks:

     1.0.0.0/24 :127.0.0.59
     1.0.0.0/22 :127.0.0.24
     1.0.4.0/22 :127.0.0.59
     1.0.8.0/21 :127.0.0.5
     1.0.16.0/20 :127.0.0.24
     1.0.32.0/19 :127.0.0.5
     1.0.64.0/18 :127.0.0.24
     1.0.128.0/17 :127.0.0.5
     1.1.0.0/24 :127.0.0.5
     1.1.1.0/24 :127.0.0.59

# The Issue:
Conversion from a range of IP addresses to the corresponding sub-networks in CIDR notation is time consuming. Out of the 2 Python libraries that do this job well: `netaddr` and `cidrize`, `cidrize` is much faster. Even then, on measuring the time by Python `time` module I found that for each entry in the Whois database, getting its latitude and lognitude and the CIDR networks takes approximately 0.14 seconds. Considering there are 160000 entries in the Whois database, generating the entire config file would take approximately 5 hours.
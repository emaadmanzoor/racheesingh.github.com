---
layout: post
title: "Generating PDNS Config File: Optimization"
description: ""
category: 
tags: [PDNS]
---
{% include JB/setup %}
Taking up the issue stated in the (last)[http://racheesingh.github.com/2012/07/29/generating-pdns-config-file-part-2/] post, in this post I will elaborate on the optimization that reduced the time taken for generating the mapfile from 5 hours to one second approximately. 

## Optimization
* Offline conversion of the Whois CSV file to a SQLite database.
* Offline Pygeoip lookup for IP addresses to get locations of subnets.
* Using a Perl script (taken from rice.net) to get CIDR notation for IP ranges in place of Python libraries like `cidrize`.

These optimizations could be done since the information in the Whois database does not change (unless we sync it to the recent Whois file from the Maxmind folks.). So, the offline conversion to a SQL database etc can be done. 

Here is the precise time taken:
     Time taken to get CIDR info 0.688957929611
This is a huge improvement over the unacceptable 5 hour time before!

All the changes are available on the (updated Github repository)[https://github.com/racheesingh/voronoi-webapp].


---
layout: post
title: "Generating PDNS Config Files: Part1"
description: ""
category: 
tags: [PDNS]
---
{% include JB/setup %}
While setting up PowerDNS with geobackend, there are a few configuration files that need to be supplied. In this post, I will talk about how I am trying to generate the `geo-ip-map-zonefile`. 

## What does the map-zonefile do?
Like the name suggests, this file maps IP addresses to servers. For instance,

     193.109.172.0/22 :127.0.0.1

Here, the IP address `193.109.172.0/22` is mapped to the pseudo IP address of the server. `127.0.0.1` is some server X which is geographically closest to this IP address.

## How to generate the file
Until the last week, I had used the Whois database to get IP addresses of networks and check which networks fall into which Voronoi cells. Now, I am just converting these IPs from the Whois database into the CIDR format and printing a `:127.0.0.X` next to it where X is the serial number assigned to a server.

## Getting the Required Data
I parsed the XML-style formatted file containing information about the mirror servers which are a part of the CERN CDN. I had done this earlier, but all of that had to be changed to get more information for generating the PDNS config files, for instance the Localsite field along with the domain name. The code which does this specifically can be found on [this](https://github.com/racheesingh/preprocess-server-py) repository.

## The Conversion
This is how a typical entry in the Whois database looks:

     "1.0.0.0","1.0.0.255","16777216","16777471","AU","Australia"

There is a `fromIP` = `1.0.0.0` and the 'toIP` is '1.0.0.255`. From this I had to get the network IP in CIDR format so as to write into the map-zonefile. After looking around, I found out about the [netaddr](http://packages.python.org/netaddr/tutorial_01.html) library which does the conversion from IP range to CIDR format IP addresses. Like:

      >>> import netaddr
      >>> start_ip = "1.0.0.0"
      >>> end_ip = "1.0.0.255"
      >>> ip_range = list( netaddr.iter_iprange( start_ip, end_ip ) )
      >>> netaddr.cidr_merge( ip_range )
      [IPNetwork('1.0.0.0/24')]


I tried `cidr_merge` and found that this library is quite slow. So, it was not practical to use it for a million conversions. 
An alternative to netaddr suggested on StackOverflow was the the [cidrize](http://pypi.python.org/pypi/cidrize/0.6.3) library. It is much faster as compared to netaddr. Here is how it works:

      >>> from cidrize import cidrize
      >>> fromIP = "1.0.0.0"
      >>> toIP = "1.0.0.255"
      >>> ip_range = fromIP 
      >>> ip_range = fromIP + "-" + toIP
      >>> cidrize( ip_range )
      [IPNetwork('1.0.0.0/24')]

Using this I have tried to generate the map-zonefile. For 160000 or so entries even this library takes quite a lot of time.

Here are the first few lines from the generated file:

     1.0.0.0/24 :127.0.0.59
     1.0.0.0/22 :127.0.0.25
     1.0.4.0/22 :127.0.0.59
     1.0.8.0/21 :127.0.0.5
     1.0.16.0/20 :127.0.0.25


# Sidebar
---------

## Bringing Together Data Pre-processing and The Computation
Until now, I was using many separate scripts to process the server names then get their location from GeoIP database and writing their outputs to files. These intermediate files were causing trouble. So, in place of writing the data into flat files, I am just building a dictionary of the data and passing it to the main method of the script that does all the computation. Further details and code are in this repo!
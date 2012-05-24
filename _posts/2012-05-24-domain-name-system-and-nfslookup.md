---
layout: post
title: "Domain Name System and nfslookup"
description: ""
category: 
tags: [DNS, nfslookup, nameserver]
---
{% include JB/setup %}
## Domain Name System (DNS)
DNS is a distributed database containing names and addresses of all reachable hosts on the Internet. While attempting to connect to a domain name (for instance: `www.google.com`), a host first checks its `hosts` file (for instance: `/etc/hosts`) for an entry corresponding to the domain name. If this entry is not in the `hosts` file, the host sends a query to its primary DNS name server. If the primary name server does not have the appropriate record, it forwards the query to a server higher in the domain name hierarchy [1].

The IP address of the primary DNS server (or the ISP's DNS server) is stored on your machine in the `/etc/resolv.conf` file. Here's how my `resolv.conf` looks:

	nameserver 121.242.190.210
	nameserver 4.2.2.3

In case your ISP's nameserver does no do quick name resolution, then you might want to use an alternate nameserver. OpenDNS is one option. You can put their nameserver's IP address in the `resolv.conf` file like:

	nameserver <opendns nameserver IP>

The DNS contains records containing the following values:

* Start of authority: authoritative name server for a given domain.
* A: Address records (IP addresses for domain names)
* CNAME: Canonical Name records provide host name aliases (alternate host names).
* PTR: Pointer records associate a host name with a given IP address (reverse of what A records do).
* MX: Mail Exchange records define the mail system for a domain.
* NS: Name server records define name servers for a given domain.

`nslookup` is a command line utility that can be used for looking at DNS records. To obtain the utility on Arch Linux, install the package `dnsutils`.

	$ pacman -S dnsutils

## Using nfslookup
From all the records that are stored by the DNS database, the `ping` command only looks at A records. The `nslookup` command looks at all the other records such as CNAME, MX etc.

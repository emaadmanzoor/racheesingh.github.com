---
layout: post
title: "Domain Name System and nslookup"
description: ""
category: 
tags: [DNS, nslookup, nameserver]
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

* __Start of authority__: authoritative name server for a given domain.
* __A__: Address records (IP addresses for domain names)
* __CNAME__: Canonical Name records provide host name aliases (alternate host names).
* __PTR__: Pointer records associate a host name with a given IP address (reverse of what A records do).
* __MX__: Mail Exchange records define the mail system for a domain.
* __NS__: Name server records define name servers for a given domain.

`nslookup` is a command line utility that can be used for looking at DNS records. To obtain the utility on Arch Linux, install the package `dnsutils`.

	$ pacman -S dnsutils

## Using nslookup
`nslookup` stands for name server lookup. It uses the entry corresponding to the local DNS nameserver present in `/etc/resolv.conf`. `nslookup` then queries the local DNS nameserver for the IP address of a certain hostname. Whereas the `ping` command only looks at A records stored by nameservers, the `nslookup` command looks at all the other records such as CNAME, MX etc. For all these records, specific command line options are available. For complete information, try `man nslookup`.

Here is a simple example use:

	[rachee@rachee ~]$ nslookup www.google.com
	Server:		121.242.190.210
	Address:	121.242.190.210#53

	Non-authoritative answer:
	www.google.com	canonical name = www.l.google.com.
	Name:	www.l.google.com
	Address: 74.125.236.51
	Name:	www.l.google.com
	Address: 74.125.236.49
	Name:	www.l.google.com
	Address: 74.125.236.52
	Name:	www.l.google.com
	Address: 74.125.236.48
	Name:	www.l.google.com
	Address: 74.125.236.50

The output depicts a couple of things, lets over them piece by piece:

* This part of the reply,
		Server:		121.242.190.210
		Address:	121.242.190.210#53

means that the DNS nameserver that is handling our query is `121.242.190.210`. No surprises here, this was just picked from the `/etc/resolv.conf` file!

* 'Non-authoritative answer' means that the DNS nameserver that returned the answer to the query 'Address of www.google.com' is not authoritative for the www.google.com zone. In effect, my local DNS nameserver issued a series of queries to different nameservers to obtain a response and returned the address to me.

* 'canonical name = www.l.google.com' implies that `www.google.com` is just a canonical name for `www.l.google.com`. In the process of name resolution, the nameserver authoritative for the `google.com` zone must have told my local DNS nameserver that `www.google.com` is a CNAME record for `www.l.google.com`. After receiving this answer, my local nameserver would query the `google.com` nameserver instead for the address of `www.l.google.com`. 

* The rest of the reply contains all A records corresponding to `www.l.google.com`.



---
layout: post
title: "Buckets of Networks"
description: ""
category: 
tags: [matplotlib, bar charts, Voronoi Diagram]
---
{% include JB/setup %}
This is in continuation with the previous post: [Data Visualization: Part 3](http://racheesingh.github.com/2012/06/14/data-visualization-part-3/). In the Python application that generates Voronoi polygons for the server locations, I needed to find how many networks in the world lie in which Voronoi cell. So here's what I did:

## GeoIP Whois Database:
From the GeoIP Whois database, I read the IP addresses of networks (This is a huge file, of about 160000 entries!). Using their Python API (`pygeoip`) I got the latitudes and longitudes of all the IPs. Now, I had to check for each coordinate, which Voronoi cell contains it, geographically. Thanks to matplotlib's in-built method for checking if a point lies with a polygon, I only had to loop through all coordinates and Voronoi cells (there are about 67 unique ones) to get a dictionary of the form:

     dict = { serialNo: <Number of networks in this cell> }

## Minor Issues:
On checking the counts of the number of Voronoi cells I get and the original number of server sites, I realized that there was a difference between the two. I read the original list of servers which are a part of CERN's CDN from a configuration file and then I used Maxmind's GeoIP database to get their coordinates. Since this database gives information as to which country the IP belongs to, some servers have overlapping coordinates. So, while there were 105 servers initially, there remained 67 servers with unique coordinates. This is why, the method which is generating Voronoi polygons returns 67 polygons. 
To clear a little bit of the mess, I wrote a method which takes in the original list of servers and merges the entries which have the same coordinates, keeping track of which servers correspond to the merged entries.

## Buckets of Networks
Using the dictionary that keeps count of how many networks fall into each Voronoi cell, I plotted a bar chart to depict how the networks are distributed and the load on each server.
Here is how it looks:
<img src="https://github.com/racheesingh/voronoi-map-py/raw/master/bar-chart.png" title="Buckets of Networks" align="left" width="100%"/>

## Maximum load on which server?
I also checked the size of each bucket to find the server which had maximum networks allocated to it.

  The most loaded server: http://frontiercache.esc.qmul.ac.uk at index 7

## The Code
The latest code for this application is [here](https://github.com/racheesingh/voronoi-map-py).
 
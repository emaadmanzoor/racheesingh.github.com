---
layout: post
title: "Visualizing Data: Part 2"
description: ""
category: 
tags: [d3.js, Maps, Visualization, Voronoi Diagrams]
---
{% include JB/setup %}
This post is in continuation to the [Visualizing Data: Part 1] (http://racheesingh.github.com/2012/06/09/visualizing-data-part-1/) post. That post was about plotting the locations of servers on a world map (using JavaScript and the third part library [d3.js](http://d3js.org)). In this post, I will use d3.js's built-in functions to plot the Voronoi diagrams, dividing the map into regions/cells. 

## What are Voronoi Diagrams?
Given a set of `n` points (or sites), a Voronoi Tessellation is a subdivision of the space into `n` cells (polygons), each cell corresponding to one site. These cells have the property that a point q lies in the cell corresponding to a site pi iff d(pi, q) < d(pj, q) for i distinct from j. The segments in a Voronoi Tessellation correspond to all points in the plane equidistant to the two nearest sites. Read more about them [here](http://en.wikipedia.org/wiki/Voronoi_diagram).

## Computing the Voronoi Polygons
There are various algorithms to construct Voronoi diagrams, the most common being [Fortune' Algorithm](http://en.wikipedia.org/wiki/Fortune%27s_algorithm). Fortune's Algorithm uses O(nlogn) time.

In this example, I have utilized an inbuilt method: `d3.geom.voronoi` to compute the vertices of the polygons in the Voronoi diagram.

## The Motivation
The clients of CVMFS (CERN Virtual Machine File System) would like to connect to mirror servers that are closer to them so as to reduce the latency in communication. To make decisions regarding which server is closest to a particular client, we are using Voronoi diagrams. So, if a client belongs to a cell C in the Voronoi diagram, it should be served by the server S corresponding to the cell C.

This is an effort to visualize the approximate partition of space.

## The Plot
So, here's how the visualization looks:

<img src="https://github.com/racheesingh/racheesingh.github.com/raw/master/_posts/voronoi-1.png" title="Voronoi Diagram" align="left" width="100%"/>

A zoomed-in view of the part where most sites are clustered:

<img src="https://github.com/racheesingh/racheesingh.github.com/raw/master/_posts/voronoi-zoom.png" title="Closeup of Voronoi diagram" align="left" width="100%"/>


## The code
The complete code for this plot along with the libraries (d3.js) are available on [this](https://github.com/racheesingh/voronoi-world-map) Github repository.

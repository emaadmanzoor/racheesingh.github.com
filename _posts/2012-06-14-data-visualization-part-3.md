---
layout: post
title: "Data Visualization: Part 3"
description: ""
category: 
tags: [matplotlib, Visualization, Basemap, Voronoi diagram]
---
{% include JB/setup %}
## Visualization for Offline Purposes
While the JavaScript visualization described in [Data Visualization: Part 2](http://racheesingh.github.com/2012/06/10/visualizing-data-part-2/) works within the browser, there is a need for building an application that allows manipulation of the mirror server data along with visualizing it. So, in this post, I will describe the construction of Voronoi diagrams in Python.

## Libraries and Credits
I made use of matplotlib toolkits's Basemap for the background world map. This was really nice to use, with a whole bunch of projections available for plotting the map. I also found a great library called [py_geo_voronoi] (https://github.com/Softbass/py_geo_voronoi) that aids plotting Voronoi diagrams on map-sized plots. Utilizing one of this library's functions, I obtained the `Polygon` objects corresponding to each of the polygon in the Voronoi diagram. Then, I processed these polygons to get coordinates corresponding to the world map I had prepared. Polygon by polygon, I plotted them on the map.

## What's in the Code?
The code for bringing this data on a world map and constructing Voronoi polygons is surprisingly small with the easy to use libraries! The full code along with the included libraries can be found [here]. Download the directory and run:

	$ python2 server_locations.py < geolist_locations

## The Plot
Here is how the Voronoi diagram on a Basemap looks:
<img src="https://github.com/racheesingh/racheesingh.github.com/raw/master/_posts/plot.png" title="Voronoi diagram" align="left" width="100%"/>
<img src="https://github.com/racheesingh/racheesingh.github.com/raw/master/_posts/plot-large.png" title="Voronoi diagram" align="left" width="100%"/>

## A "Closer" Look:
A closer look at the more cluttered parts of the map, here's US's zoomed-in view:
<img src="https://github.com/racheesingh/racheesingh.github.com/raw/master/_posts/zoomin1.png" title="Voronoi diagram Zoom" align="left" width="100%"/>

And the rest:
<img src="https://github.com/racheesingh/racheesingh.github.com/raw/master/_posts/zoomin2.png" title="Voronoi diagram Zoom" align="left" width="100%"/>



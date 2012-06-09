---
layout: post
title: "Visualizing Data: Part 1"
description: ""
category: 
tags: [d3.js, maps, visualization]
---
{% include JB/setup %}
In this post, I am trying to visualize some data on a map to get a fair idea of how things are distributed. 

## What is this data?
I am trying to visualize the location of servers which are a part of CERNVM's Content Distribution Network (CDN). In Part 2 of this post, I will also construct voronoi polygons considering each of these server locations a site in the diagram. 
I have a JSON file that contains data in this format:

		server-name: 
		location: {
			x:
			y:	
		}

(x,y) represents the latitude and longitude of the server's locations. These are approximate values. 
[Sidebar: There was also some pre-processing that had to be done to get this data, I will describe that process in another post!]

## Raw Materials
I am using JavaScript along with the d3.js library. Since I am really new to JavaScript, it has taken me a while to understand how it works. I haven't quite got the tricks of the language yet, but I can comprehend bits and pieces of JavaScript code now.

## Lets Visualize
So, here it is, the visualization:
<img src="https://github.com/racheesingh/racheesingh.github.com/raw/master/_posts/servers_plot.png" title="The Plot of Server Locations" align="center" />


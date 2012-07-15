---
layout: post
title: "Flask Web Application"
description: ""
category: 
tags: [Flask, Webapp, sqlite3, voronoi]
---
{% include JB/setup %}
In this post, I will describe the Web application I had setup. This application basically uses a Sqlite3 database to store the information of all the CVMFS servers. It shows the list of servers currently in database. If the user is logged in, he/she can add to the list of servers. They only need to add the name of the server and the URL. Then the application performs a GeoIP look-up and adds the server's latitude and longitude to the database. 

There is a method called `init_db` which reads the input file containing the servers names and locations. It populates the database with the contents of this file. New entries are added to the database in the `add_entry` method. 

## The Screenshots
Here is the main page, showing a form to add new servers. It also lists the servers currently existing in the database:

<img src="https://github.com/racheesingh/racheesingh.github.com/raw/master/_posts/webapp1.png" title="Web Application1">

After scrolling down on the main page, there is a button called `Plot Voronoi`. Clicking on this redirects to `http://127.0.0.1:5000/voronoi`. On this URL the Voronoi diagram is displayed. 
<img src="https://github.com/racheesingh/racheesingh.github.com/raw/master/_posts/webapp2.png" title="Web Application2">

On clicking the `Plot Voronoi` button, the plot is displayed on `/voronoi`:

<img src="https://github.com/racheesingh/racheesingh.github.com/raw/master/_posts/webapp3.png" title="Web Application3">

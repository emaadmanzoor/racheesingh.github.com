---
layout: post
title: "Removing a Mirror Server from the Database"
description: ""
category: 
tags: []
---
{% include JB/setup %}
From where I left last week, I added checkboxes for every entry (mirror server) and made all of them submit to the `/delete` URL when the `Delete Selected` button is clicked. Then, in the `delete` method, I checked the entries for which the checkbox was checked and deleted them from the database.

Here is how it looks:

<img src="https://github.com/racheesingh/racheesingh.github.com/raw/master/_posts/delete-webapp.png" title="Web Application" align="left" width="100%"/>


<img src="https://github.com/racheesingh/racheesingh.github.com/raw/master/_posts/delete-webapp2.png" title="Web Application" align="left" width="100%"/>

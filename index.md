---
layout: page
title: Rachee Singh
tagline: A Computer Science Undergraduate Student.
---
{% include JB/setup %}

This blog is made using Jekyll Bootstrap and Github Pages. Complete usage and documentation available at: [Jekyll Bootstrap](http://jekyllbootstrap.com)

## About Me

I am a computer science undergraduate from [BITS Pilani Goa Campus, India](http://universe.bits-pilani.ac.in/Goa/). I am interested in Computer Networks, Distributed Computing and Machine Learning. This blog concerns my attempts at scratching the surface of these interesting fields. For more details about me, check [this](http://racheesingh.github.com/about.html) page!

## Posts

Here is a list of all my posts, the list is still quite small!

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>


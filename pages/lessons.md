---
layout: page
title: Lessons
description: My current teaching with advanced lessons focusing on depth, writing and serious discussion
permalink: /lessons/
og-type: website
---

I run small groups of three to five people that focus on advanced English for professionals.  

[Contact me][0] if you're interested in either joining a group or starting a new one. 

## How it Works
 
 - A group selects a topic and works through the materials. 
 - They make comments, write questions and add responses in a shared document. 
 - Other people in the group and I respond. Writing and peer to peer communication are essential for making these groups successful. 
 - We meet for about two hours to discuss the topic and go over feedback that I have from the shared document. 

Each iteration can take a couple of weeks to a month depending on the amount of reading and listening the topic has. 

<h2 id="topics" class="centered-element">Topics</h2> 

{% for lesson in site.lessons reversed  %}
  {%include lesson-listing.html %}
{% endfor %}

[0]: /contact
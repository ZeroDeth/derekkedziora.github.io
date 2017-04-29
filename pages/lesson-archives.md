---
layout: blank
title: Lesson Archives
og-type: website
permalink: /lesson-archives/
---

# Lesson Archives

These are forty lessons I created in 2016 to serve as discussion topics for small groups and individual lessons. 

{% for lesson-archive in site.lesson-archives reversed  %}
  {%include lesson-archive-listing.html %}
{% endfor %}

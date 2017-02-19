---
title: Linking to a Random Post on a Jekyll Blog
description: Here's how I finally figured out how to create a link to a random post on my Jekyll blog
tags:
 - jekyll
 - programming
categories:
 - tech   
---
I love using [Jekyll][0] for my blog, because a static site generator gives me more or less everything I need without the horror stories and black boxes of databases and PHP. The coding is simple enough that I can take care of pretty much anything myself. One of the problems of static site generators is that fun features like linking to a random post are much harder to implement.

When searching around, I could only find two solutions and neither of them would work in my case. The first is using a plugin. Unfortunately, this isn't an option since I host my site via GitHub Pages. The other choice was to generate a new random link on each site build, which is kind of lame since my site is built no more than once a week or so.   

A little tinkering with Javascript and [Liquid][1], Jekyll's template language, brought about the result that I wanted - a new random link each time somebody visits the site without a plugin.

The solution is straightforward: get all the post URLs into a Javascript array, use Javascript to generate a (pseudo)random number bounded by the number of items in the array and you have the URL to a random post.

To use this in Jekyll, create a new file in your `_includes` folder.

Copy the first section of code into the file to generate the array ([view on GitHub][2]) and add the second code snippet where you'd like a link to a random post to appear ([view on GitHub][3]).

```

{% raw %}{% assign counter_rand = 0 %}
{% assign array_urls = "" %}

{% for post in site.posts %}
  {% unless post.url == page.url %}
    {% assign counter_rand = counter_rand | plus: 1 %}
    {% assign array_urls = array_urls | append: post.url %}
    {% assign array_urls = array_urls | append: "," %}
  {% endunless %}
{% endfor %}

{% assign array_urls = array_urls | split: "," %}
{% assign array_urls = array_urls | append: ""]" %}
{% assign array_urls = array_urls | join: '", "' %}{% endraw %}

<script>
  var myArray = {% raw %}{{ array_urls }}{% endraw %};
  var randnum = Math.floor(Math.random()
   * {% raw %}{{ counter_rand }}){% endraw %} + 0;
  var linkToPost = myArray[randnum]
  document.getElementById("randoLink").href = linkToPost
</script>

```

```

<a id="randoLink" href"">visit a random post</a>
{% raw %}{% include (name-of-your-file).html %}{% endraw %}

```

Unfortunately, this doesn't work in markdown; it can only be added to HTML files.

[0]: http://jekyllrb.com
[1]: https://shopify.github.io/liquid/
[2]: https://github.com/derekkedziora/derekkedziora.github.io/blob/master/_includes/random-post.html
[3]: https://github.com/derekkedziora/derekkedziora.github.io/blob/master/_includes/next-previous-links.html

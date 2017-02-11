---
title: A Random Post on Jekyll, a Static Site Generator
description: Here's how I finally figured out how to create a link to a random post on my Jekyll blog 
tags: 
 - jekyll
 - programming 
categories:
 - tech   
---
I love using <a href="http://jekyllrb.com" target="_blank">Jekyll</a> for my blog, because a static site generator gives me more or less everything I need without the horror stories of databases and PHP. The coding is simple enough that I can take care of pretty much anything myself.

One of the problems of static site generators is that fun features like linking to a random post are much harder to implement. A little tinkering with Javascript and <a href="https://shopify.github.io/liquid/" target="_blank">Liquid</a> (Jekyll's templating language), brought the result that I wanted. 

The solution is straightforward: get all the post URLs into a Javascript array, use Javascript to generate a (pseudo)random number bounded by the number of items in the array and you have the URL to a random post.

The code is on <a href="https://github.com/derekkedziora/derekkedziora.github.io/blob/master/_includes/random-post.html" target="_blank">GitHub</a>. 

To use this in Jekyll, copy the code into a new file in your _includes folder. 

Add the following code snippet where you'd like a link to a random post:

> <a id="randoLink" href"">visit a random post</a>  
> {% raw %}{% include (name-of-your-file).html %}{% endraw %}

Unfortunately, this doesn't work in markdown; it can only be added to HTML files. 

Of course, this doesn't seem like much to a professional programmer, but for a hobby programmer it's fun to actually make my own solution to a problem that couldn't be solved through searching the internet. 








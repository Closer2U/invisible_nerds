---
layout: category_index
title: Tags
permalink: /tags/
category_name: tags
---

This page displays the site's tags in alphabetical order and shows how many posts there are per tag, makes anchor links for each tag, then outputs posts by tag in reverse chronological order. 

### Posts by tag

{% assign sorted_tags = (site.tags | sort:0) %}
<ul class="tag-box">
	{% for tag in sorted_tags %}
		{% assign t = tag | first %}
		{% assign posts = tag | last %}
		<li><a href="#{{ t | downcase }}">{{ t }} <span class="size">({{ posts.size }})</span></a></li>
	{% endfor %}
</ul>

{% for tag in sorted_tags %}
  {% assign t = tag | first %}
  {% assign posts = tag | last %}

<h4 id="{{ t | downcase }}">{{ t }}</h4>
<ul>
{% for post in posts %}
  {% if post.tags contains t %}
    <li>
       <span class="date">{{ post.date | date: '%d %b %y' }}</span>:  <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endif %}
{% endfor %}
</ul>
{% endfor %}

<!-- Listing posts by tag template from http://github.com/cagrimmett/jekyll-tools -->
<!--

Set the front matter:
title = your page title and link name in the navigation
permalink = the url for the page, i.e. example.com/my-awesome-category
category_name = the name of the cateogry you want to use to group posts, you'll need to use the same name on post pages

Save this page in the root directory.
Use the same name for the filename as the permalink, i.e.

permalink: /my-awesome-category/
filename: my-awesome-category.html

-->


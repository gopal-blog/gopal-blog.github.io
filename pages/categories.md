---
layout: categories
title: Categories
description: categories template
keywords: Classification
comments: false
menu: Classification
permalink: /categories/
---

<section class="container posts-content">
{% assign sorted_categories = site.categories | sort %}
{% for category in sorted_categories %}
<h3>{{ category | first }}</h3>
<ol class="posts-list" id="{{ category[0] }}">
{% for post in category.last %}
<li class="posts-list-item">
<span class="posts-list-meta">{{ post.date | date_to_string }}/</span>
<a class="posts-list-name" href="{{ site.url }}{{ post.url }}">{{ post.title }}</a>
</li>
{% endfor %}
</ol>
{% endfor %}
</section>
<!-- /section.content -->

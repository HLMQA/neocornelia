---
published: true
layout: filter-page
date: '2020-01-02 19:19:20 +0100'
categories: post event
title: Notes
subtitle: 
hero_image: /neocornelia/images/Banner_trimmed.jpg
---

{% assign filtered-posts = site.posts | where:"categories", "note" %}

{% for post in filtered-posts %}

{% assign next-post = filtered-posts[forloop.index] %}
{% capture year %}{{ post.date | date: '%Y' }}{% endcapture %}
{% capture nyear %}{{ next-post.date | date: '%Y' }}{% endcapture %}

{% include note-item.html content=post %}

{% if year != nyear and next-post.date %}
<header class="timeline-header">
    <span class="tag is-primary" style="font-size: 0.90rem;" >{{ post.date | date: '%Y' }}</span>
</header>
{% endif %}
{% endfor %}
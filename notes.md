---
published: true
layout: page
date: '2020-01-02 19:19:20 +0100'
categories: post event
title: Notes
subtitle: Announcements, trips, and news from the team behind Cornelia.
---

<html>
<head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>Cornelia</title>
    <link rel="stylesheet" href="{{ "/assets/css/timeline.css" | relative_url }}">
    <script defer src="https://use.fontawesome.com/releases/v5.3.1/js/all.js"></script>
</head>
<body>

<section class="section">
    <div class="container">
        <div class="columns">
            <div class="column is-8-desktop is-offset-2-desktop">
                <div class="timeline">
                    {% for post in site.posts %}
                      {% capture year %}{{ post.date | date: '%Y' }}{% endcapture %}
                      {% capture nyear %}{{ post.next.date | date: '%Y' }}{% endcapture %}
                      {% if year != nyear %}
                        <header class="timeline-header">
                          <span class="tag is-primary" style="font-size: 0.90rem;" >{{ post.date | date: '%Y' }}</span>
                        </header>
                      {% endif %}
                      {% capture category %}{{ post.categories.first }}{% endcapture %}
                      {% assign content = post.content | strip_newlines %}



                      {% if category == "note" %}
                      <div class="timeline-item is-primary">

                          <div class="timeline-marker is-primary"></div>
                          <div class="timeline-content">
                                <p class="heading">{{ category }}</p>
                                {% if content == "" %}
                 
                                    {% if post.link %}
                                        <p><i><a href="{{ post.link }}">{{ post.title }}</a></i>
                                        <i class="fas fa-external-link-square-alt" aria-hidden="true"></i></p>
                                    {% else %}

                                    <p>{{ post.title }}</p>

                                    {% endif %}
                          
                                {% else %}   
                                    <p><a href="{{ post.url | prepend: site.baseurl | prepend: site.url }}">{{ post.title }}</a></p> 

                                    
                                {% endif %}         
                          </div>
                      </div>
                      {% endif %}


                    {% endfor %}
                    <header class="timeline-header">
                        <span class="tag is-primary" style="font-size: 0.90rem;">Project starts</span>
                    </header>
                </div>
            </div>
        </div>
    </div>
</section>


</body>
</html>

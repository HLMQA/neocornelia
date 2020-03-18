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
                          <span class="tag is-primary">{{ post.date | date: '%Y' }}</span>
                        </header>
                      {% endif %}
                      {% capture category %}{{ post.categories.first }}{% endcapture %}
                    {% unless category contains "note" or category contains "news" %}
                        {% continue %}
                    {% endunless %}
                      {% if category == "publication" %}
                      <div class="timeline-item is-danger">
                        <div class="timeline-marker is-danger is-icon">
                          <i class="fa fa-bookmark"></i>
                        </div>
                        <div class="timeline-content">
                          <p class="heading">{{ category }}</p>
                          {{ post.authors }} <strong>‘{{post.title}}’</strong>. {{ post.journal }}</p>
                        </div>
                      </div>
                      {% else %}
                      <div class="timeline-item is-primary">
                          <div class="timeline-marker is-primary"></div>
                          <div class="timeline-content">
                            <p class="heading">{{ category }}</p>
                            {% if category contains "post" or category contains "note" %}
                            <p>{{ post.title }}</p>
                            {% else %}
                            <p><a href="{{ post.url | prepend: site.baseurl | prepend: site.url }}">{{ post.title }}</a></p>
                            {% endif %}
                          </div>
                      </div>
                      {% endif %}
                    {% endfor %}
                    <header class="timeline-header">
                        <span class="tag is-primary">Project starts</span>
                    </header>
                </div>
            </div>
        </div>
    </div>
</section>

</body>
</html>
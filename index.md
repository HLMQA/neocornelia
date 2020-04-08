---
# You don't need to edit this file, it's empty on purpose.
# Edit theme's home layout instead if you wanna make some changes
# See: https://jekyllrb.com/docs/themes/#overriding-theme-defaults
layout: home
---

{% for post in site.posts %}
{% capture year %}{{ post.date | date: '%Y' }}{% endcapture %}
{% capture nyear %}{{ post.next.date | date: '%Y' }}{% endcapture %}
{% if year != nyear and post.next %}
<header class="timeline-header">
    <span class="tag is-primary" style="font-size: 0.90rem;" >{{ post.date | date: '%Y' }}</span>
</header>
{% endif %}
{% capture category %}{{ post.categories.first }}{% endcapture %}
{% assign content = post.content | strip_newlines %}
<!-- Define knot style and title formatting for publications -->
{% if category == "publication" %}
{% include publication-item.html content=post %}

<!-- Define knot style and title formatting for infrastructure -->

{% elsif category contains "infrastructure" %}
{% include infrastructure-item.html content=post %}



<!-- Define knot style and title formatting for presentations -->

{% elsif category contains "presentation" %}
{% include presentation-item.html content=post %}



<!-- Define knot style and title formatting for other types of post (essentially news and notes) -->

{% else %}
{% include note-item.html content=post %}

{% endif %}
{% endfor %}
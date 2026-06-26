---
layout: page
title: Notes
description: "Technical notes and short essays."
permalink: /notes/
---

{% if site.posts.size > 0 %}
<div class="post-list">
  {% for post in site.posts %}
  <article class="post-preview">
    <time datetime="{{ post.date | date: '%Y-%m-%d' }}">{{ post.date | date: "%B %-d, %Y" }}</time>
    <h2><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h2>
    {% if post.excerpt %}
      <p>{{ post.excerpt | strip_html | truncate: 220 }}</p>
    {% endif %}
  </article>
  {% endfor %}
</div>
{% else %}
Notes will appear here when posts are added.
{% endif %}


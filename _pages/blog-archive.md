---
layout: posts
permalink: /blog/
excerpt: "Lars Olesens blog."
title: Lars Olesens Blog
seo_title: "Lars Olesens blog"
classes: wide
author_profile: true
blog:
  - excerpt: '[Se blogindlæg efter kategori](/tags/){: .btn .btn--large .btn--success }'
---

<h2>Seneste opdateringer på bloggen</h2>

<div class="feature__wrapper">

{% assign site_posts = site.posts | sort: "last_modified_at" | reverse %}

{% if site_posts.size > 0 %}
  {% for post in site_posts limit:16 %}
    {% include archive-single.html type="grid" %}
  {% endfor %}
{% endif %}

</div>

{% include feature_row id="blog" type="center" %}

---
layout: splash
permalink: /rejser/
title: Mine rejser
description: Vi maler med lys
excerpt: 'Vi maler med lys'
header:
  overlay_color: "#5e616c"
  overlay_image: /assets/images/picture-1.png
author_profile: true
#intro:
#  - excerpt: 'Tilmeld dig den historiske gruppe &nbsp; [<i class="fab fa-facebook-f"></i> VIH Historiske Gruppe](https://www.facebook.com/groups/655406751295188/){: .btn .btn--facebook}'
---

Vi maler med lys. Vil du være med til at male med lys?

<div class="feature__wrapper">

{% assign site_posts = site.posts | where: "categories", "Rejser" | sort: "last_modified_at" | reverse %}

{% if site_posts.size > 0 %}
  {% for post in site_posts limit:8 %}
    {% include archive-single.html type="grid" %}
  {% endfor %}
{% endif %}

</div>

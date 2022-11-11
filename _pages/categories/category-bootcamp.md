---
title: "Bootcamp"
layout: archive
permalink: categories/bootcamp
author_profile: true
sidebar_main: true
---

{% assign posts = site.categories.bootcamp %}
{% for post in posts %} 
    {% include archive-single2.html type=page.entries_layout %} 
{% endfor %}
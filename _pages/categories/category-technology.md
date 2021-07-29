---
title: "Technology"
layout: archive
permalink: categories/technology
author_profile: true
sidebar_main: true
---

{% assign posts = site.categories.technology %}
{% for post in posts %} 
    {% include archive-single2.html type=page.entries_layout %} 
{% endfor %}
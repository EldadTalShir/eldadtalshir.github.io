---
title: "Sitemap"
layout: archive
permalink: /sitemap/
author_profile: true
---

{% include base_path %}

A list of the main pages on the site. For you robots out there, there is an [XML version](/sitemap.xml) available for digesting as well.

{% assign allowed = "/about/,/research/,/cv/" | split: "," %}
{% assign items = site.pages | concat: site.documents %}
{% for item in items %}
  {% assign keep = false %}
  {% for prefix in allowed %}
    {% assign plen = prefix | size %}
    {% assign head = item.url | slice: 0, plen %}
    {% if head == prefix %}{% assign keep = true %}{% endif %}
  {% endfor %}
  {% if keep %}
    {% assign post = item %}
    {% include archive-single.html %}
  {% endif %}
{% endfor %}

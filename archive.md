---
layout: page
title: "Archive"
permalink: archive
---

# Blog Archive

{% assign posts_by_year = site.posts | group_by_exp:"post", "post.date | date: '%Y'" %}
{% for year in posts_by_year %}
  <h2>{{ year.name }}</h2>
  <ul class="archive-list">
    {% assign posts_by_month = year.items | group_by_exp:"post", "post.date | date: '%B %Y'" %}
    {% for month in posts_by_month %}
      <li class="archive-month">{{ month.name }}</li>
      <ul class="archive-posts">
        {% for post in month.items %}
          <li><a href="{{ post.url }}">{{ post.title }}</a></li>
        {% endfor %}
      </ul>
    {% endfor %}
  </ul>
{% endfor %}
{% comment %}
  <h2>Archive</h2>
  <ul class="archive-list">
    {% for post in site.posts %}
      <li><a href="{{ post.url }}">{{ post.title }}</a></li>
    {% endfor %}
  </ul>
{% endcomment %}
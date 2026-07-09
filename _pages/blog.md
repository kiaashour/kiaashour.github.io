---
layout: default
permalink: /blog/
title: Writings
nav: true
nav_order: 1
description: Research notes and articles by Kia Ashouritaklimi
---

<div class="post">
  <div class="header-bar">
    <h1>{{ site.blog_name }}</h1>
    {% if site.blog_description %}<h2>{{ site.blog_description }}</h2>{% endif %}
  </div>

  {% assign paper_posts = site.posts | where: "paper_entry", true %}
  <ul class="post-list">
    {% for post in paper_posts %}
      <li>
        <h3>
          {% if post.redirect == blank %}
            <a class="post-title" href="{{ post.url | relative_url }}">{{ post.title }}</a>
          {% elsif post.redirect contains '://' %}
            <a class="post-title" href="{{ post.redirect }}" target="_blank">{{ post.title }}</a>
          {% else %}
            <a class="post-title" href="{{ post.redirect | relative_url }}">{{ post.title }}</a>
          {% endif %}
        </h3>
        <p class="post-meta">{{ post.date | date: '%B %-d, %Y' }}</p>
        {% if post.description %}<p>{{ post.description }}</p>{% endif %}
      </li>
    {% else %}
      <li>No posts yet.</li>
    {% endfor %}
  </ul>
</div>

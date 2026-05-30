---
layout: default
permalink: /talks/
title: talks
nav: true
nav_order: 2
---

<div class="post">

  <div class="header-bar">
    <h1>Talks & Musings</h1>
    <h2>A more casual corner — talk slides, notes, and half-formed thoughts.</h2>
  </div>

  <ul class="post-list">

    {% assign talks = site.talks | sort: "date" | reverse %}
    {% for talk in talks %}

    {% assign read_time = talk.content | number_of_words | divided_by: 180 | plus: 1 %}
    {% assign year = talk.date | date: "%Y" %}
    {% assign tags = talk.tags | join: "" %}

    <li>

{% if talk.thumbnail %}

<div class="row">
        <div class="col-sm-9">
{% endif %}
      <h3>
        {% if talk.redirect == blank %}
          <a class="post-title" href="{{ talk.url | relative_url }}">{{ talk.title }}</a>
        {% elsif talk.redirect contains '://' %}
          <a class="post-title" href="{{ talk.redirect }}" target="_blank">{{ talk.title }}</a>
          <svg width="2rem" height="2rem" viewBox="0 0 40 40" xmlns="http://www.w3.org/2000/svg">
            <path d="M17 13.5v6H5v-12h6m3-3h6v6m0-6-9 9" class="icon_svg-stroke" stroke="#999" stroke-width="1.5" fill="none" fill-rule="evenodd" stroke-linecap="round" stroke-linejoin="round"></path>
          </svg>
        {% else %}
          <a class="post-title" href="{{ talk.redirect | relative_url }}">{{ talk.title }}</a>
        {% endif %}
      </h3>
      <p>{{ talk.description }}</p>
      <p class="post-meta">
        {{ read_time }} min read &nbsp; &middot; &nbsp;
        {{ talk.date | date: '%B %d, %Y' }}
        {% if talk.venue %}
          &nbsp; &middot; &nbsp; {{ talk.venue }}
        {% endif %}
      </p>
      <p class="post-tags">
        <i class="fa-solid fa-calendar fa-sm"></i> {{ year }}
        {% if tags != "" %}
          &nbsp; &middot; &nbsp;
          {% for tag in talk.tags %}
            <i class="fa-solid fa-hashtag fa-sm"></i> {{ tag }} &nbsp;
          {% endfor %}
        {% endif %}
      </p>

{% if talk.thumbnail %}

</div>

  <div class="col-sm-3">
    <img class="card-img" src="{{ talk.thumbnail | relative_url }}" style="object-fit: cover; height: 90%" alt="image">
  </div>
</div>
{% endif %}
    </li>

    {% endfor %}

  </ul>

</div>

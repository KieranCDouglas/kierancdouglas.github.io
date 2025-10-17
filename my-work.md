---
title: My Work
permalink: /my-work/
layout: default
---

<h1>My Work</h1>
<p>Selected research and projects.</p>

<ul class="project-list">
  {% assign items = site.projects | sort: "year" | reverse %}
  {% for p in items %}
    <li class="project-card">
      <a class="project-link" href="{{ p.url | relative_url }}">
        {% if p.thumbnail %}
          <img src="{{ p.thumbnail | relative_url }}" alt="" class="project-thumb">
        {% endif %}
        <div class="project-meta">
          <strong>{{ p.title }}</strong>
          {% if p.year %}<span class="muted"> · {{ p.year }}</span>{% endif %}
          {% if p.summary %}<div class="summary">{{ p.summary }}</div>{% endif %}
        </div>
      </a>
    </li>
  {% endfor %}
</ul>

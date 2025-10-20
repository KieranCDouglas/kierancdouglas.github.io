---
title: My Work
permalink: /my-work/
layout: default
---

<h1>My Work</h1>
<p>Selected research and projects.</p>

<ul class="project-list project-list--expandable">
  {% assign items = site.projects | sort: "year" | reverse %}
  {% for p in items %}
  <li class="project-card project-card--expandable">
    <!-- Accessible toggle -->
    <button class="project-toggle" aria-expanded="false">
      {% if p.thumbnail %}
        <img src="{{ p.thumbnail | relative_url }}" alt="" class="project-thumb">
      {% endif %}
      <div class="project-meta">
        <strong class="project-title">{{ p.title }}</strong>
        {% if p.year %}<span class="muted"> · {{ p.year }}</span>{% endif %}

        {% assign authors_text = p.authors %}
        {% if p.authors and p.authors.size %}
          {% if p.authors.first %}
            {% assign authors_text = p.authors | join: ", " %}
          {% endif %}
        {% endif %}
        {% if authors_text %}
          <div class="project-authors">{{ authors_text }}</div>
        {% endif %}
        {% comment %} summary intentionally hidden in collapsed view {% endcomment %}
      </div>
    </button>

    <!-- Expanded panel: summary + optional PDF and/or external link -->
    <div class="project-details" hidden>
      <div class="project-details__inner">
        {% if p.summary %}
          <p class="summary summary--full">{{ p.summary }}</p>
        {% endif %}

        {% if p.pdf_url or p.external_url %}
          <p class="project-actions">
            {% if p.pdf_url %}
              <a class="btn btn--primary" href="{{ p.pdf_url | relative_url }}" target="_blank" rel="noopener">
                Open PDF
              </a>
            {% endif %}
            {% if p.external_url %}
              <a class="btn btn--primary" href="{{ p.external_url }}" target="_blank" rel="noopener" style="margin-left:.5rem">
                Open
              </a>
            {% endif %}
          </p>
        {% endif %}
      </div>
    </div>
  </li>
  {% endfor %}
</ul>

<script>
/* Expand/collapse cards */
(function() {
  const list = document.querySelector('.project-list--expandable');
  if (!list) return;

  list.addEventListener('click', function(e) {
    const toggle = e.target.closest('.project-toggle');
    if (!toggle) return;

    const card = toggle.closest('.project-card--expandable');
    const details = card.querySelector('.project-details');
    const isOpen = card.classList.contains('is-open');

    card.classList.toggle('is-open', !isOpen);
    details.hidden = isOpen;
    toggle.setAttribute('aria-expanded', String(!isOpen));
  });
})();
</script>

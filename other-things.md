---
layout: default
title: Other Things
permalink: /other-things/
---

<h1>Other Things</h1>
<p>Music, hobbies, and other experiments.</p>

<ul class="other-grid other-grid--expandable">
  {% assign items = site.others | sort: "year" | reverse %}
  {% for o in items %}
  <li class="other-card other-card--expandable">
    <button class="other-toggle" aria-expanded="false">
      {% if o.thumbnail %}
        <img src="{{ o.thumbnail | relative_url }}" alt="" class="other-thumb">
      {% endif %}
      <div class="other-meta">
        <strong class="other-title">{{ o.title }}</strong>
        {% if o.year %}<span class="muted"> · {{ o.year }}</span>{% endif %}
        {% if o.tags %}<div class="other-tags">{{ o.tags | join: ', ' }}</div>{% endif %}
      </div>
    </button>

    <div class="other-details" hidden>
      <div class="other-details__inner">
        {% if o.summary %}
          <p class="summary summary--full">{{ o.summary }}</p>
        {% endif %}

        {% if o.external_url %}
          <p class="other-actions">
            <a class="btn btn--primary" href="{{ o.external_url }}" target="_blank" rel="noopener">
              Open external link
            </a>
          </p>
        {% endif %}
      </div>
    </div>
  </li>
  {% endfor %}
</ul>

<script>
(function() {
  const grid = document.querySelector('.other-grid--expandable');
  if (!grid) return;

  grid.addEventListener('click', function(e) {
    const toggle = e.target.closest('.other-toggle');
    if (!toggle) return;

    const card = toggle.closest('.other-card--expandable');
    const details = card.querySelector('.other-details');
    const isOpen = card.classList.contains('is-open');

    card.classList.toggle('is-open', !isOpen);
    details.hidden = isOpen;
    toggle.setAttribute('aria-expanded', String(!isOpen));
  });
})();
</script>

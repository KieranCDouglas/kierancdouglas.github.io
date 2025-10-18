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
  <li class="project-card project-card--expandable" data-url="{{ p.url | relative_url }}">
    <!-- Button = better accessibility than <a> for toggling -->
    <button class="project-toggle" aria-expanded="false">
      {% if p.thumbnail %}
        <img src="{{ p.thumbnail | relative_url }}" alt="" class="project-thumb">
      {% endif %}
      <div class="project-meta">
        <strong class="project-title">{{ p.title }}</strong>
        {% if p.year %}<span class="muted"> · {{ p.year }}</span>{% endif %}
        {% if p.summary %}
          <div class="summary summary--teaser">{{ p.summary }}</div>
        {% endif %}
      </div>
    </button>

    <!-- Hidden panel; revealed on expand -->
    <div class="project-details" hidden>
      <div class="project-details__inner">
        {% if p.summary %}
          <p class="summary summary--full">{{ p.summary }}</p>
        {% endif %}

        {% if p.content %}
          <div class="project-body">
            {{ p.content | markdownify }}
          </div>
        {% endif %}

        <p class="project-actions">
          <a class="btn btn--primary" href="{{ p.url | relative_url }}">Open full page</a>
        </p>
      </div>
    </div>
  </li>
  {% endfor %}
</ul>

<script>
/* Expand/collapse cards (click or keyboard) */
(function() {
  const list = document.querySelector('.project-list--expandable');
  if (!list) return;

  list.addEventListener('click', function(e) {
    const toggle = e.target.closest('.project-toggle');
    if (!toggle) return;

    const card = toggle.closest('.project-card--expandable');
    const details = card.querySelector('.project-details');
    const isOpen = card.classList.contains('is-open');

    // Optional: only one open at a time (uncomment to enable)
    // list.querySelectorAll('.project-card--expandable.is-open').forEach(c => {
    //   if (c !== card) {
    //     c.classList.remove('is-open');
    //     const d = c.querySelector('.project-details');
    //     const t = c.querySelector('.project-toggle');
    //     if (d) d.hidden = true;
    //     if (t) t.setAttribute('aria-expanded', 'false');
    //   }
    // });

    card.classList.toggle('is-open', !isOpen);
    details.hidden = isOpen;                      // show/hide
    toggle.setAttribute('aria-expanded', String(!isOpen));
  });
})();
</script>

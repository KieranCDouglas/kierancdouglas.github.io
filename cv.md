---
layout: default
title: CV
permalink: /cv/
---

<!-- Desktop/Large screens: embedded, scrollable PDF -->
<div class="cv-wide">
  <iframe
    class="pdf-viewer"
    src="{{ 'assets/cv.pdf' | relative_url }}#zoom=page-fit"
    loading="lazy"
    title="Kieran Douglas CV">
  </iframe>
</div>

<!-- Mobile/Small screens: open in the device PDF viewer -->
<div class="cv-mobile">
  <p>On mobile, it’s best to open the PDF in your viewer:</p>
  <a class="btn btn--primary" href="{{ 'assets/cv.pdf' | relative_url }}" target="_blank" rel="noopener">
    Open CV (PDF)
  </a>
</div>

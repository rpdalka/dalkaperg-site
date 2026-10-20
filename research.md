---
layout: page
title: Research
intro: An overview of the questions we study.
---

{% for area in site.data.research %}
<section class="research-area">
  <h2>{{ area.title }}</h2>
  {{ area.description | markdownify }}
</section>
{% endfor %}

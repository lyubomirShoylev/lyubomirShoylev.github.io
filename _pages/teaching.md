---
layout: page
title: teaching
permalink: /teaching/
description: Information about courses I have taught.
nav: false

teaching_categories: [brezi, oxf-compos, prep-olymp, pmgbs]

teaching_dict:
  brezi: Beli Brezi Astronomy School
  oxf-compos: COMPOS Programme, Oxford University
  prep-olymp: Preparation Camp for IAO, Team Bulgaria
  pmgbs: High School of Natural Sciences and Mathematics 'Nicola Obreshkov'
---

<div class="post">
  <article>
    <div class="teaching">
      {% for host in page.teaching_categories%}
        <h3 class="teaching-host mt-4">{{ page.teaching_dict[host] }}</h3>
        {%- assign categorized_teaching = site.teaching | where: "host", host -%}
        {%- assign sorted_teaching = categorized_teaching | sort: "year" | reverse %}
        <!-- Generate card for each course -->
          {% for course in sorted_teaching %}
            {% include teach-card.html%}
          {% endfor %}



      {% endfor %}
    </div>
  </article>
</div>

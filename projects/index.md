---
layout: page
title: Projects
description: Other builds, tools and experiments — the things that aren't a walkable room (yet).
---

<h1>Projects</h1>

<p>Things built along the way — tools, machines, odd experiments. One file per project in <code>_projects/</code>.</p>

{% assign projects = site.projects | sort: "order" %}

{% if projects == empty %}
<p><em>No projects yet — copy <code>_projects/_TEMPLATE.md</code> to add one.</em></p>
{% else %}
<div class="card-grid">
  {% for project in projects %}
    <a class="card card-plain" href="{{ project.url | relative_url }}">
      <div class="card-body">
        <h3 class="card-title">{{ project.title | escape }}</h3>
        <p class="card-sub">{{ project.blurb | escape }}</p>
      </div>
    </a>
  {% endfor %}
</div>
{% endif %}

---
layout: page
title: Bole Hill Quarry
description: The buildings of Bole Hill Quarry, scanned as walkable 3D meshes — click in, wait for the mesh to stream, then explore.
---

<h1>Bole Hill Quarry</h1>

<p>
  Building by building, the quarry is being captured with photogrammetry and
  rebuilt as walkable 3D. Each card below is a real structure on the site —
  click one and the viewer opens straight inside it. Click to grab control,
  drag to look around, and walk with <kbd>W</kbd><kbd>A</kbd><kbd>S</kbd><kbd>D</kbd>.
  Meshes are a few dozen megabytes, so give them a few seconds on first load.
</p>

<p>
  Every scan started as a few hundred ordinary photos: a pipeline on the
  server meshes them, optimises them for the web, and publishes them here —
  no plugins, no accounts, no apps.
</p>

{% assign rooms = site.rooms | sort: "order" %}

{% if rooms == empty %}
<p><em>Nothing scanned yet — the first buildings are processing.</em></p>
{% else %}
<div class="card-grid">
  {% for room in rooms %}
    {% include room-card.html room=room %}
  {% endfor %}
</div>
{% endif %}

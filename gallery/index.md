---
layout: page
title: Gallery
description: Walkable 3D scans of real rooms — click in, wait for the mesh to stream, then explore.
---

<h1>The rooms</h1>

<p>
  Each card below is a full 3D reconstruction of a real space. Click one and
  the viewer opens straight into the room — click to grab control, drag to
  look around, and walk with <kbd>W</kbd><kbd>A</kbd><kbd>S</kbd><kbd>D</kbd>.
  Meshes are a few dozen megabytes, so give them a few seconds on first load.
</p>

{% assign rooms = site.rooms | sort: "order" %}

{% if rooms == empty %}
<p><em>No rooms yet — run <code>./add_room.sh</code> to publish the first one.</em></p>
{% else %}
<div class="card-grid">
  {% for room in rooms %}
    {% include room-card.html room=room %}
  {% endfor %}
</div>
{% endif %}

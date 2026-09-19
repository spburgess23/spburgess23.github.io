---
layout: page
title: Quarry Map
description: Bole Hill Quarry from above — click a building to walk inside it in 3D.
---

<link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css">
<script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>

<h1>The site from above</h1>

<p>
  Every marker is a real building at Bole Hill Quarry, scanned as a walkable
  3D mesh. Click one to step inside — or <a href="{{ '/quarry/' | relative_url }}">browse the list</a>.
</p>

<div id="quarrymap"></div>

<script>
const rooms = [
{% assign rooms = site.rooms | where: "project", "quarry" | sort: "order" %}
{% for r in rooms %}
  {% assign vpath = "/assets/rooms/" | append: r.folder | append: "/offline_viewer.html" %}
  {% assign has_viewer = site.static_files | where: "path", vpath | first %}
  {title: "{{ r.title | escape }}", lat: {{ r.lat }}, lon: {{ r.lon }},
   url: "{{ r.url }}", ready: {% if has_viewer %}true{% else %}false{% endif %}}{% unless forloop.last %},{% endunless %}
{% endfor %}
];

const map = L.map('quarrymap', {scrollWheelZoom: false});
const bounds = L.latLngBounds(rooms.map(r => [r.lat, r.lon]));
map.fitBounds(bounds, {padding: [50, 50], maxZoom: 17});
L.tileLayer('https://server.arcgisonline.com/ArcGIS/rest/services/World_Imagery/MapServer/tile/{z}/{y}/{x}', {
  maxZoom: 21,
  attribution: 'Imagery &copy; <a href="https://www.esri.com/">Esri</a>, Maxar, Earthstar Geographics'
}).addTo(map);

for (const r of rooms) {
  const m = L.marker([r.lat, r.lon]).addTo(map);
  m.bindTooltip(r.title, {permanent: true, direction: 'top', className: 'maplabel'});
  m.bindPopup(
    `<b>${r.title}</b><br>` +
    (r.ready ? `<a href="${r.url}">Walk inside &rarr;</a>` : `Mesh in progress&hellip;`));
}
map.on('click', () => map.scrollWheelZoom.enable());
</script>

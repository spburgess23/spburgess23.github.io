---
layout: project
title: The Scan Pipeline
order: 1
blurb: "Photos in, walkable 3D rooms out — the pipeline that builds this gallery's content."
link:
---

The engine room behind the gallery: a pipeline on the Linux box that takes
raw photo sweeps, reconstructs them into textured meshes, calibrates the
viewing pose, and emits a self-contained web viewer plus an optimised
`.glb` for every room.

Its final act is publishing: each finished room lands in this site with one
script run. The website never has to know a pipeline exists — it just eats
what it's fed.

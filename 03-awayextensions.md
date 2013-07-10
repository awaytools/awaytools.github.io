---
layout: page
title : Away Extensions
header : Post Archive
tagline : <p>A collection of plugins and scripts that provide a direct workflow between commercial 3D modeling packages and Away3D. Extensions are available for all the major software packages including <a href="https://github.com/awaytools/awd-tools-3dsmax">3D Studio Max</a>, <a href="https://github.com/awaytools/awd-tools-maya">Maya</a>, <a href="https://github.com/awaytools/awd-tools-c4d">Cinema 4D</a> and <a href="https://github.com/awaytools/awd-tools-blender">Blender</a>. At present, Away Extensions are maintained on a ad-hoc basis due to limited resources.</p>
group: navigation
permalink: "awayextensions/"
---
{% include JB/setup %}

{% assign posts_collate = site.categories.awayextensions %}
{% assign category = 'awayextensions' %}
{% include JB/posts_collate %}
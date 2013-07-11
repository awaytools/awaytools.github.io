---
layout: page
title : AWD Format
tagline : <p>An optimised binary format for online 3D assets, storing all aspects of a 3D scene for easy retrieval. The format is based on the data structures available in Away3D, and is designed to be light-weight, compact, fast and extensible. The internal structure of the format can be viewed via the latest <a href="https://github.com/awaytools/awd-sdk/blob/master/docs/AWD_format_specification2_1_Alpha.pdf?raw=true">AWD specification</a> doc.</p><p>To find out more on the AWD Format, please visit our <a href="/awdformat/about/">About page</a></p>
image : Logo_AWD_300x300.png
header : Post Archive
category : AWDFormat
group: navigation
permalink: "awdformat/"
---
{% include JB/setup %}

{% assign posts_collate = site.categories.awdformat %}
{% include JB/posts_collate %}
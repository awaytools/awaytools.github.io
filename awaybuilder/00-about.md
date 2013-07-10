---
title : About
layout: page
header : Post Archive
group: AwayBuilder
category : AwayBuilder
permalink: "about/"
---
{% include JB/setup %}

## What is Away Builder?

Away Builder is a visual editing tool that takes the pain out of asset creation for Away3D. What used to take a lot of coding by hand is now accomplished in just a few clicks, using either the downloadable [AIR application](https://github.com/awaytools/AwayBuilder/blob/master/awaybuilder-desktop/bin-release/AwayBuilderApplication.air?raw=true) or online [web version](/awaybuilder/AwayBuilderApplication.html) of the tool. Away Builder is built on top of the [Away3D framework](http://www.away3d.com), and leverages Stage3D - the hardware acceleration technology built into Adobe's Flash & AIR runtimes.

## What does Away Builder Do?

Away Builder allows the import and arranging / augmenting of 3D assets. The current version of Away Builder allows the import of a variety of different asset formats including OBJ, 3DS, MD2, MD5 and Collada, as well as jpg and png formats for use in textures. 

Once imported, Away Builder allows the editing of your assets via Away3D-based controls, and can adjust such parameters as scene position, material, shading, lighting and animation settings.

You can think of Away Builder as a normalish dynamic blog but rather than parsing content, templates, and tags
on each request, Jekyll does this once _beforehand_ and caches the _entire website_ in a folder for serving statically.

## Away Builder is Not Modeling Software

**Away Builder is a 3D workflow tool.**

Away Builder does not come with any modeling capabilities and you should leave this ability to your professional 3D editors / designers.
What Away Builder does offer a visual solution to the problem of asset preparation for Away3D projects.

## Initial Setup

Away Builder is bundled with the Adobe Gaming SDK as a desktop application, with the latest binary always available from our [github repository](https://github.com/awaytools/AwayBuilder). It is also available as an [in-browser demonstration](/awaybuilder/AwayBuilderApplication.html) that you can instantly access and try out before downloading and installing.

## The AWD Format

Away Builder uses the AWD format as an output file format for use in Away3D. This is another open source project managed by [The Away Foundation](http://www.theawayfoundation.org), and the current format specification can be view via the latest [AWD specification doc](https://github.com/awaytools/awd-sdk/blob/master/docs/AWD_format_specification2_1_Alpha.pdf?raw=true)

## Conclusion

We hope this paints a clearer picture of what Away Builder is and for what purpose it has been created. 

## More Info

Please take a look at [{{ site.categories.api.first.title }}]({{ BASE_PATH }}{{ site.categories.api.first.url }}) 
or jump right into [Usage]({{ BASE_PATH }}{{ site.categories.usage.first.url }}) if you'd like.
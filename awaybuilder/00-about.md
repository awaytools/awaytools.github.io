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

Away Builder is a visual editing tool that takes the pain out of asset creation in Away3D. What used to take a lot of coding by hand is now accomplished in just a few clicks, using either the downloadable [AIR application](https://github.com/awaytools/AwayBuilder/blob/master/awaybuilder-desktop/bin-release/AwayBuilderApplication.air?raw=true) or online [web version](/awaybuilder/live_tool/) of the tool. Away Builder is built on top of the [Away3D framework](http://www.away3d.com), and leverages Stage3D - the hardware acceleration technology built into Adobe's Flash & AIR runtimes.

## What does Away Builder Do?

Away Builder allows the import and optimisation / augmentation of 3D assets. The current version of Away Builder allows the import of a variety of different asset formats including OBJ, 3DS, MD2, MD5 and Collada, as well as jpg and png image formats for use in textures. 

Once imported, Away Builder allows the editing of your assets via Away3D-based controls, and can adjust parameters such as scene position, material setup, shading, lighting and animation settings.

You can think of Away Builder as the missing link between designer and developer on a 3D project. In order for the designer to hand off assets to the developer, they want some assurances as to what the final results will look like in Away3D. Away Builder allows them to preview their creations, but more than that, tailor the visual settings in the engine to their exact requirements without any need for coding. The developer then receives a single file that will recreate the designers intent upon loading, while still allowing easy integration of their assets within an application framework.

## Away Builder is Not Modeling Software

**Away Builder is a 3D workflow tool.**

Away Builder does not come with any modeling capabilities and you should leave this ability to your professional 3D editors / designers.
What Away Builder does offer is a visual solution to the problem of asset preparation for Away3D projects.

## Initial Setup

Away Builder is bundled with the Adobe Gaming SDK as a desktop application, with the latest binary always available from our [github repository](https://github.com/awaytools/AwayBuilder). It is also available as an [in-browser demonstration](/awaybuilder/AwayBuilderApplication.html) that you can instantly access and try out before downloading and installing.

## The AWD Format

Away Builder uses the AWD format as an output file format for use in Away3D. This is another open source project managed by [The Away Foundation](http://www.theawayfoundation.org), and the current format specification can be view via the latest [AWD specification doc](https://github.com/awaytools/awd-sdk/blob/master/docs/AWD_format_specification2_1_Alpha.pdf?raw=true). You can find more info on the [AWD About Pages](/awdformat/about)

## Source Code

As well as the tool being freely available for use in both desktop and online form, we also supply the source code for you to hack about with, augment for your own company needs, contribute back to the project or just have a nose around. We use the [Apache 2.0](http://www.apache.org/licenses/LICENSE-2.0) which grants the recipient freedom to use the code for pretty much whatever purpose they require, without fear of restriction. Away Builder is built using [Apache Flex](http://flex.apache.org/), [Robotlegs](http://www.robotlegs.org/) and of course, [Away3D](http://www.away3d.com). The code can be downloaded from our [Github Repository](https://github.com/awaytools/AwayBuilder), where you will also find instructions for setting up a local build of the project.
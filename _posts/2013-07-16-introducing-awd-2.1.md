---
layout: post
title : Introducing AWD 2.1
category : AWDFormat
summary: "The AWD Format has gone through a major upgrade in its 2.1 version. In this post we give a brief outline of the changes already made, and the plans for further additions"
tags : [News, Releases]
image : introducing-awd-2.1.jpg
---
{% include JB/setup %}

The AWD format has recently been involved in a major upgrade alongside the construction of [Away Builder](/awaybuilder), and is becoming a backbone for design workflows within Away3D projects. Its latest 2.1 build is currently in Alpha, and adds significant functionality to enable the storage and retrieval of Away3D data structures.

## Compatibility

You can grab a copy of the latest specification doc by [Downloading the PDF](https://github.com/awaytools/awd-sdk/blob/master/docs/AWD_format_specification2_1_Alpha.pdf?raw=true) form GitHub. Care has been taken to make all changes both backward and forward compatible - in the event of a 2.1 file being loaded into a 2.0 parser, the data will degrade gracefully with any unrecognised data blocks simply ignored. Similarly, you can expect all your existing 2.0 AWDs to work in the new 2.1 parser, and we intend to maintain this compatibility moving forward.

## Additions in this release

The format's main additions have centered around providing a more detailed data structure for scene data, particularly in the areas of materials and animation. A full set of updates will be published on GitHub in due course, but here are some of the more significant areas of upgrade so far:

### Materials

- Extra material properties (smooth, mipmap, bothSides, alphaBlending, alphaThreshold, preMultiplied, blendMode, lightPicker etc)
- Multiple texture assignments in a single material (for diffuse, ambient, specular, and normal textures)
- Shader method assignment controlling individual method behaviour (for diffuse, ambient, specular and normal methods)
- Material effects methods for custom shader processing options

### Animation

- Vertex animation data object
- Animation sets (Vertex & Skeleton) 
- Animator objects for applying animations to mesh objects (Vertex & Skeleton)

### Lights

- Light picker object for StaticLightPicker
- Light objects for DirectionalLight and PointLight
- Shadow method and shadow mapper objects for both directional and point lights 

### Micellaenous

- Texture projection objects
- Geometry primitive objects (Sphere, Cube, Cylinder etc)
- Camera and lens objects
- Skybox object


Once the next stage of Away Builder development commences, we expect to see a more comprehensive set of AWD features emerge. Of course, we welcome any suggestions on focus or areas of interest for future additions to the format, and will be posting more in the coming weeks on roadmap and planned milestones for further development.

To find out more on the AWD Format's history and direction, please visit our [About](/awdformat/about/) page.


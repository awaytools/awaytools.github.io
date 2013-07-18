---
title : About
layout: page
header : Post Archive
group: AWDFormat
category : AWDFormat
permalink: "about/"
---
{% include JB/setup %}

## What is AWD?

AWD is a compact binary format for the storing and retrieval of 3D data. It is primarily designed for use in websites and installable mobile and desktop applications, and is optimised for use with the [Away3D framework](http://www.away3d.com). For an up-to-date document of the specification, you can download the [AWD Format Specification](https://github.com/awaytools/awd-sdk/blob/master/docs/AWD_format_specification2_1_Alpha.pdf?raw=true) from GitHub as a PDF.

## Why have we created the AWD Format?

AWD is a format designed for online use, be it through a web browser, mobile or desktop application. It defines and delivers on the following requirements for a general purpose 3D format for the web:

- A compact binary file that is optimised for OTA deployment
- A lightweight block format that is fast to parse
- A tag system that is easy to extend with user-generated attributes
- An internal structure that allows the streaming of larger file and scenes
- A free and open source license, available for anyone to implement in their workflow

As well as the above, the AWD format has many data structures that transfer seamlessly with the data structures in Away3D-based 3D scenes, offering many options for asset storage and retrieval when dealing with Away3D-based projects.

## AWD is not an Interchange format

**AWD is a publishing format for 3D files.**

AWD is not designed to be multi-purpose or multi-compatible. AWD is built to provide a standard for scene data in Away3D projects. Rather than looking to replace existing interchange formats like Collada and FBX, AWD is intended as a container for assets in a live application. The former can still be used for the majority of production work, but it is in the process of publishing that we see AWD being used to its greatest potential. Our focus with AWD is therefore around the tools and extensions that allow seamless conversion between production assets and published assets, and it is here that we look to supporting resources in the Away Tools collection such as [Away Builder](/awaybuilder) and [Away Extensions](/awayextensions)

## ToolChain

Currently there are a number of Away Tools projects using the AWD format, as well as the Away3D engine itself. These are:

- [Away Builder](http://www.github.com/awaytools/AwayBuilder)
- [Maya AWD Exporter](http://www.github.com/awaytools/awd-tools-maya)
- [Blender AWD Exporter](http://www.github.com/awaytools/awd-tools-blender)
- [3DS Max Exporter](http://www.github.com/awaytools/awd-tools-3dsmax)
- [C4D Exporter](http://www.github.com/awaytools/awd-tools-c4d)

With the exception of the Away Builder project (written in ActionScript 3), all projects have a dependency on the [AWD SDK](https://github.com/awaytools/awd-sdk) repository, which contains, among other things:

- **libawd:** A C++ library to (greatly) simplify encoding of AWD files
- **PyAWD:** A Python toolkit, offering a pythonic way to work with AWD files.

The latter can be compiled as a wrapper for libawd, or as a standalone (with poorer writing performance) and currently works for both Python 2.6 and 3.x.

## Source Codes

The AWD SDK is available for unrestricted use in your own tools and workflows, using the [Apache 2.0 license](http://www.apache.org/licenses/LICENSE-2.0) for distribution. The latest sources are always available for [download from GitHub](https://github.com/awaytools/awd-sdk/archive/master.zip), or can be forked and worked on in your own git repositories.

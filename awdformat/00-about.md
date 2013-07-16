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

AWD is a compact binary format for the storing and retrieval of 3D data. It is primarily designed for use in websites and installable mobile and desktop applications, and is optimised for use with the [Away3D framework](http://www.away3d.com). For an up-to-date document of the specification, you can download the [AWD Format Specification](https://github.com/awaytools/awd-sdk/blob/master/docs/AWD_format_specification2_1_Alpha.pdf?raw=true) PDF on GitHub.

## Why have we created the AWD Format?

AWD is a format designed for online use, be it through the browser, mobile or desktop application. It defines and delivers on the following requirements for a general purpose 3D format for the web:

- A compact binary file that is optimised for OTA deployment
- A lightweight block format that is fast to parse
- A tag system that is easy to extend with user-generated attributes
- An internal structure that allows the streaming of larger file and scenes
- A free and open source license, available for anyone to implement in their workflow

As well as the above, the AWD format has many data structures that transfer seamlessly with the data structures in Away3D-based 3D scenes, offering many options for asset creation when dealing with Away3D-based projects.

## AWD is not an Interchange format

**AWD is a publishing format for 3D files.**

AWD is not designed to be multi-purpose or multi-compatible. AWD is built to provide a standard for scene data in Away3D projects. Rather than looking to replace existing interchange formats like Collada and FBX, AWD is intended as a container for assets in a live application. The former can still be used for the majority of production work, but it is in the process of publishing that we see AWD being used to its greatest potential. Our focus with AWD is therefore around the tools and extensions that allow seamless conversion between production assets and published assets, and it is here that we look to supporting resources in the Away Tools collection such as [Away Builder](/awaybuilder) and [Away Extensions](/awayextensions)

## Source Code

The AWD SDK consists of a set of AWD parsers and serialisers for use in your own tools and workflows, all of which use the [Apache 2.0 license](http://www.apache.org/licenses/LICENSE-2.0) for distribution and carry no restrictions on use. The latest sources are always available from our [GitHub repository](https://github.com/awaytools/awd-sdk), and some examples of SDK utilisation can be seen in the extensions and plugins under development in our own [Away Extensions](/awayextensions) libraries.

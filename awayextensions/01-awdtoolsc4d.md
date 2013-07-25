---
title : AWD-Tools-C4D
layout: page
header : Post Archive
group: AwayExtensions
prettygroup: Away Extensions
category : AwayExtensions
permalink: "about/AWDToolsC4D/"
---
{% include JB/setup %}



## What is AWD-Tools-C4D ?

AWD-Tools-C4D is a exporter-plugin for Cinema4D R13+, that enables to export C4D-scenes as AWD-files.

Like the other AWD-Tools, it is open source and hostet on [GitHub](https://github.com/awaytools/awd-tools-c4d). 



## How should the AWD-Tools-C4D be used ?

The AWD-Tools-C4D can be used to create AWD-files, that can be loadet and used within the Away3d-Engine.

Since some C4D-object-properties can not be mapped to Away3d-object-properties, it is recommanded to inspect and finalize the exported files using the AwayBuilder.



## How to install AWD-Tools-C4D ?

The AWD-Tools-C4D does not need any installer or setup. Download the [AWD-Tools-C4D](https://github.com/awaytools/awd-tools-c4d/archive/master.zip), and extract the zip-archiv into your Cinema4D-Plugin-Directory.

In Cinema4D you should be able to access the exporter-plugin via the plugin-menu, and several tag-plugins in the tag-menu
(right-mouse-click on objects in the object-manager)



## What is the current state of development for the AWD-Tools-C4D ?

The AWD-Tools-C4D is still in a early state.
At the moment the AWD-Tools-C4D is the only Away Extension that is not using any of the libraries provided by the AWD-SDK.
It is written in python, and will be refactored to make use of the [ppyAWD](https://github.com/awaytools/awd-sdk/tree/master/python-ppyawd) soon.


## Where can i get more information/documentation about the AWD-Tools-C4D?

There is a documentation inculded in the plugin (Menu: File->Help).
The included documentation is not complete (yet).

We will provide more articles and tutorials about the AWD-Tools-C4D on this webiste.

Articles / Tutorials:

* [Introducing to AWD-Tools-C4D](/awayextensions/introducing-awdtoolsc4d)
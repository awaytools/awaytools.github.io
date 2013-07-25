---
title : About
layout: page
header : Post Archive
group: AwayExtensions
prettygroup: Away Extensions
category : AwayExtensions
permalink: "about/"
---
{% include JB/setup %}

## What are the Away Extensions?

The Away Extensions are a collection of plugins and scripts (AWD-Tools) that provide a direct workflow between commercial 3D modeling packages and Away3D.

AWD-Tools can be installed into 3D modeling packages, to enable the export of 3D scene data into AWD-Files.


## What is the AWD-SDK

The [AWD-SDK](https://github.com/awaytools/awd-sdk) is the core of all Away Extensions, as it provides the c++ and python libraries used to build the other Away Extensions.

The AWD-SDK contains 3 different libraries, to simplify managing and exporting of AWD-Data.

* [libAWD (c++ library)](https://github.com/awaytools/awd-sdk/tree/master/cpp-libawd)
* [pyAWD (python library that wraps the libAWD for better performance)](https://github.com/awaytools/awd-sdk/tree/master/python-pyawd)
* [ppyAWD (python library without any c++ wrapping)](https://github.com/awaytools/awd-sdk/tree/master/python-ppyawd)

Using the libAWD or pyAWD is clearly the better solution for best performance in the final plugins.
However, libAWD and pyAWD both have to be compiled for a specific platform (win / mac). 
Thats why we introduced the ppyAWD. It can be used to create AWDTools that do not need to be compiled.
 


## Away Extensions and AwayBuilder?


While the exported files can be used in your Away3d project directly, we recomment to import them into AwayBuilder.



## What Away Extensions exists?

* 3dsMax (AWD-Tools-3ds)
* Maya (AWD-Tools-Maya)
* Blender (AWD-Tools-Blender)
* [Cinema4D (AWD-Tools-C4D)](/awayextensions/about/AWDToolsC4D)



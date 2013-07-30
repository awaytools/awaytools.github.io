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

## What are Away Extensions?

Away Extensions are a collection of plugins and scripts that provide a direct workflow between commercial 3D modeling packages and Away3D. Installing an Away Extensions library is carried out using the regular installation processes characterised by the modeling software in question. A standard function of Away Extensions is to allow the export of AWD files for use in Away Builder or directly in Away3D.


## Dependencies

The [AWD-SDK](https://github.com/awaytools/awd-sdk) is used as the core of many Away Extensions, as it provides the c++ and python libraries used to serialise the binary data required for the creation of AWD files.

The AWD-SDK contains 3 different libraries that simplify the management and export of AWD data.

* [libAWD (c++ library)](https://github.com/awaytools/awd-sdk/tree/master/cpp-libawd)
* [pyAWD (python library that wraps the libAWD for better performance)](https://github.com/awaytools/awd-sdk/tree/master/python-pyawd)
* [ppyAWD (python library without any c++ wrapping)](https://github.com/awaytools/awd-sdk/tree/master/python-ppyawd)

Using the libAWD or pyAWD libraries gives the best performance for AWD exporter plugins, but is not always an option given the OS and specification of the host machine (both libraries have to be compiled for use on a specific platform OS). The ppyAWD library was created to be compatible across more systems as it is a pure python library with no c++ dependencies.


## Away Extensions and AwayBuilder?

Away Extensions are designed to complement the workflow already offered in Away Builder for a variety of existing 3D formats. While exported AWD files from an Away Extensions library can be used in your Away3D project directly, you can also import them into [Away Builder](/awaybuilder) for further previewing and tweaking.


## What platforms do Away Extensions support?

The current software list includes:

- 3D Studio Max
- Maya
- Blender
- [Cinema4D](/awayextensions/C4D)



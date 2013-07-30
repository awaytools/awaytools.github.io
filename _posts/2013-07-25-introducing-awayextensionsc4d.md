---
layout: post
title : Introducing Away Extensions C4D
category : AwayExtensions
summary: "The Cinema4D extensions repository is the first AwayExtensions library to be upgraded to support the new features of AWD 2.1"
tags : [News, Release, C4D]
image : introducing-awayextensionsc4d.jpg
---
{% include JB/setup %}

A new set of extensions that compliment a Cinema4D -> Away3D workflow have been uploaded to the awaytools Github. This is the first AwayExtensions library to be upgraded to support the <a href="/awdformat/introducing-awd-2.1">new features of AWD 2.1</a>

Development is ongoing, but we encourage any Cinema4D users to try things out as the included tools can already be used to export a C4D-scene into an AWD 2.1 file that includes lights, materials and animations. The source is written in python and can be downloaded from the right-hand link or browsed by going to <a href="https://github.com/awaytools/awayextensions-c4d">https://github.com/awaytools/awayextensions-c4d</a>

The following is an overview of the current AWD support in Cinema4D.

# Contents

- [1. General](#main1)
- [2. Supported Objects](#main2)
  - [2.1 Null-Objects](#main2sub1)
  - [2.2 Polygon-Objects](#main2sub2)
  - [2.3 Primitives](#main2sub3)
  - [2.4 Instance-Objects](#main2sub4)
  - [2.5 Joint-Objects](#main2sub5)
  - [2.6 Light-Objects](#main2sub6)
  - [2.7 LightPicker](#main2sub7)
  - [2.8 Camera-Objects](#main2sub8)
- [3. AWDObjectSettings Tag](#main3)
- [4. Materials](#main4)
  - [4.1 Texture-Tags](#main4sub1)
- [5. Textures](#main5)
- [6. Animations](#main6)


<section id="main1l"/>
# 1. General

Before using the AWD exporter, it is advised that you save your C4D-scene. You do not need to save every scene-change, but the scene must have a valid name and a document-path, and must not be a newly created scene, that has never been saved.

To ensure the exporter will find the filepaths to all textures, it is recommended to perform a "Save Project with Assets" before exporting a scene. this will let you choose a name and a location and will save the project to a new folder, created at the chosen location with the given name. All textures used in the project will be saved to a folder called "tex" next to the saved C4D-project, making them easy to retrieve. For easy access (and as a reminder), a "Save Project with Assets" shortcut has been included into the exporter GUI.

The C4D layering system is frequently used in a project to prevent groups of objects from being displayed in the main view. This arrangement is ignored by the exporter - all objects found inside a C4D-project, regardless of layer, will be exported in the same way. To prevent unexpected results, it is currently recommended to avoid using the C4D layering system altogether.


<section id="main2"/>
# 2. Supported Objects

Unsupported objects will be ignored by the exporter. If an unsupported object is parent of a supported object, it will be exported as a Null object (e.g. an Away3D ObjectContainer3D object)

Most unsupported objects can be easily converted into polygon-objects in C4D (eg. right click on Hypernurbs and select "Current state to object")


<section id="main2sub1"/>	
## 2.1 Null Objects	
		
Null objects are exported as ObjectContainer3Ds. A null object has a name, a 3D transform matrix and a list of children. All other scene-objects inherit these three properties.

<section id="main2sub2"/>
## 2.2 Polygon Objects

All polygon objects will be triangulated into Away3D Geometry objects on export.

The point count of a polygon object shown in C4D (Object information), will in most cases not be the same as the point count of the generated Away3D geometry.
 This is due to C4D storing vertices with the potential for shared UV values, normal-values etc. for different points. In AWD, the geometry data is organised into unique  vertices that do not share data with any other vertices. This is done for fast parsing, but if you're geometry has a lot of shared UV values (seams) or un-merged normal values (phong breaks) you may want to consider optimising the data before exporting.

In C4D, one polygon can have multiple materials assigned to it. The exported Away3D geometry will have one SubGeometry for each material that is used in the polygon-object, however only one material per polygon will be exported. A SubGeometry has a restricted size based on the maximum vertex count allowed for a single draw call in Away3D (65536) - therefore the exporter might need to create several SubGeometries for a single polygon.

Polygon-objects can be set to display object colors instead of the assigned materials ("object-color-mode"). The exporter will export an Away3D ColorMaterial object for each object color used.

In C4D, objects can inheritate materials assigned to their parent objects. The exporter will resolve this material assignment, so that every mesh is exported with the correct materials assigned directly.

Polygon objects can be animated. [Read more information in the animation chapter.](#main6)


<section id="main2sub3"/>
## 2.3 Primitives

AWD 2.1 can store primitive geometry using the primitive's parameters rather than the raw vertex data. The following C4D primitives are supported for export:

- Plane
- Sphere
- Cube
- Cylinder
- Cone
- Capsule
- Torus

The up-vector for all exported primitives will default to the y-axis (yup = true).


<section id="main2sub4"/>
## 2.4 Instance Objects

To be included in an AWD export, a C4D instance object must reference either a polygon object or one of the supported C4D primitves.

If the instance object is defined as a render instance, it will use the same object color mode as the referenced object. Otherwise it will use its own object color mode. If the referenced polygon object has a material assigned directly, the instance object will use the same material. If the referenced polygon-object has no material assigned directly, the instance-object can have  its own material applied (directly or by inheritance).


<section id="main2sub5"/>
## 2.5 Joint-Objects	

To  be included in an AWD export, a Joint object needs to be part of an AWDSkeleton / AWDSkeletonAnimation. 
Read more information in the [animation chapter](#main6)


<section id="main2sub6"/>
## 2.6 Light-Objects	
		
Only two types of lights are supported in the current AWD format, point lights and directional lights.

C4D Point lights will be exported as AwayD PointLight objects, infinite lights will be exported as Away3D DirectionalLight objects.

Export light properties:

- Transform (position, rotation).
- Color (RGB).
- Intensity for ambient, specular and diffuse components.

In Away3D, a light object has different intensity values for ambient, specular and diffuse components. This is not the case In C4D, so the values are determined by the single strength value of the light. A checkbox to enable/disable specular, ambient or diffuse light intensities controls the extra values in the output.

- A specular, ambient or diffuse checkbox that is disabled will export the property with an intensity (level) of 0.
- A specular, ambient or diffuse checkbox that is enabled will export the property with an intensity (level) of the general light strength.

<section id="main2sub7"/>
## 2.7 LightPicker

In C4D, each light source has a list of objects that that define which objects are effected by the light. Away3D uses a separate grouping object known as a Light Picker that can be defined individually for each object or for a group of objects.

The AWD exporter will create an Away3D StaticLightPicker for each light so the lighting setup is recreated in Away3D. Since the Away3D StaticLightPicker is a property of a material rather than an object, the exporter will automatically clone any material that requires different light treatment on different objects.


<section id="main2sub8"/>
## 2.8 Cameras

Cameras are exported by default. The only supported projection currently is "Perspective". All other projections will be automatically exported as "Perspective".


<section id="main3"/>
# 3. AWDObjectSettings Tag


For best results, it is a good idea to clean your C4D scene before using the AWD exporter so no unsupported/unnecessary objects are included. In the cases where objects that are not intended for export are still required in the scene, an AWDObjectSettingsTag can be applied with the "Export" option set to false. This will cause the exporter to ignore them when exporting the scene.

If your ignored objects contain a lot of children to be ignored, a quick way to strip them all is to enable the "Apply to Childs" option in an AWDObjectSettingsTag with "Export" set to false. Otherwise, any supported objects found in the children of an ignored object will still be exported, with the ignored object showing up in the exported scenegraph as an ObjectContainer3D.


<section id="main4"/>
# 4. Materials


The AWD exporter currently supports a subset of the C4D standard material. 

In C4D, a standard material is made up of a list of channels. Currently supported channels include:

You can expand this list, but a custom-channel will not be read by the exported.

This channels will be exportet:

- **Color Channel:** If the shader slot of the color channel contains a bitmap shader with a texture file, the material will be exported as an Away3D TextureMaterial, with the texture stored as an Away3D BitmapTexture. Otherwise, the material is exported as an Away3D ColorMaterial using the color value of the channel.

- **Transparency Channel:** The strength of the transparency is exported as the alpha property of the material. No other settings of the transparency channel are exported.

- **Normal Channel:** Only the normal texture found in the shader slot of the normal channel is exported. No other settings of the normal channel are exported.

- **Specular Channel:** Only the diffuse texture found in the shader slot of the specular channel is exported (as an Away3D SpecularTexture). No other settings of the specular channel are exported.

In C4D, most material channels contain a shader slot. This slot (or LinkBox) can contain many different shader types (e.g. Noise, Fresnel, Layer, etc). Currently only the bitmap shader type is supported for export.


<section id="main4sub1"/>
## 4.1 Texture Tags:
	
In C4D, materials are assigned to objects by a texture tag and it is possible to assign multiple materials to the same polygon object, However, in Away3D only one material can be applied to a SubGeometry. The exporter therefore only ever takes one material from each polygon to use in the AWD file. For polygon objects with multiple materials, this is determined as the first encountered texture tag that appears compatible for export.

The only supported projection mode for texture tags is "UV-Mapping". Repeat, offset-x, offset-y, scalex and scaley properties are exported by baking the result into the UV data of the file, and repeat-x or repeat-y properties currently have no effect.

In the case when tag settings overlap (e.g. if one texture tag assigns a material to a object with repeat set to true, and another texture tag  assigns the same material to another object with repeat set to false) then the exporter will create a duplicate the material in order to assign the correct setings in Away3D.		 


<section id="main5"/>
# 5 Textures
	
The AWD exporter includes all texture objects found in the shader slots of the supported material channels of an exported material. A textures must have a square size equal to a  power of two (4x4, 8x8, 16x16, 32x32 etc) in order to ensure texture are compatible with the renderers in Away3D. If a texture is not a power of 2 in dimensions, the exporter will prompt the user with an error dialog.

All non-transparent textures will be stored as jpg data. Textures containing transparency will be exported as png data.
	
In the exporter GUI you can choose to embed all textures into the awd file which will result in a single file with the jpg/png data stored inside. If this option is not enabled, the exporter will save separate jpg/png files in a local "textures" folder.


<section id="main6"/>
# 6 Animation

Two different kind of animation can be exported to Away3D.

- SkeletonAnimation 
- VertexAnimation

More information about animation is currently under construction, and will be uploaded soon.

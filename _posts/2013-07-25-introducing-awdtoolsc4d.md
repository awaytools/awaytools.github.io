---
layout: post
title : Introducing to AWD-Tools-C4D
category : AwayExtensions
summary: "The AWD-Tools-C4D is the first Away Extension, that is supporting some of the new features of AWD2.1"
tags : [News, Releases]
image : introducing-awdtoolsc4d.jpg
---
{% include JB/setup %}

The AWD-Tools-C4D is the first Away Extension, that is supporting some of the new features of AWD2.1.

While it is still in development, it can already be used to export a C4D-scene into the AWD2.1-Format, including light-setups and animations.


## Content

<nav><ul>
<li><a href="#main1">1. General</a></li>
<li><a href="#main2">2. Supported Objects</a></li>
<li><a href="#main2sub1">2.1 Null-Objects</a></li>
<li><a href="#main2sub2">2.2 Polygon-Objects</a></li>
<li><a href="#main2sub3">2.3 Primitives</a></li>
<li><a href="#main2sub4">2.4 Instance-Objects</a></li>
<li><a href="#main2sub5">2.5 Joint-Objects</a></li>
<li><a href="#main2sub6">2.6 Light-Objects</a></li>
<li><a href="#main2sub7">2.7 LightPicker</a></li>
<li><a href="#main2sub8">2.8 Camera-Objects</a></li>
<li><a href="#main3">3. AWDObjectSettings Tag</a></li>
<li><a href="#main4">4. Materials</a></li>
<li><a href="#main4sub1">	4.1 Texture-Tags</a></li>
<li><a href="#main5">5. Textures</a></li>
<li><a href="#main6">6. Animations</a></li>
</ul></nav>


<section id="main1l"/>
## 1. General


The C4D-scene needs to have been saved before exporting. 
(You do not need to save every scene-change, but the scene must have a valid name and a document-path, and must not be a newly created scene, that has never been saved)

To make shure the plugin will find the pathes to all textures, it is recommented to perform a "Save Project with Assets" before exporting a scene.
("Save Project with Assets" will let you choose a name and a location and will save the project to a new folder, created at the choosen location, named by the given name. All textures, used in the project will be saved to a folder called "tex" next to the saved C4D-project. 
This is a standart C4D-function. For easy access (and as a reminder), the "Save Project with Assets" has been included into the Plugin-Gui.

The C4D layer-system enables to prevent groups of objects from beeing displayed in the scenegraph at all. The exporter will export all objects found inside a C4D-project, regardless of its layer.
To prevent errors on export, its is best not to use the C4D layer-system at all.


<section id="main2"/>

## 2. Supported Objects


Unsupported objects will not be exported.
If a unsupported object is parent of a supported object, it will be exported as a Null-Object (e.g. a Away3d ObjectContainer3d)

Most unsupported object can be converted into polygon-objects in C4D very easy. 
(select a primitive and press "c") 
(right click on hypernurbs and select "current State to object")



<section id="main2sub1"/>
	
### 2.1 Null-Objects	
		
Null Object are exported as ObjectContainer3D.
A NullObject has a name, a transform-matrix and a list of children.
All other scene-objects inherite these three properties.

<section id="main2sub2"/>

### 2.2 Polygon-Objects

All polygon-objects will be triangulated on export.

The point-count of a polygon-object shown in C4D (object-Information), will in most cases not be the point-count of the generated Away3d-geometry.

This is because, in C4D you can have multiple uv-values and multiple normal-vectors for the same point. 
In Away3d a geometry needs to have multiple points (vertices) if you want two have multiple uv-values (uv-seams) or multiple normal-vectors (phong breaks) for the same point-position.
		
In C4D, the phong-tag is used, to define the look of the mesh, regarding phong and phong-breaks.
The exporter will calculate the extra points needed to display the mesh in Away3d.

Since each UV-seam and Phong-Breaks results in duplicated vertices for the same position, you want to minimize them as much as possible (for smaller fileSize).
Spezially when working with animated meshes,  point-count really matters.

In C4D, one polygon can have multiple materials assigned. Only one material per polygon will be exported.
The exported geometry will have one subgeometry for each material that is used in the polygon-object.
Since a subgeometry is restricted in its size (and a polygon-object is not) the exporter might need to create several subgeometries for the same material.

Polygon-objects can be set to display object-colors instead of the assigned materials ("object-color-mode"). The exporter will export a away3d-colormaterial for each object-color that is used.

In C4D, objects can inheritate materials assigned to their parent objects.
The exporter will resolve this material-assignment, so that every mesh is exported with the correct materials assigned directly.

Polygon-objects can be animated. <a href="#main6">Read more information in the animation-chapter.</a>


<section id="main2sub3"/>

### 2.3 Primitives


This C4D-primitves are supported for export:

* Plane
* Sphere
* Cube
* Cylinder
* Cone
* Capsule
* Torus

The up-vector for all exported primitives will be the y-axis (yup = true).



<section id="main2sub4"/>
	
### 2.4 Instance-Objects


To be valid for export, a C4D-instance-object needs to reference a polygon-object, or one of the supported C4D-primitves. 

If the instance-object is set to be a "render-instance", it will use the same "object-color-mode" as the referenced object. Otherwise it will use its own "object-color-mode".
		
If the referenced polygon-object has a material assigned directly, the instance-object will use the same material.

If the referenced polygon-object has no material assigned directly, the instance-object can have  its own material applied (directly or by inheritate).


<section id="main2sub5"/>
### 2.5 Joint-Objects	

To  be exported, a Joint-Object needs to be part of a  AWDSkeleton / AWDSkeletonAnimation. 
Read more information in the animation-chapter


<section id="main2sub6"/>
### 2.6 Light-Objects	
		
Only two types of lights are supported for export.
Point-lights will be exported as Away3d-pointlights, infinite-lights will be exported as C4d-directionallights.

Exportet light-properties:

* Position / Rotation (Direction) 
* Color
* Strength for ambient, specular and diffuse

In Away3d a light-object has a different strength-value for ambient, specular and diffuse light.
In c4d a light has only one strength value, but a checkbox to enable/disable specular, ambient or diffuse light.

* A specular, ambient or diffuse that is disabled, will be exported as strength = 0.

* A specular, ambient or diffuse that is enabled , will be exported with the general-light-strength.

<section id="main2sub7"/>
### 2.7 LightPicker

In C4D each light has a list of objects that can be used to add the light only to specific objects, or to prevent specific objects from being lit by this light.
The exporter will create Away3D-StaticLightPickers so the lighting can be recreated in Away3d.
Since the Away3D-StaticLightPicker is a property of the material, the exporter might need to clone some of the materials (and assign different LightPickers to the clones).


<section id="main2sub8"/>
### 2.8 Cameras

Cameras will be exported. The only exported projection is "Perspective". All other projections will be exported as "Perspective".


<section id="main3"/>
## 3. AWDObjectSettings Tag


Generally its best to clean your C4D-Scene before export, so no unsupported/unnessessary Objects are exported.
For some reasons, you might want to keep objects in your scene, that should not get exported.
Apply a AWDObjectSettingsTag to objects, to keep them from getting exported.
 (Disable the "Export"-option. You can enable the "Apply to Childs"-option, to prevent all childs from getting exported too.)
If you disable the "Export" and the "Apply to childs" and a supported child object is found in the scene, the object that should be excludet from export is exported as a ObjectContainer3d. 


<section id="main4"/>
## 4. Materials


Only the c4d-Standart Material is supported. 

The c4d-Standart Material is made of a list of Channels. 

You can expand this list, but a custom-channel will not be read by the exported.

This channels will be exportet:

* Color-Channel: 
The Color will be exported. 
If the Color-Shader is a BitmapShader  (Texture-File) the material will be exported as a texture-material, and the texture will be exported too.  
All other Shader (like "Layer", "Fresnel", or "SubSurfaceScattering") are not supported.

* Transparenzy-Channel :
The strength of the transparenzy is exported as the alpha property of the material.
No other settings of the transparenzy-Channel are exported.

* Normal-Channel :
Only the normal-texture found in the shader-slot of the normal-channel is exported.
No other settings of the normal-Channel are exported.

* Diffuse Channel :
Only the diffuse-texture found in the shader-slot of the diffuse-channel is exported (as specular-texture).
No other settings of the normal-Channel are exported.

In C4D most material-channels containing a shader-slot. This slot (or LinkBox) can contain other shaders than bitmap-shader (e.g. Noise, Fresnell, Layer, etc). Only Bitmap-shader is supported for export.


<section id="main4sub1"/>
### 4.1 Texture Tags:
	
In C4D materials are assigned to objects by a texture tag.

if you assign two materials to the same polygon, only the material that is assigned by the texturetag that appears most right in the object-manager is exported.

Only supported projection-Mode for texture-tags is "UV-Mapping"

Repeat, offset-x, offset-y, scalex and scaley properties are exporter (gets baked into the UV-Data), but you cannot use repeat-x or repeat-y.

If one texture-tag assigns a material to a object with repeat=true, and another texture-tag  assigns the same material to another object with repeat=false, 
the exporter will have to duplicate the material, so the scene can be reconstructed in away3d.		 


<section id="main5"/>
## 5 Textures
	
The exporter exports all textures found in the shader-slots of the supportet material-channels of a exported material.

A textures must have a size of power of two, or the user is prompted by a error-dialog.

All textures will be stored as jpg-data, or,  if they contain a transparentzy channel, as png-data.
	
You can choose to embed all textures into the awd-file (the jpg/png data will be stored directly in the file), 
or to use them as external files (the exporter saves jpg/png-files).




<section id="main6"/>
## 6 Animation

Two different kind of animation can be exported to Away3d.
* SkeletonAnimation 
* VertexAnimation

More information about animation is currently under construction, and will be uploaded soon.

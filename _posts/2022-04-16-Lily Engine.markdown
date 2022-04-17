---
title:  "Lily Engine"
date:   2022-04-16 01:29:23
categories: []
tags: []
---
An open source 3D game engine that I develop in my free time. Uses OpenGL and [Simple DirectMedia Layer][SDL] to render a scene hierarchy of entities and their components.

![image](/images/LilyScrShot.jpg)

(A sample scene showing meshes being rendered in the scene hierarchy)

This project was initially designed to help me learn and get comfortable with graphics programming concepts, but over it's development I've had to become familiar with other aspects of large software architecture.

The renderer uses OpenGL, and was the starting point of the project. Initially the repository for Lily was a fork of a friends university graphics project that was used as a playground for
me to learn a graphics API. As time went on the original code is entirely replaced with more modular game engine code.

Every Scene utilizes an Entity-Component-System (ECS) that was built from scratch to provide data locality which improves frame time. [ECS Wikipedia Page][ECS] I'm still working on testing
if my implementation is any faster than a traditional object-oriented approach. Right now the plan is to make my ECS it's own separate project.

A long detour was spent deciding how the engine should serialize and deserialize data. My first instinct was to look at c++ implementations of JSON, but I soon realized that larger
file sizes were much slower as plain text. I think this is an area worth being careful with, as load times are quite important in any game engine. The current
workaround is using Open Asset Import library to export and import the models loaded into the engine as binary data, while basic scene structure is still saved in JSON format. This is all subject to change.

The GUI is meant to be minimal and simple--I'm using ImGui to help me achieve that. It is fast and responsive, and customizable to the extent that I need it to be.


[Source Code][lily]

[Download][release]

[lily]: https://github.com/erikrramsey/Lily
[release]: https://github.com/erikrramsey/Lily/releases
[ECS]: https://en.wikipedia.org/wiki/Entity_component_system
[SDL]: https://www.libsdl.org/

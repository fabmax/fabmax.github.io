---
layout: default
title: Demos
nav_order: 2
---

# kool Demos
{: .fs-9 }

The following demos demonstrate various features of the engine. All demos run in the browser as well as on Desktop JVM.
{: .fs-6 .fw-300 }

---

## kool Demos

- [Editor](https://fabmax.github.io/kool/kool-editor/): Work in progress graphical editor for this engine. Fully
  implemented within the engine itself. 
- [Island](https://fabmax.github.io/kool/kool-js/?demo=phys-terrain): Height-map based
  island incl. some wind-affected vegetation + a basic controllable character.
- [Physics - Ragdoll](https://fabmax.github.io/kool/kool-js/?demo=phys-ragdoll): Ragdoll physics demo.
- [Physics - Vehicle](https://fabmax.github.io/kool/kool-js/?demo=phys-vehicle): A drivable vehicle (W, A, S, D /
  cursor keys, R to reset) based on the Nvidia PhysX vehicles SDK.
- [Physics - Joints](https://fabmax.github.io/kool/kool-js/?demo=phys-joints): Physics demo consisting of a chain
  running over two gears. Uses a lot of multi shapes and revolute joints.
- [Physics - Collision](https://fabmax.github.io/kool/kool-js/?demo=physics): The obligatory collision physics demo with
  various different shapes.
- [Embedded UI](https://fabmax.github.io/kool/kool-js/?demo=ui): Integrated UI framework implemented completely within
  the engine. Fast, highly customizable and easy-to-use.
- [Particles](https://fabmax.github.io/kool/kool-js/?demo=bees): Two teams of bees fighting against each other.
  Simulation can be toggled between CPU and compute-shader (if available, i.e. on WebGPU).
- [Fluffy Bunny](https://fabmax.github.io/kool/kool-js/?demo=shell): Shell-shading based rendering of animated fur
  (based on this [video](https://www.youtube.com/watch?v=9dr-tRQzij4)).
- [Creative Coding](https://fabmax.github.io/kool/kool-js/?demo=creative-coding): A few relatively simple demos
  showcasing different techniques of generating procedural geometry.
- [Procedural Geometry](https://fabmax.github.io/kool/kool-js/?demo=procedural): Small test-case for
  procedural geometry; all geometry is generated in code (even the roses! Textures are regular images though). Also,
  some glass shading (shaft of the wine glass, the wine itself looks quite odd when shaded with refractions and is
  therefore opaque).
- [glTF Models](https://fabmax.github.io/kool/kool-js/?demo=gltf): Various demo models loaded from glTF / glb format
  - Flight Helmet from [glTF sample models](https://github.com/KhronosGroup/glTF-Sample-Models/tree/master/2.0/FlightHelmet)
  - Polly from [Blender](https://github.com/KhronosGroup/glTF-Blender-Exporter/tree/master/polly)
  - Coffee Cart from [Poly Haven](https://polyhaven.com/a/CoffeeCart_01)
  - Camera Model also from [Poly Haven](https://polyhaven.com/a/CoffeeCart_01)
  - A few feature test models also from the [glTF sample model repository](https://github.com/KhronosGroup/glTF-Sample-Models/tree/master/2.0)
- [Deferred Shading](https://fabmax.github.io/kool/kool-js/?demo=deferred): Thousands of dynamic
  light sources, bloom and ambient occlusion.
- [Screen-space Ambient Occlusion](https://fabmax.github.io/kool/kool-js/?demo=ao): Roughly based on
  [this](http://john-chapman-graphics.blogspot.com/2013/01/ssao-tutorial.html) article by John
  Chapman with slightly optimized sampling (also shamelessly recreated his demo scene).
- [Screen-space Reflections](https://fabmax.github.io/kool/kool-js/?demo=ssr): A simple PBR shaded
  model with screen-space reflections and up to four spot-lights with dynamic shadows.
- [Physical Based Rendering](https://fabmax.github.io/kool/kool-js/?demo=pbr): Interactive PBR demo 
  with image based lighting for various materials and environments (underlying PBR theory from
  [this](https://learnopengl.com/PBR/Theory) awesome article series).
- [Instanced / LOD Drawing](https://fabmax.github.io/kool/kool-js/?demo=instance): Instanced rendering
  demo of the Stanford Bunny. Uses six levels of detail to render up to 8000 instances.
- [Mesh Simplification](https://fabmax.github.io/kool/kool-js/?demo=simplification): Interactive mesh
  simplification demo (based on traditional [error-quadrics](https://www.cs.cmu.edu/~./garland/Papers/quadrics.pdf))

Code for all demos is available in `kool-demo` sub-project in the [kool repo][kool repo].

----

[kool repo]: https://github.com/fabmax/kool
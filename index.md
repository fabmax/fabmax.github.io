# Welcome to my Github page!

## kool Demos

Here are a few demos I made with my 3D engine. All code (engine + demos) is available on github: [https://github.com/fabmax/kool](https://github.com/fabmax/kool)

- [Physics - Vehicle](https://fabmax.github.io/kool/kool-js/?demo=phys-vehicle): A drivable vehicle (W, A, S, D) 
  based on the nVidia PhysX vehicles SDK (via emscripten/WebIDL bindings:
  [physx-js-webidl](https://github.com/fabmax/physx-js-webidl)). Still work in progress and currently does not work
  on JVM.
- [Physics - Joints](https://fabmax.github.io/kool/kool-js/?demo=phys-joints): Physics demo consisting of a chain
  running over two gears. Uses a lot of multi / compound shapes and revolute / hinge joints. Based on nVidia
  PhysX on javascript / [JBullet](http://jbullet.advel.cz/) on JVM). 
- [Physics - Collision](https://fabmax.github.io/kool/kool-js/?demo=physics): The obligatory box collision physics demo.
- [Atmospheric Scattering](https://fabmax.github.io/kool/kool-js/?demo=atmosphere): Earth (and Moon) with volumetric atmosphere.
  Lots of interactive controls for adjusting the appearance of the atmosphere. The planet itself is rendered by a highly customized
  deferred pbr shader with extensions for rendering the oceans and night side.
- [Procedural Geometry](https://fabmax.github.io/kool/kool-js/?demo=procedural): Small test-case for
  procedural geometry; all geometry is generated in code (even the roses! Textures are regular images though). Also some glass
  shading (shaft of the wine glass, the wine itself looks quite odd when shaded with refractions and is therefore opaque)
- [glTF Models](https://fabmax.github.io/kool/kool-js/?demo=gltf): Various demo models loaded from glTF / glb format
  - Flight Helmet from [glTF sample models](https://github.com/KhronosGroup/glTF-Sample-Models/tree/master/2.0/FlightHelmet)
  - Polly from [Blender](https://github.com/KhronosGroup/glTF-Blender-Exporter/tree/master/polly)
  - Coffee Cart from [3D Model Haven]((https://3dmodelhaven.com/model/?c=appliances&m=CoffeeCart_01))
  - Camera Model also from [3D Model Haven](https://3dmodelhaven.com/model/?c=appliances&m=CoffeeCart_01)
  - A few feature test models also from the [glTF sample model repository](https://github.com/KhronosGroup/glTF-Sample-Models/tree/master/2.0)
- [Deferred Shading](https://fabmax.github.io/kool/kool-js/?demo=deferred): Handles thousands of dynamic
  light sources - also includes PBR shading and ambient occlusion.
- [Screen-space Ambient Occlusion](https://fabmax.github.io/kool/kool-js/?demo=ao): Roughly based on
  [this](http://john-chapman-graphics.blogspot.com/2013/01/ssao-tutorial.html) article by John
  Chapman with slightly optimized sampling (also shamelessly recreated his demo scene).
- [Screen-space Reflections](https://fabmax.github.io/kool/kool-js/?demo=ssr): A simple PBR shaded
  model with screen-space reflections and up to four spot lights with dynamic shadows.
- [Physical Based Rendering](https://fabmax.github.io/kool/kool-js/?demo=pbr): Interactive PBR demo 
  with image based lighting for various materials and environments (underlying PBR theory from
  [this](https://learnopengl.com/PBR/Theory) awesome article series).
- [Procedural Tree](https://fabmax.github.io/kool/kool-js/?demo=tree): A simple procedural tree generator
  based on a [space colonization algorithm](http://algorithmicbotany.org/papers/colonization.egwnp2007.large.pdf)
- [Instanced / LOD Drawing](https://fabmax.github.io/kool/kool-js/?demo=instance): Instanced rendering
  demo of the Stanford Bunny. Uses six levels of detail to render up to 8000 instances.
- [Mesh Simplification](https://fabmax.github.io/kool/kool-js/?demo=simplification): Interactive mesh
  simplification demo (based on traditional [error quadrics](https://www.cs.cmu.edu/~./garland/Papers/quadrics.pdf))

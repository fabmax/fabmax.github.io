---
layout: default
title: Shading
---

# Shading
{: .fs-9 .no_toc }

kool comes with a set of general purpose shaders as well as its own shading language to write custom shaders.
{: .fs-6 .fw-300 }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Builtin shaders

Builtin shaders provide easy-to-use masterials suitable for most standard use-cases.

{: .note }
All builtin shaders are written in [KSL](#ksl---kool-shading-language), the same DSL you can use to write your own custom shaders.

{: .note }
> Documentation is still very basic. Most notably, `KslPbrShader` and `KslBlinnPhongShader`
> share a lot of light-related settings, which are not further described here. This will hopefully
> change soon.

### KslPbrShader

[`KslPbrShader`][KslPbrShader] provides a general purpose shader for lit materials following the
[physcical based rendering][PBR theory] (PBR) approach. PBR shaders
try to approximate the physical properties of real materials more closely than older shading
techniques like, e.g., Blinn-Phong shading. This typically results in a more realistic look
of rendered objects. On the downside PBR shading is quite a bit more expensive than simpler
shading models. So, in case you are targeting low-end and / or mobile devices, you should consider
using a [Blinn-Phong shader](#kslblinnphongshader) instead.

kool's PBR shader follows the metallic workflow, meaning it has two basic material properties:

- **Roughness**: A value ranging from 0 (very smooth) to 1 (very rough).
- **Metallic**: A value ranging from 0 (dielectric, i.e. non-metallic, e.g. plastic) to 1 (pure metal).

To assign a PBR shader to a mesh you can use the corresponding constructor function:

```kotlin
mesh.shader = KslPbrShader {
    color { /* color config */ }

    // Use constant roughness / metallic values
    metallic(0f)
    roughness(0.5f)

    // or use textures providing the roughness / metallic values
    roughness { textureProperty(materialRoughnessMap) }
    // You can also use a uniform property, which allows changing the property
    // after shader construction
    metallic { uniformProperty(1f) }

    // Optionally, you can set additional settings
    normalMapping { setNormalMap(materialNormalMap) }
    shadow { addShadowMap(someShadowMap) }
    ao {
        materialAo { textureProperty(materialAoMap) }
        enableSsao(sceneSpaceAoMap)
    }
}
```

### KslBlinnPhongShader

[`KslBlinnPhongShader`][KslBlinnPhongShader] provides a general purpose shader for lit materials following the
traditional [Blinn-Phong][Blinn-Phon theory] method. It is less sophisticated than PBR shading but quite a bit
faster making it more suitable for low-end and / or mobile devices.

`KslBlinnPhongShader` has three specific material properties:

- **Shininess**: A value ranging from 0 to infinity, describing how shiny the surface is.
- **Specular strength**: A multiplier (typically ranging from 0 to 1) affecting the strength of the specular lighting term.
- **Specular color**: A color value, which is multiplied to the specular lighting term (white by default).

Assigning a Blinn-Phong shader works similar to PBR shaders:

```kotlin
mesh.shader = KslBlinnPhongShader {
    color { /* color config */ }

    // Use constant roughness / metallic values
    shininess(50f)
    specularStrength(1f)

    // or use textures providing the roughness / metallic values
    shininess { textureProperty(materialShinessMap) }
    // You can also use a uniform property, which allows changing the property
    // after shader construction
    specularStrength { uniformProperty(1f) }

    // Optionally, you can set additional settings
    normalMapping { setNormalMap(materialNormalMap) }
    shadow { addShadowMap(someShadowMap) }
    ao {
        materialAo { textureProperty(materialAoMap) }
        enableSsao(sceneSpaceAoMap)
    }
}
```

### KslUnlitShader

[`KslUnlitShader`][KslUnlitShader] is a general purpose shader, that does not incorporate any lighting model.
Instead, the material source color (texture or vertex / instance / uniform property) is forwarded more or less
unmodified by the fragment shader (apart from optional color-space conversion).

Unlit shaders are typically used for UI overlays, or stuff like navigation grids, wireframes etc.

Assigning an unlit shader works similar to lit shaders. Since there are no light-related properties, you typically
only set the color source:

```kotlin
mesh.shader = KslUnlitShader {
    color { /* color config */ }
}
```

## KSL - kool shading language

{: .warning }
KSL is quite powerful and offers pretty much the same feature set as GLSL, although the syntax is sometimes a
bit more complicated. However, documentation is still very much incomplete. In case you want to dive deep you
should take a look at the source code of the builtin shaders, to get an idea about how things work.

Here's a minimal example for a custom KSL shader:

```kotlin
mesh.shader = KslShader("Hello world shader") {
    val interStageColor = interStageFloat4()
    vertexStage {
        main {
            val mvp = mvpMatrix()
            val localPosition = float3Var(vertexAttribFloat3(Attribute.POSITIONS))
            outPosition set mvp.matrix * float4Value(localPosition, 1f.const)
            interStageColor.input set vertexAttribFloat4(Attribute.COLORS)
        }
    }
    fragmentStage {
        main {
            colorOutput(interStageColor.output)
        }
    }
}
```

If you ever wrote a shader before the structure should be familiar: The shader consists of a vertex
stage (responsible for projecting the individual mesh vertices onto the screen) and a fragment stage (responsible
for computing the output-color for each pixel covered by the mesh). This example shader is almost as simple as a valid
shader can be: It uses a pre-multiplied MVP matrix to project the vertex position attribute to the screen. Moreover,
the color attribute is taken from the vertex input and forwarded to the fragment shader via `interStageColor`. The
fragment stage then simply takes the color from `interStageColor` and writes it to the screen.

A little more complex example is available in the [HelloKsl] demo.

## Deferred shading

{: .warning }
The deferred rendering pipeline is somewhat deprecated at the moment and will probably change significantly
in the future. Documentation is therefore very limited.

So far, all discussed shaders use traditional forward rendering. Another option to do the rendering is deferred
shading which can be cheaper and allows for more advanced lighting effects.

To use deferred shading, you need to use an appropriate shader. Currently, the only builtin option is [`DeferredKslPbrShader`][DeferredKslPbrShader], which has mostly the same configuration options like the
forward-rendering version described [above](#kslpbrshader).

Examples using deferred shading are [DeferredDemo], [ReflectionDemo] and the
[VehicleDemo]

----

[KslPbrShader]: https://github.com/fabmax/kool/blob/main/kool-core/src/commonMain/kotlin/de/fabmax/kool/modules/ksl/KslPbrShader.kt
[PBR theory]: https://learnopengl.com/PBR/Theory
[KslBlinnPhongShader]: https://github.com/fabmax/kool/blob/main/kool-core/src/commonMain/kotlin/de/fabmax/kool/modules/ksl/KslBlinnPhongShader.kt
[Blinn-Phon theory]: https://en.wikipedia.org/wiki/Blinn%E2%80%93Phong_reflection_model
[DeferredKslPbrShader]: https://github.com/fabmax/kool/blob/main/kool-core/src/commonMain/kotlin/de/fabmax/kool/pipeline/deferred/DeferredPbrShader.kt
[KslUnlitShader]: https://github.com/fabmax/kool/blob/main/kool-core/src/commonMain/kotlin/de/fabmax/kool/modules/ksl/KslUnlitShader.kt
[HelloKsl]: https://github.com/fabmax/kool/blob/main/kool-demo/src/commonMain/kotlin/de/fabmax/kool/demo/helloworld/HelloKsl.kt
[DeferredDemo]: https://github.com/fabmax/kool/blob/main/kool-demo/src/commonMain/kotlin/de/fabmax/kool/demo/DeferredDemo.kt
[ReflectionDemo]: https://github.com/fabmax/kool/blob/main/kool-demo/src/commonMain/kotlin/de/fabmax/kool/demo/ReflectionDemo.kt
[VehicleDemo]: https://github.com/fabmax/kool/tree/main/kool-demo/src/commonMain/kotlin/de/fabmax/kool/demo/physics/vehicle
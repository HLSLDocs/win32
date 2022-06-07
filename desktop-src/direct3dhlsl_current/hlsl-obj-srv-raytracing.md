# SRV (Shader Resource View) Raytracing

Shader resource views typically wrap textures in a format that the shaders can access them.

Wrapping a single texture is probably the simplest form of shader resource view. More complex examples would be a collection of subresources (individual arrays, planes, or colors from a mipmapped texture), 3D textures, 1D texture color gradients, and so on.

Shader resource views are for read only use (which is the most common use of resources).

## RaytracingAccelerationStructure

The acceleration structure is an object that represents a full 3D environment in a format optimal for traversal by the GPU.  Represented as a two-level hierarchy, the structure affords both optimized ray traversal by the GPU, as well as efficient modification by the application for dynamic objects.

The first step in rendering any content using DXR is to build the acceleration structures.

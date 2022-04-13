# Built-in Structures

## Raytracing

### Call parameter structure

A user-defined structure provided as an inout argument to a [**CallShader**](callshader-function.md) call, and as an inout parameter for the [callable shader](callable-shader.md). The structure type used in the callable shader must match the structure provided to the corresponding **CallShader** call.

### Intersection attributes structure 

A structure declared in HLSL to represent hit attributes for fixed-function triangle intersection or axis-aligned bounding box for procedural primitive intersection.

#### Fixed-function triangle intersection

The following structure is declared in HLSL to represent hit attributes for fixed-function triangle intersection:


```
struct BuiltInTriangleIntersectionAttributes
{
    float2 barycentrics;
};
```

[Any hit](any-hit-shader.md) and [closest hit](closest-hit-shader.md) shaders invoked using fixed-function triangle intersection must use this structure for hit attributes. Given attributes a0, a1 and a2 for the 3 vertices of a triangle, barycentrics.x is the weight for a1 and barycentrics.y is the weight for a2.  For example, the app can interpolate by doing:  a = a0 + barycentrics.x * (a1-a0) + barycentrics.y* (a2 – a0).

#### Axis-aligned bounding box for procedural primitive intersection

When axis-aligned bounding boxes are used for intersection with procedural primitives, an intersection shader is triggered.  That shader provides a user-defined intersection attribute structure to the [**ReportHit**](reporthit-function.md) call.  The any hit and closest hit shaders bound in the same hit group with this intersection shader must use the same structure for hit attributes, even if the attributes are not referenced.  The maximum attribute structure size is 32 bytes, defined as **D3D12\_RAYTRACING\_MAX\_ATTRIBUTE\_SIZE\_IN\_BYTES**.

### Ray payload structure 

A user-defined structure that is provided as an inout argument in a [**TraceRay**](traceray-function.md) call, and as an inout parameter in the shader types that may access the ray payload, which include [any hit](any-hit-shader.md), [closest hit](closest-hit-shader.md), and [miss](miss-shader.md) shaders. Any shaders that access the ray payload must use the same structure as the one provided at the originating **TraceRay** call.  Even if one of these shaders doesn’t reference the ray payload at all, it still must specify the matching payload as the originating **TraceRay** call.

### RayDesc structure

Passed to the [**TraceRay**](traceray-function.md) function to define the origin, direction, and extents of the ray.

#### Syntax


```
struct RayDesc
{
    float3 Origin;
    float  TMin;
    float3 Direction;
    float  TMax;
};

```



#### Fields

<dl> <dt>

<span id="Origin"></span><span id="origin"></span>**Origin**
</dt> <dd>

The origin of the ray.

</dd> <dt>

<span id="TMin"></span><span id="tmin"></span>**TMin**
</dt> <dd>

The minimum extent of the ray.


</dd> <dt>

<span id="Direction"></span><span id="direction"></span>**Direction**
</dt> <dd>

The direction of the ray.


</dd> <dt>

<span id="TMax"></span><span id="tmax"></span>**TMax**
</dt> <dd>

The maximum extent of the ray.


</dd>
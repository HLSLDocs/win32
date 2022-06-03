# Built-in Structures

Built-in structures are reserved [`structs`](hlsl-language-type-struct.md) for use in advanced features. 

## Raytracing

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

### RayDesc structure

Passed to the [**TraceRay**](hlsl-built-ins-functions_raytracing.md#traceray-function) function to define the origin, direction, and extents of the ray.

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
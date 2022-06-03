# Raytracing

### AcceptHitAndEndSearch function

Used in an [any hit shader](any-hit-shader.md) to commit the current hit and then stop searching for more hits for the ray. If there is an intersection shader running, it's execution stops.  Execution passes to the [closest hit shader](closest-hit-shader.md), if enabled, with the closest hit recorded so far.

#### Syntax

```
void AcceptHitAndEndSearch();
```




#### Return Value

**void**

#### Remarks

This function can be called from the following raytracing shader types:

* [**Callable Shader**](callable-shader.md)
* [**Closest Hit Shader**](closest-hit-shader.md)
* [**Miss Shader**](miss-shader.md)
* [**Ray Generation Shader**](ray-generation-shader.md)

### CallShader function

Invokes another shader from within a shader.

#### Syntax
This intrinsic function definition is equivalent to the following function template:

```
template<param_t>
void CallShader(uint ShaderIndex, inout param_t Parameter);
```



#### Parameters

`ShaderIndex`

An unsigned integer representing the index into the [callable shader](callable-shader.md) table specified in the call to [**DispatchRays**](/windows/desktop/api/d3d12/nf-d3d12-id3d12graphicscommandlist4-dispatchrays.

`Parameter`

The user-defined parameters to pass to the callable shader.  This parameter structure must match the parameter structure used in the callable shader pointed to in the shader table.


#### Return Value

**void**

#### Remarks

This function can be called from the following raytracing shader types:

* [**Callable Shader**](callable-shader.md)
* [**Closest Hit Shader**](closest-hit-shader.md)
* [**Miss Shader**](miss-shader.md)
* [**Ray Generation Shader**](ray-generation-shader.md)

### IgnoreHit function

Called from an [any hit shader](any-hit-shader.md) to reject the hit and end the shader. The hit search continues on without committing the distance and attributes for the current hit.  The [**ReportHit**](reporthit-function.md) call in the [intersection shader](intersection-shader.md), if there is one, will return false.  Any modifications made to the ray payload up to this point in the any hit shader are preserved.

#### Syntax

```
void IgnoreHit();

```


#### Return Value

**void**

#### Remarks

This function can be called from the following raytracing shader types:

* [**Any Hit Shader**](any-hit-shader.md)

### ReportHit function

Called by an [intersection shader](intersection-shader.md) to report a ray intersection.

#### Syntax
This intrinsic function definition is equivalent to the following function template:

```
template<attr_t>
bool ReportHit(float THit, uint HitKind, attr_t Attributes);
```



#### Parameters

`THit`

A float value specifying the parametric distance of the intersection..

`HitKind`

An unsigned integer that identifies the type of hit that occurred.  This is a user-specified value in the range of 0-127.  The value can be read by [any hit](any-hit-shader.md) or [closest hit](closest-hit-shader.md) shaders with the **HitKind** intrinsic.

`Attributes`

The user-defined [**Intersection Attribute Structure**](intersection-attributes.md) structure specifying the intersection attributes.  

#### Return Value

**bool** True if the hit was accepted.  A hit is rejected if *THit* is outside the current ray interval, or the any hit shader calls [**IgnoreHit**](ignorehit-function.md).  The current ray interval is defined by **RayTMin** and **RayTCurrent**.

#### Remarks

This function can be called from the following raytracing shader types:

* [**Intersection Shader**](intersection-shader.md)

### TraceRay function

Sends a ray into a search for hits in an acceleration structure.

#### Syntax
This intrinsic function definition is equivalent to the following function template:

```
Template<payload_t>
void TraceRay(RaytracingAccelerationStructure AccelerationStructure,
              uint RayFlags,
              uint InstanceInclusionMask,
              uint RayContributionToHitGroupIndex,
              uint MultiplierForGeometryContributionToHitGroupIndex,
              uint MissShaderIndex,
              RayDesc Ray,
              inout payload_t Payload);

```



#### Parameters

`AccelerationStructure`

The top-level acceleration structure to use. Specifying a NULL acceleration structure forces a miss.

`RayFlags`

Valid combination of [ray_flag](ray_flag.md) values. Only defined ray flags are propagated by the system, i.e. are visible to the [RayFlags](rayflags.md) shader intrinsic.

`InstanceInclusionMask`

An unsigned integer, the bottom 8 bits of which are used to include or reject geometry instances based on the InstanceMask in each instance. For example:
```
if(!((InstanceInclusionMask & InstanceMask) & 0xff)) { //ignore intersection }
```

`RayContributionToHitGroupIndex`

An unsigned integer specifying the offset to add into addressing calculations within shader tables for hit group indexing.  Only the bottom 4 bits of this value are used.

`MultiplierForGeometryContributionToHitGroupIndex`

An unsigned integer specifying the stride to multiply by *GeometryContributionToHitGroupIndex*, which is just the 0 based index the geometry was supplied by the app into its bottom-level acceleration structure. Only the bottom 16 bits of this multiplier value are used.

`MissShaderIndex`

An unsigned integer specifying the index of the miss shader within a shader table.

`Ray`

A [**RayDesc**](raydesc.md) representing the ray to be traced.

`Payload`

A user defined ray payload accessed both for both input and output by shaders invoked during raytracing.  After [**TraceRay**](traceray-function.md) completes, the caller can access the payload as well.

#### Return Value

**void**

#### Remarks

This function can be called from the following raytracing shader types:

* [**Closest Hit Shader**](closest-hit-shader.md)
* [**Miss Shader**](miss-shader.md)
* [**Ray Generation Shader**](ray-generation-shader.md)
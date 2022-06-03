# Built-in Semantics

Built-in semantics are reserved [`semantic`](hlsl-language-semantics.md) values to describe [`variables`](hlsl-language-variables.md).

>**Note** The semantic COLOR isn't supported on DXC by default. When writing new HLSL shaders targeting DXC, you should instead use [SV_Target](https://docs.microsoft.com/windows/desktop/direct3dhlsl/dx-graphics-hlsl-semantics#migration-from-direct3d-9-to-direct3d-10-and-later). However, DXC also provides an option to compile shaders referencing the COLOR semantic by passing it the `-Gec` flag. For example, the following HLSL code should compile successfully on DXC when the `-Gec` flag is used.

>**Note** ```C++
float main() : COLOR
{
    return 1.f;
}
```

## System Value Semantics

### SV\_InnerCoverage

SV\_InputCoverage represents underestimated conservative rasterization information (i.e. whether a pixel is guaranteed-to-be-fully covered).

#### Type



| Type     |
|------|
| uint |



 

#### Remarks

This system generated value is required for tier 3 support, and is only available in that tier. This input is mutually exclusive with SV\_Coverage - both cannot be used.

To access SV\_InnerCoverage, it must be declared as a single component out of one of the pixel shader input registers. The interpolation mode on the declaration must be constant (interpolation does not apply).

Conservative rasterization is available in both D3D11.3 and D3D12. Refer to:

-   [D3D11.3 Conservative Rasterization](/windows/desktop/direct3d11/conservative-rasterization)
-   [D3D12 Conservative Rasterization](/windows/desktop/direct3d12/conservative-rasterization)


### SV\_StencilRef

SV\_StencilRef represents the current pixel shader stencil reference value.

#### Type



| Type     |
|------|
| uint |



 

#### Remarks

Specifying the shader reference value in the pixel shader is available in both D3D11.3 and D3D12. Refer to:

-   [D3D11.3 Shader Specified Stencil Reference Value](/windows/desktop/direct3d11/shader-specified-stencil-reference-value)
-   [D3D12 Shader Specified Stencil Reference Value](/windows/desktop/direct3d12/shader-specified-stencil-reference-value)


### SV\_DispatchThreadID

Indices for which combined thread and thread group a compute shader is executing in. SV\_DispatchThreadID is the sum of SV\_GroupID \* numthreads and GroupThreadID. It varies across the range specified in [**Dispatch**](/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-dispatch) and [numthreads](sm5-attributes-numthreads.md). For example if Dispatch(2,2,2) is called on a compute shader with numthreads(3,3,3) SV\_DispatchThreadID will have a range of 0..5 for each dimension.

#### Type



| Type      |
|-------|
| uint3 |



 

#### Remarks

This system value is optional.

The following illustration shows the relationship between the parameters passed to [**Dispatch**](/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-dispatch), Dispatch(5,3,2), the values specified in the [numthreads](sm5-attributes-numthreads.md) attribute, numthreads(10,8,3), and values that will passed to the compute shader for the thread-related system values ([SV\_GroupIndex](sv-groupindex.md),SV\_DispatchThreadID,[SV\_GroupThreadID](sv-groupthreadid.md),[SV\_GroupID](sv-groupid.md)).

![illustration of the relationship between dispatch, thread groups, and threads](images/threadgroupids.png)

### SV\_DomainLocation

Defines the location on the hull of the current domain point being evaluated.

#### Type



| Type       | Input topology               |
|--------|----------------|
| float2 | quad patch     |
| float3 | tri patch      |
| float2 | isoline        |



 

#### Remarks

This system value is required.

### SV\_GroupID

Indices for which thread group a compute shader is executing in. The indices are to the whole group and not an individual thread. Possible values vary across the range passed as parameters to [**Dispatch**](/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-dispatch). For example calling Dispatch(2,1,1) results in possible values of 0,0,0 and 1,0,0.

Defines the group offset within a [**Dispatch**](/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-dispatch) call, per dimension of the dispatch call.

#### Type



| Type      |
|-------|
| uint3 |



 

#### Remarks

This system value is optional.

The following illustration shows the relationship between the parameters passed to [**Dispatch**](/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-dispatch), Dispatch(5,3,2), the values specified in the [numthreads](sm5-attributes-numthreads.md) attribute, numthreads(10,8,3), and values that will passed to the compute shader for the thread-related system values ([SV\_GroupIndex](sv-groupindex.md),[SV\_DispatchThreadID](sv-dispatchthreadid.md),[SV\_GroupThreadID](sv-groupthreadid.md),SV\_GroupID).

![illustration of the relationship between dispatch, thread groups, and threads](images/threadgroupids.png)

### SV\_GroupIndex

The "flattened" index of a compute shader thread within a thread group, which turns the multi-dimensional SV\_GroupThreadID into a 1D value. SV\_GroupIndex varies from 0 to (numthreadsX \* numthreadsY \* numThreadsZ) – 1.

#### Type



| Type |
|------|
| uint |



 

#### Remarks


```
SV_GroupIndex = SV_GroupThreadID.z*dimx*dimy + 
                      SV_GroupThreadID.y*dimx + 
                      SV_GroupThreadID.x
```



where dimx and dimy are the dimensions specified in the [numthreads](sm5-attributes-numthreads.md) attribute for the entry point.

This system value is optional. However, its use ensures that a thread only writes to its assigned region of memory in the groupshared variable.

The following illustration shows the relationship between the parameters passed to [**ID3D11DeviceContext::Dispatch**](/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-dispatch), Dispatch(5,3,2), the values specified in the [numthreads](sm5-attributes-numthreads.md) attribute, numthreads(10,8,3), and values that will passed to the compute shader for the thread-related system values (SV\_GroupIndex,[SV\_DispatchThreadID](sv-dispatchthreadid.md),[SV\_GroupThreadID](sv-groupthreadid.md),[SV\_GroupID](sv-groupid.md)).

![illustration of the relationship between dispatch, thread groups, and threads](images/threadgroupids.png)

### SV\_GroupThreadID

Indices for which an individual thread within a thread group a compute shader is executing in. SV\_GroupThreadID varies across the range specified for the compute shader in the [numthreads](sm5-attributes-numthreads.md) attribute. For example if numthreads(3,2,1) was specified possible values for the SV\_GroupThreadID input value have this range of values (0-2,0-1,0).

#### Type



| Type      |
|-------|
| uint3 |



 

#### Remarks

This system value is optional, and is always within the bounds of the values passed into the [numthreads](sm5-attributes-numthreads.md) attribute.

The following illustration shows the relationship between the parameters passed to [**Dispatch**](/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-dispatch), Dispatch(5,3,2), the values specified in the [numthreads](sm5-attributes-numthreads.md) attribute, numthreads(10,8,3), and values that will passed to the compute shader for the thread-related system values ([SV\_GroupIndex](sv-groupindex.md),[SV\_DispatchThreadID](sv-dispatchthreadid.md),SV\_GroupThreadID,[SV\_GroupID](sv-groupid.md)).

![illustration of the relationship between dispatch, thread groups, and threads](images/threadgroupids.png)

### SV\_GSInstanceID

Defines the [instance](sm5-attributes-instance.md) of the geometry shader.

#### Type



| Type     |
|------|
| uint |



 

#### Remarks

This system value is optional.

### SV\_InsideTessFactor

Defines the tessellation amount within a patch surface.

#### Type



|  Type          | Input topology               |
|------------|----------------|
| float\[2\] | quad patch     |
| float      | tri patch      |
| unused     | isoline        |



 

Tessellation factors must be declared as array; they cannot be packed into a single vector.

#### Remarks

This value must be defined during the patch constant function of the hull shader.

Required output value for the hull shader if using quad or tri patches. This value is a required input for the domain shader in order for hardware to match the signatures through the tessellator.

### SV\_OutputControlPointID

Defines the index of the control point ID being operated on by an invocation of the main entry point of the hull shader.

#### Type



| Type     |
|------|
| uint |



 

#### Remarks

This system value is optional.

### SV_ViewID

Graphics shaders in shader model 6.1+ can input unsigned 32-bit integer system value SV_ViewID identifying the current view.  These inputs don't appear in shader input or output signatures for the purpose of shader linkage, and shaders can't output them (as system values).  

If a shader references SV_ViewID, that reference and its dependencies logically/implicitly become instanced by ViewInstanceCount.   

If the Pixel Shader inputs SV_ViewID, one of the input vertex data scalars is reserved (taken away from the amount of data the application can put in its vertices) to allow some implementations to pass the SV_ViewID through vertex data.  Applications don't need to bother outputting SV_ViewID to the Pixel Shader from the upstream shader – only the implementations that need to will do it.

SV_ViewID is mapped to the dx.op.viewID() intrinsic in DXIL. 

#### View Dependent Vertex Storage 

Any shader output that is a function of SV_ViewID implicitly costs scalars contributing, subject to signature packing constraints, towards the 128 scalar limit on vertex size between any two shader stages.  This limit is enforced for uniformity. 

There is nothing the application has to indicate in its shader output declaration about which attributes are view dependent.  The HLSL compiler does annotate, in the bytecode it generates, which outputs could have been influenced by an SV_ViewID reference based on code flow.  Regardless of whether the actual computed values end up being view varying or not, any output with a possible SV_ViewID dependency is assumed to vary per view by implementations.  This annotation can be leveraged by runtimes as needed.

The HLSL compiler generates metadata in shader bytecode to assist with validation. There are three components to the metadata: 

(1) A bit for every scalar output of a shader indicating if it could be influenced by a reference to ViewID in that shader 

(2) A bit vector that describes for every scalar output from a shader which scalar inputs influence it

(3) Shader input/output/pc arrays have a bit mask indicating which components are dynamically indexed 

Below are some important details on the HLSL compiler analysis: 

(1) The compiler analyzes hull shader stages independently; i.e., values in one stage do not affect values in the other stage. The analysis resolves that patch constant stage outputs depend on control point (main entry) inputs; the runtime/driver does not need to do this. 

(2) UAV accesses do not propagate dependency on ViewID as it is unlikely that an implementation is willing to replicate a UAV; that is, loads from UAVs are never dependent on ViewID.

(3) The current implementation of ViewID state analysis in the HLSL compiler is somewhat conservative. There is no context-sensitive analysis of loads and stores for indexable registers. As such, any ViewID-dependent store to such a register, makes all loads from this variable depend on ViewID in the entire shader. Future versions of the compiler may implement a more precise, context-sensitive analysis of loads and stores. 

### SV_Barycentrics

Barycentric coordinates are a common method for defining locations within a geometric primitive such as a triangle or line. This document describes a mechanism for pixel shaders to read barycentric coordinates of the current pixel relative to the containing primitive. These can then be used for custom attribute interpolation, such as higher-order interpolation schemes, creative attribute unpacking, or allowing per-vertex attributes to be specified and interpolated at other precisions. Effectively, barycentric coordinates cleanly isolate the process of mapping the current pixel to a location within the primitive being rasterized, and associated fixed-function logic for interpolating the attribute at that location, which can then be done on the shader processor. We consider this an important direction for future evolution of the graphics pipeline.
Two relatively orthogonal mechanisms are described, accessing the barycentric weights, and accessing attributes at the primitive vertices to be interpolated with those weights.

#### System Generated Barycentric Coordinates
Pixel shaders can access barycentric weights in their input attribute declaration via the SV_Barycentrics semantic system value, following the standard attribute declaration syntax:

    float4 PSMain(float3 baryWeights : SV_Barycentrics) : SV_Target {
       ...
    }

Attributes declared with the SV_Barycentrics system-generated value must be a vector of three 32-bit floating point numbers, representing the barycentric weights of the current pixel relative to the vertices of the original API primitive prior to clipping (see later re. interactions with clipping).

The 3 values are NOT guaranteed to add up to floating-point 1.0 exactly. If it is desired for the pixel shader to ensure that the weights have this property, it can reconstruct the third coordinate per fragment by subtracting the sum of the other two from 1.0.

Also note, that individual barycentric weights may take on arbitrarily large or arbitrarily small values, and are not constrained to be within [0...1] range necessarily – this may happen for screen-space (non-perspective-correct) barycentric interpolants, screen-space quads, or external triangles.
For triangle primitives, all 3 weights will typically contain non-zero values, but for line primitives the third barycentric weight (e.g. myBaryWeights.z) is guaranteed to be exactly 0.0. With this definition, pixel shaders can remain agnostic to the primitive type being rasterized (i.e. they can evaluate barycentric sums using all 3 barycentric weights for both triangles and lines).

Implementers note: attributes declared as barycentrics will not have space reserved in the pixel shader signature storage.

#### Barycentric Coordinate Interpolation Types
For the most part, barycentric coordinates behave just like any other regular attribute, in the sense of allowing either affine (screen-space) or perspective-correct interpolation, and optional centroid adjustment. Interpolation type is specified using existing syntax, e.g.:

    // perspective-correct barycentrics: (default)
    linear float3 BaryLinear : SV_Barycentrics;

    // centroid-adjusted affine (screen-space) barycentrics:
    centroid noperspective float3 BaryAffine : SV_Barycentrics;

    // force shader to run at supersampling rate (one invocation per MSAA sample)
    sample noperspective float3 BaryAffineSample : SV_Barycentrics;

The nointerpolation interpolation modifier is disallowed for barycentric attributes.
As an exception to the current attribute specification rules, it is allowed for the pixel shader to declare **at most two** input attributes with the SV_Barycentrics system semantics, provided that one declaration uses **perspective-correct** interpolation type, and the other uses **noperspective**(affine, screen-space) interpolation type. These two system semantics should have different indices with value either 0 or 1.  For example, the following is a valid attribute syntax:
    
    float4 PSMain(float3 PerspectiveBaryWeights : SV_Barycentrics,
       noperspective float3 NoPerspectiveBaryWeights : SV_Barycentrics1) : SV_Target

This allows the pixel shader to get access to both perspective-correct and affine versions of barycentric coordinates.

### Barycentric Coordinate Ordering
Barycentric coordinates ordering from the perspective of the pixel shader matches vertex ordering of the primitive being rasterized in the original API stream. For example, if a triangle ABC is specified using the following order of its vertices: A, B, C, then the pixel shader will see the barycentric weight associated with the vertex A in the x component of the SV_Barycentric vector, and barycentric weights associated with vertices B and C will be found in y and z components of the vector, correspondingly. Note that this definition also implies that the barycentric weight, associated with the provoking vertex of the current primitive can always be found in the x component of the SV_Barycentrics vector. 
One important exception to the above rule is triangle strips: due to the way triangle strips are specified, the order of barycentric weights will have to be flipped for every other triangle. This is necessary to ensure that the pixel shader always sees consistent winding of vertices for all triangles in the strip. More specifically, given the following triangle strip:

 ![triangle_strip](https://github.com/youngkim93/DirectXShaderCompiler/blob/execution-barycentric/docs/BarycentricTriangleStrip.jpg)

The first two triangles will specify their barycentric weights in the following order (corresponding to x,y,z components of the SV_Barycentric vector):

Triangle 0: [x:0, y:1, z:2], 0 is the provoking vertex

Triangle 1: [x:1, y:3, z:2], 1 is the provoking vertex

Note how barycentric weights corresponding to vertices 2 and 3 of the second triangle have been flipped relative to their API specification order.

#### Per-Vertex Attributes
For pixel shaders to perform attribute interpolation using the system-generated barycentric weights, the attributes values at the vertices must be provided.
These can be accessed by declaring the attribute as nointerpolation, and using new intrinsics to read the values at the 3 vertices.
Attributes declared as nointerpolation do not participate in the clipping and interpolation setup stages, but rather their per-vertex values are provided as is to the pixel shader. Implementations are required to preserve all bits in the binary representation of such attributes through the VS/DS/GS-to-PS interface – so that applications can treat them essentially as sets of 32-bit bitfields with application-specific interpretation.
To use the above barycentric weights to interpolate attributes, the values of the attributes at the vertices are provided by the following routine:

    <attributeType> GetAttributeAtVertex( nointerpolation <attributeType> attribute,
                                                                      uint VertexID );

Where **VertexID** is in the range 0..2, and **attributeType** is an attribute declared with **nointerpolation**.

This routine can be used in the following way:

    // enum available in HLSL 2017
    enum VertexID { 
        FIRST = 0,
        SECOND = 1,
        THIRD = 2
    };

    // Linear perspective-correct interpolation of the COLOR attribute
    float3 main( float3 vBaryWeights : SV_Barycentrics,
		 nointerpolation float3 Color : COLOR ) : SV_Target
    {
        float3 vColor;
        . . .

        float3 vColor0 = GetAttributeAtVertex( Color, VertexID::FIRST );  // color at provoking vertex
        float3 vColor1 = GetAttributeAtVertex( Color, VertexID::SECOND ); // color at 2nd vertex
        float3 vColor2 = GetAttributeAtVertex( Color, VertexID::THIRD );  // color at last vertex

        vColor = vBaryWeights.x*vColor0 + vBaryWeights.y*vColor1 + vBaryWeights.z*vColor2;

        return vColor;
    }

The triangle indices specified follow the order of the original triangle vertices as specified in the API stream, (taking the behavior of strips into account). This also means that the order of barycentric weights and the order of per-vertex attributes always match, so that the pixel shader can always assume that the per-vertex attribute at VertexID= 0 corresponds to the barycentric weight placed in the x component of the SV_Barycentrics vector, etc. This also means that the value of a per vertex attribute at VertexID 0 always corresponds to its value at the “provoking vertex”.

As a consequence, it should be possible for pixel shaders to read attributes directly from a vertex buffer and interpolate them in a manner consistent with the fixed-function interpolator.

As always, it is illegal to combine nointerpolation mode with centroid or sample specifiers on the same parameter.

#### Interactions with Clipping
Per-vertex attributes are never clipped, and always passed along unmodified, so that the pixel shader gets access to their values as they are output by the last shader in the geometry pipeline (DS, VS or GS). This is also true for vertices which happen to be outside the frustum, or even behind the W=0 plane in clip-space, regardless of what kind of clipping situation occurs for the current primitive.

#### Wireframe mode
When drawing primitives with wireframe rasterizer mode (i.e., D3D12_FILL_MODE_WIREFRAME), barycentric co-ordinates follow the same order as the input vertices. This means that when drawing triangle primitives for example, where a barycentric co-ordinate in a wireframe tends to have a zero component and two non-zero ones, the 3rd component isn't necessary the zero.

# Texture3D.SampleGrad Method

Reference

## Definition

Samples a [Texture3D](#Texture3D.md) using a gradient to influence the way the sample location is calculated.
#### In this article

*  [Definition](#definition)
*  [Overloads](#overloads)

## Overloads

| Method | Description |
| ------ | ----------- |
| [SampleGrad(S,float3,float3,float3,int3)](#SampleGrad-S-float3-float3-float3-int3) | Samples a texture, using a gradient to influence the way the sample location is calculated. |
| [SampleCmp(S,float3,float3,float3,int3,float)](#SampleCmp-S-float3-float3-float3-int3-float) | Samples a texture, using a gradient to influence the way the sample location is calculated, with an optional value to clamp sample level-of-detail (LOD) values to. |
| [SampleCmp(S,float3,float3,float3,int3,float,uint)](#SampleCmp-S-float3-float-float-int3-float-uint) | Samples a texture, using a gradient to influence the way the sample location is calculated, with an optional value to clamp sample level-of-detail (LOD) values to. Returns status about the operation. |

## SampleGrad(S,float3,float3,float3,int3) {#SampleGrad-S-float3-float3-float3-int3}

Samples a texture, using a gradient to influence the way the sample location is calculated.

```HLSL
DXGI_FORMAT SampleCmp(
  in SamplerState S,
  in float3       Location,
  in float3       DDX,
  in float3       DDY,
  in int3         Offset
);
```

### Parameters
<i>S</i> [in] SamplerState
The zero-based sampler index.

<i>Location</i> [in] float3
The sample coordinates (u,v,w).

<i>DDX</i> [in] float3
The rate of change of the surface geometry in the x direction.

<i>DDY</i> [in] float3
The rate of change of the surface geometry in the y direction.

<i>Offset</i> [in] int3
The offset applied to the texture coordinates before sampling.

### Returns
Type: DXGI_FORMAT

The texture format, which is one of the typed values listed in DXGI_FORMAT.

## SampleGrad(S,float3,float3,float3,int3,float) {#SampleGrad-S-float3-float3-float3-int3-float}

Samples a Texture3D, using a gradient to influence the way the sample location is calculated, with an optional value to clamp sample level-of-detail (LOD) values to.

```HLSL
DXGI_FORMAT SampleCmp(
  in SamplerState S,
  in float3       Location,
  in float3       DDX,
  in float3       DDY,
  in int3         Offset,
  in float        Clamp
);
```

### Parameters
<i>S</i> [in] SamplerState
The zero-based sampler index.

<i>Location</i> [in] float3
The sample coordinates (u,v,w).

<i>DDX</i> [in] float3
The rate of change of the surface geometry in the x direction.

<i>DDY</i> [in] float3
The rate of change of the surface geometry in the y direction.

<i>Offset</i> [in] int
The offset applied to the texture coordinates before sampling.

<i>Clamp</i> [in] float
An optional value to clamp sample LOD values to. For example, if you pass 2.0f for the clamp value, you ensure that no individual sample accesses a mip level less than 2.0f.

### Returns
Type: DXGI_FORMAT

The texture format, which is one of the typed values listed in DXGI_FORMAT.

## SampleGrad(S,float3,float3,float3,int3,float) {#SampleGrad-S-float3-float3-float3-int3-float}

Samples a Texture3D, using a gradient to influence the way the sample location is calculated, with an optional value to clamp sample level-of-detail (LOD) values to.

```HLSL
DXGI_FORMAT SampleCmp(
  in SamplerState S,
  in float3       Location,
  in float3       DDX,
  in float3       DDY,
  in int3         Offset,
  in float        Clamp,
  out uint        Status
);
```

### Parameters
<i>S</i> [in] SamplerState
The zero-based sampler index.

<i>Location</i> [in] float3
The sample coordinates (u,v,w).

<i>DDX</i> [in] float3
The rate of change of the surface geometry in the x direction.

<i>DDY</i> [in] float3
The rate of change of the surface geometry in the y direction.

<i>Offset</i> [in] int
The offset applied to the texture coordinates before sampling.

<i>Clamp</i> [in] float
An optional value to clamp sample LOD values to. For example, if you pass 2.0f for the clamp value, you ensure that no individual sample accesses a mip level less than 2.0f.

<i>Status</i> [out] uint
The status of the operation. You can't access the status directly; instead, pass the status to the CheckAccessFullyMapped intrinsic function. CheckAccessFullyMapped returns TRUE if all values from the corresponding Sample, Gather, or Load operation accessed mapped tiles in a tiled resource. If any values were taken from an unmapped tile, CheckAccessFullyMapped returns FALSE.

### Returns
Type: DXGI_FORMAT

The texture format, which is one of the typed values listed in DXGI_FORMAT.
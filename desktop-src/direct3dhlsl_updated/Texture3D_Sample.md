# Texture3D.Sample Method

Reference

## Definition

Samples a [Texture3D](#Texture3D.md).

See the documentation on gather4 for more information describing the underlying DXBC instruction.

#### In this article

*  [Definition](#definition)
*  [Overloads](#overloads)

## Overloads

| Method | Description |
| ------ | ----------- |
| [Sample(S,float3,int3)](#Sample-S-float3-int3) | Samples a texture. |
| [Sample(S,float3,int3,float)](#Sample-S-float3-int3-float) | Samples a texture with an optional value to clamp sample level-of-detail (LOD) values to. |
| [Sample(S,float3,int3,float,uint)](#Sample-S-float-int-float-uint) | Samples a texture with an optional value to clamp sample level-of-detail (LOD) values to, and returns status of the operation. |

## Sample(S,float,int) {#Sample-S-float-int}

```HLSL
DXGI_FORMAT Sample(
  in SamplerState S,
  in float3 Location,
  in int3 Offset
);
```

### Parameters
<i>S</i> [in] SamplerState
The zero-based sampler index.

<i>Location</i> [in] float3
The sample coordinates (u,v,w).

<i>Offset</i> [in] int3
The offset applied to the texture coordinates before sampling.

### Returns
The texture format, which is one of the typed values listed in DXGI_FORMAT.

## Sample(S,float3,int3,float) {#Sample-S-float3-int3-float}

```HLSL
DXGI_FORMAT Sample(
  in SamplerState S,
  in float3 Location,
  in int3 Offset,
  in float Clamp
);
```

### Parameters
<i>S</i> [in] SamplerState
The zero-based sampler index.

<i>Location</i> [in] float3
The sample coordinates (u,v,w).

<i>Offset</i> [in] int3
The offset applied to the texture coordinates before sampling.

<i>Clamp</i> [in] float
An optional value to clamp sample LOD values to. For example, if you pass 2.0f for the clamp value, you ensure that no individual sample accesses a mip level less than 2.0f.

### Returns
The texture format, which is one of the typed values listed in DXGI_FORMAT.

## Sample(S,float,int,float,uint) {#Sample-S-float-int-float-uint}

```HLSL
DXGI_FORMAT Sample(
  in SamplerState S,
  in float3 Location,
  in int3 Offset,
  in float Clamp,
  out uint Status
);
```

### Parameters
<i>S</i> [in] SamplerState
The zero-based sampler index.

<i>Location</i> [in] float3
The sample coordinates (u,v,w).

<i>Offset</i> [in] int3
The offset applied to the texture coordinates before sampling.

<i>Clamp</i> [in] float
An optional value to clamp sample LOD values to. For example, if you pass 2.0f for the clamp value, you ensure that no individual sample accesses a mip level less than 2.0f.

<i>Status</i> [out] uint
The status of the operation. You can't access the status directly; instead, pass the status to the CheckAccessFullyMapped intrinsic function. CheckAccessFullyMapped returns TRUE if all values from the corresponding Sample, Gather, or Load operation accessed mapped tiles in a tiled resource. If any values were taken from an unmapped tile, CheckAccessFullyMapped returns FALSE.

### Returns
The texture format, which is one of the typed values listed in DXGI_FORMAT.
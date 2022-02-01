# Texture1DArray.Sample Method

Reference

## Definition

Samples a [Texture1D](#Texture1D.md).

#### In this article

*  [Definition](#definition)
*  [Overloads](#overloads)

## Overloads

| Method | Description |
| ------ | ----------- |
| [Sample(S,float2,int)](#Sample-S-float2-int) | Samples a texture. |
| [Sample(S,float2,int,float)](#Sample-S-float2-int-float) | Samples a texture with an optional value to clamp sample level-of-detail (LOD) values to. |
| [Sample(S,float2,int,float,uint)](#Sample-S-float2-int-float-uint) | Samples a texture with an optional value to clamp sample level-of-detail (LOD) values to, and returns status about the operation. |

## Sample(S,float,int) {#Sample-S-float-int}

```HLSL
DXGI_FORMAT Sample(
  in SamplerState S,
  in float2 Location,
  in int Offset
);
```

### Parameters
<i>S</i> [in] SamplerState
A Sampler state. This is an object declared in an effect file that contains state assignments.

<i>location</i> [in] float2
The index position. The first component contains the u coordinate. The second component indicates the desired array slice.

<i>offset</i> [in] int
The offset applied to the texture coordinates before sampling.

### Returns
The texture format, which is one of the typed values listed in DXGI_FORMAT.

## Sample(S,float2,int,float) {#Sample-S-float2-int-float}

```HLSL
DXGI_FORMAT Sample(
  in SamplerState S,
  in float2 Location,
  in int Offset,
  in float Clamp
);
```

### Parameters
<i>S</i> [in] SamplerState
A Sampler state. This is an object declared in an effect file that contains state assignments.

<i>location</i> [in] float2
The index position. The first component contains the u coordinate. The second component indicates the desired array slice.

<i>offset</i> [in] int
The offset applied to the texture coordinates before sampling.

<i>Clamp</i> [in] float
An optional value to clamp sample LOD values to. For example, if you pass 2.0f for the clamp value, you ensure that no individual sample accesses a mip level less than 2.0f.

### Returns
Type: DXGI_FORMAT

The texture format, which is one of the typed values listed in DXGI_FORMAT.

## Sample(S,float2,int,float,uint) {#Sample-S-float2-int-float-uint}

```HLSL
DXGI_FORMAT Sample(
  in SamplerState S,
  in float2 Location,
  in int Offset,
  in float Clamp,
  out uint Status
);
```

### Parameters
<i>S</i> [in] SamplerState
A Sampler state. This is an object declared in an effect file that contains state assignments.

<i>location</i> [in] float2
The index position. The first component contains the u coordinate. The second component indicates the desired array slice.

<i>offset</i> [in] int
The offset applied to the texture coordinates before sampling.

<i>Clamp</i> [in] float
An optional value to clamp sample LOD values to. For example, if you pass 2.0f for the clamp value, you ensure that no individual sample accesses a mip level less than 2.0f.

<i>Status</i> [out] uint
The status of the operation. You can't access the status directly; instead, pass the status to the CheckAccessFullyMapped intrinsic function. CheckAccessFullyMapped returns TRUE if all values from the corresponding Sample, Gather, or Load operation accessed mapped tiles in a tiled resource. If any values were taken from an unmapped tile, CheckAccessFullyMapped returns FALSE.

### Returns
Type: DXGI_FORMAT

The texture format, which is one of the typed values listed in DXGI_FORMAT.
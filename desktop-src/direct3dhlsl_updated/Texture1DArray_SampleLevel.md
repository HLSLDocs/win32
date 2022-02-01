# Texture1D.SampleLevel Method

Reference

## Definition

Samples a texture on the specified mipmap level.

#### In this article

*  [Definition](#definition)
*  [Overloads](#overloads)

## Overloads

| Method | Description |
| ------ | ----------- |
| [SampleLevel(S,float2,float,int)](#SampleLevel-S-float2-float-int) | Samples a texture on the specified mipmap level. |
| [SampleLevel(S,float2,float,int,uint)](#SampleLevel-S-float2-float-int-uint) | Samples a texture on the specified mipmap level and returns status about the operation. |

## SampleLevel(S,float2,float,int) {#SampleLevel-S-float2-float-int}

Samples a texture on the specified mipmap level.

```HLSL
DXGI_FORMAT SampleLevel(
  in  SamplerState S,
  in  float2       Location,
  in  float        LOD,
  in  int          Offset
);
```

### Parameters
<i>S</i> [in] SamplerState
A Sampler state. This is an object declared in an effect file that contains state assignments.

<i>location</i> [in] float2
The index position. The first component contains the u coordinate. The second component indicates the desired array slice.

<i>LOD</i> [in] float
A number that specifies the mipmap level. If the value is <= 0, mipmap level 0 (biggest map) is used. The fractional value (if supplied) is used to interpolate between two mipmap levels.

<i>Offset</i> [in] int
The offset applied to the texture coordinates before sampling.

### Returns
Type: DXGI_FORMAT

The texture format, which is one of the typed values listed in DXGI_FORMAT.

## SampleLevel(S,float2,float,int,uint) {#SampleLevel-S-float2-float-int-uint}

Samples a texture on the specified mipmap level and returns status about the operation.

```HLSL
DXGI_FORMAT SampleLevel(
  in  SamplerState S,
  in  float2       Location,
  in  float        LOD,
  in  int          Offset,
  out uint         Status
);
```

### Parameters
<i>S</i> [in] SamplerState
A Sampler state. This is an object declared in an effect file that contains state assignments.

<i>location</i> [in] float2
The index position. The first component contains the u coordinate. The second component indicates the desired array slice.

<i>LOD</i> [in] float
A number that specifies the mipmap level. If the value is <= 0, mipmap level 0 (biggest map) is used. The fractional value (if supplied) is used to interpolate between two mipmap levels.

<i>Offset</i> [in] int
The offset applied to the texture coordinates before sampling.

<i>Status</i> [out] uint
The status of the operation. You can't access the status directly; instead, pass the status to the CheckAccessFullyMapped intrinsic function. CheckAccessFullyMapped returns TRUE if all values from the corresponding Sample, Gather, or Load operation accessed mapped tiles in a tiled resource. If any values were taken from an unmapped tile, CheckAccessFullyMapped returns FALSE.

### Returns
Type: DXGI_FORMAT

The texture format, which is one of the typed values listed in DXGI_FORMAT.

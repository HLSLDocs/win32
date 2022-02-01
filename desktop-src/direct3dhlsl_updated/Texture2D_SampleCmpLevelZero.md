# Texture2D.SampleCmpLevelZero Method

Reference

## Definition

Samples a Texture2D on mipmap level 0 only, using a comparison value to reject samples.

#### In this article

*  [Definition](#definition)
*  [Overloads](#overloads)

## Overloads

| Method | Description |
| ------ | ----------- |
| [SampleCmpLevelZero(S,float2,float,int2)](#SampleCmpLevelZero-S-float-float-int) | Samples a texture on mipmap level 0 only and compares the result to a comparison value. |
| [SampleCmpLevelZero(S,float2,float,int2,uint)](#SampleCmpLevelZero-S-float-float-int-uint) | Samples a texture on mipmap level 0 only and compares the result to a comparison value. Returns status about the operation. |

## SampleCmpLevelZero(S,float2,float,int2) {#SampleCmpLevelZero-S-float2-float-int2}

Samples a Texture2D, using a comparison value to reject samples.

```HLSL
DXGI_FORMAT SampleCmpLevelZero(
  in SamplerState S,
  in float2       Location,
  in float        CompareValue,
  in int2         Offset
);
```

### Parameters
<i>S</i> [in] SamplerState
The zero-based sampler index.

<i>Location</i> [in] float2
The sample coordinates (u,v).

<i>CompareValue</i> [in] float
A floating-point value to use as a comparison value.

<i>Offset</i> [in] int
The offset applied to the texture coordinates before sampling.

### Returns
Type: DXGI_FORMAT

The texture format, which is one of the typed values listed in DXGI_FORMAT.

## SampleCmpLevelZero(S,float2,float,int2,uint) {#SampleCmpLevelZero-S-float2-float-int2-uint}

Samples a texture on mipmap level 0 only and compares the result to a comparison value. Returns status about the operation.

```HLSL
DXGI_FORMAT SampleCmpLevelZero(
  in SamplerState S,
  in float2       Location,
  in float        CompareValue,
  in int2         Offset,
  out uint        Status
);
```

### Parameters
<i>S</i> [in] SamplerState
The zero-based sampler index.

<i>Location</i> [in] float2
The sample coordinates (u,v).

<i>CompareValue</i> [in] float
A floating-point value to use as a comparison value.

<i>Offset</i> [in] int
The offset applied to the texture coordinates before sampling.

<i>Status</i> [out] uint
The status of the operation. You can't access the status directly; instead, pass the status to the CheckAccessFullyMapped intrinsic function. CheckAccessFullyMapped returns TRUE if all values from the corresponding Sample, Gather, or Load operation accessed mapped tiles in a tiled resource. If any values were taken from an unmapped tile, CheckAccessFullyMapped returns FALSE.

### Returns
Type: DXGI_FORMAT

The texture format, which is one of the typed values listed in DXGI_FORMAT.

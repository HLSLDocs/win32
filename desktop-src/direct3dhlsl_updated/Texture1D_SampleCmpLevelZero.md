# Texture1D.SampleCmpLevelZero Method

Reference

## Definition

Samples a Texture1D on mipmap level 0 only, using a comparison value to reject samples.

#### In this article

*  [Definition](#definition)
*  [Overloads](#overloads)

## Overloads

| Method | Description |
| ------ | ----------- |
| [SampleCmpLevelZero(S,float,float,int)](#SampleCmpLevelZero-S-float-float-int) | Samples a texture on mipmap level 0 only and compares the result to a comparison value. |
| [SampleCmpLevelZero(S,float,float,int,uint)](#SampleCmpLevelZero-S-float-float-int-uint) | Samples a texture on mipmap level 0 only and compares the result to a comparison value. Returns status about the operation. |

## SampleCmpLevelZero(S,float,float,int) {#SampleCmpLevelZero-S-float-float-int}

Samples a Texture2D, using a comparison value to reject samples.

```HLSL
DXGI_FORMAT SampleCmpLevelZero(
  in SamplerComparisonState S,
  in float        Location,
  in float        CompareValue,
  in int          Offset
);
```

### Parameters
<i>S</i> [in] SamplerComparisonState
A Sampler state. This is an object declared in an effect file that contains state assignments.

<i>location</i> [in] float
The texture coordinate; the first component contains the u coordinates.

<i>CompareValue</i> [in] float
A floating-point value to use as a comparison value.

<i>Offset</i> [in] int
The offset applied to the texture coordinates before sampling.

### Returns
Type: DXGI_FORMAT

The texture format, which is one of the typed values listed in DXGI_FORMAT.

## SampleCmpLevelZero(S,float,float,int,uint) {#SampleCmpLevelZero-S-float-float-int-uint}

Samples a texture on mipmap level 0 only and compares the result to a comparison value. Returns status about the operation.

```HLSL
DXGI_FORMAT SampleCmpLevelZero(
  in SamplerComparisonState S,
  in float        Location,
  in float        CompareValue,
  in int          Offset,
  out uint        Status
);
```

### Parameters
<i>S</i> [in] SamplerComparisonState
A Sampler state. This is an object declared in an effect file that contains state assignments.

<i>location</i> [in] float
The texture coordinate; the first component contains the u coordinates.

<i>CompareValue</i> [in] float
A floating-point value to use as a comparison value.

<i>Offset</i> [in] int
The offset applied to the texture coordinates before sampling.

<i>Status</i> [out] uint
The status of the operation. You can't access the status directly; instead, pass the status to the CheckAccessFullyMapped intrinsic function. CheckAccessFullyMapped returns TRUE if all values from the corresponding Sample, Gather, or Load operation accessed mapped tiles in a tiled resource. If any values were taken from an unmapped tile, CheckAccessFullyMapped returns FALSE.

### Returns
Type: DXGI_FORMAT

The texture format, which is one of the typed values listed in DXGI_FORMAT.

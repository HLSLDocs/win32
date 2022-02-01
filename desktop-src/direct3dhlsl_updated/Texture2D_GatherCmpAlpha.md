# Texture2D.GatherCmpAlpha Method

Reference

## Definition

Samples and compares a [Texture2D](#Texture2D.md) and returns the alpha component.

#### In this article

*  [Definition](#definition)
*  [Overloads](#overloads)

## Overloads

| Method | Description |
| ------ | ----------- |
| [GatherCmpAlpha(S,float2,float,int2)](#GatherCmpAlpha-S-float2-float-int2) | Samples and compares a texture and returns the alpha component. |
| [GatherCmpAlpha(S,float2,float,int2,int2,int2,int2)](#GatherCmpAlpha-S-float2-float-int2-int2-int2-int2) | Samples and compares a texture and returns the alpha component. |
| [GatherCmpAlpha(S,float2,float,int2,uint)](#GatherCmpAlpha-S-float-float-int-uint) | Samples and compares a texture and returns the alpha component along with status about the operation. |
| [GatherCmpAlpha(S,float2,float,int2,int2,int2,int2,uint)](#GatherCmpAlpha-S-float-float-int2-int2-int2-int2-uint) | Samples and compares a texture and returns the alpha component along with status about the operation. |

## GatherCmpAlpha(S,float2,float,int2) {#GatherCmpAlpha-S-float2-float-int2}

For four texel values that would be used in a bi-linear filtering operation, returns a comparison of their alpha component against a compare value.

```HLSL
float4 GatherCmpAlpha(
  in SamplerComparisonState S,
  in float2 location,
  in float compare_value,
  in int2 offset
);
```

### Parameters
<i>S</i> [in] SamplerComparisonState
The zero-based sampler index.

<i>location</i> [in] float2
The sample coordinates (u,v).

<i>compare_value</i> [in] float
A value to compare each against each sampled value.

<i>offset</i> [in] int2
The offset applied to the texture coordinates before sampling.

### Returns
float4

A four-component value, each component is the result of a per-component comparison.

### Remarks
The texture samples can be used for bilinear interpolation.

## GatherCmpAlpha(S,float2,float,int2,int2,int2,int2) {#GatherCmpAlpha-S-float2-float-int2-int2-int2-int2}

For four texel values that would be used in a bi-linear filtering operation, returns a comparison of their alpha component against a compare value.

```HLSL
TemplateType GatherCmpAlpha(
  in SamplerComparisonState S,
  in float2       Location,
  in float        CompareValue,
  in int2         Offset1,
  in int2         Offset2,
  in int2         Offset3,
  in int2         Offset4
);
```

### Parameters
<i>S</i> [in] SamplerComparisonState
The zero-based sampler index.

<i>Location</i> [in] float2
The sample coordinates (u,v).

<i>CompareValue</i> [in] float
A value to compare each against each sampled value.

<i>Offset1</i> [in] int2
The first offset component applied to the texture coordinates before sampling.

<i>Offset2</i> [in] int2
The second offset component applied to the texture coordinates before sampling.

<i>Offset3</i> [in] int2
The third offset component applied to the texture coordinates before sampling.

<i>Offset4</i> [in] int2
The fourth offset component applied to the texture coordinates before sampling.

### Returns
TemplateType

A four-component value whose type is the same as the template type.

### Remarks
The texture samples can be used for bilinear interpolation.

## GatherCmpAlpha(S,float2,float,int2,uint) {#GatherCmpAlpha-S-float-float-int-uint}

For four texel values that would be used in a bi-linear filtering operation, returns a comparison of their alpha component against a compare value along with tile-mapping status.

```HLSL
TemplateType GatherCmpAlpha(
  in  SamplerComparisonState S,
  in  float2       Location,
  in  float        CompareValue,
  in  int2         Offset,
  out uint         Status
);
```

### Parameters
<i>S</i> [in] SamplerComparisonState
The zero-based sampler index.

<i>Location</i> [in] float2
The sample coordinates (u,v).

<i>CompareValue</i> [in] float
A value to compare each against each sampled value.

<i>Offset</i> [in] int2
The offset applied to the texture coordinates before sampling.

<i>Status</i> [out] uint
The status of the operation. You can't access the status directly; instead, pass the status to the CheckAccessFullyMapped intrinsic function. CheckAccessFullyMapped returns TRUE if all values from the corresponding Sample, Gather, or Load operation accessed mapped tiles in a tiled resource. If any values were taken from an unmapped tile, CheckAccessFullyMapped returns FALSE.

### Returns
TemplateType

A four-component value whose type is the same as the template type.

### Remarks
The texture samples can be used for bilinear interpolation.

## GatherCmpAlpha(S,float2,float,int2,int2,int2,int2,uint) {#GatherCmpAlpha-S-float2-float-int2-int2-int2-int2-uint}

For four texel values that would be used in a bi-linear filtering operation, returns a comparison of their alpha component against a compare value along with tile-mapping status.

```HLSL
TemplateType GatherCmpAlpha(
  in  SamplerComparisonState S,
  in  float2       Location,
  in  float        CompareValue,
  in  int2         Offset1,
  in  int2         Offset2,
  in  int2         Offset3,
  in  int2         Offset4,
  out uint         Status
);
```

### Parameters
<i>S</i> [in] SamplerComparisonState
The zero-based sampler index.

<i>Location</i> [in] float2
The sample coordinates (u,v).

<i>CompareValue</i> [in] float
A value to compare each against each sampled value.

<i>Offset1</i> [in] int2
The first offset component applied to the texture coordinates before sampling.

<i>Offset2</i> [in] int2
The second offset component applied to the texture coordinates before sampling.

<i>Offset3</i> [in] int2
The third offset component applied to the texture coordinates before sampling.

<i>Offset4</i> [in] int2
The fourth offset component applied to the texture coordinates before sampling.

<i>Status</i> [out] uint
The status of the operation. You can't access the status directly; instead, pass the status to the CheckAccessFullyMapped intrinsic function. CheckAccessFullyMapped returns TRUE if all values from the corresponding Sample, Gather, or Load operation accessed mapped tiles in a tiled resource. If any values were taken from an unmapped tile, CheckAccessFullyMapped returns FALSE.

### Returns
TemplateType

A four-component value whose type is the same as the template type.

### Remarks
The texture samples can be used for bilinear interpolation.
# Texture2DArray.GatherCmpGreen Method

Reference

## Definition

Samples and compares a texture and returns the green component.

#### In this article

*  [Definition](#definition)
*  [Overloads](#overloads)

## Overloads

| Method | Description |
| ------ | ----------- |
| [GatherCmpGreen(S,float3,float,int2)](#GatherCmpGreen-S-float3-float-int2) | Samples and compares a texture and returns the green component. |
| [GatherCmpGreen(S,float3,float,int2,int2,int2,int2)](#GatherCmpGreen-S-float3-float-int2-int2-int2-int2) | Samples and compares a texture and returns the green component. |
| [GatherCmpGreen(S,float3,float,int2,uint)](#GatherCmpGreen-S-float3-float-int2-uint) | Samples and compares a texture and returns the green component along with status about the operation. |
| [GatherCmpGreen(S,float,float,int2,int2,int2,int2,uint)](#GatherCmpGreen-S-float-float-int2-int2-int2-int2-uint) | Samples and compares a texture and returns the green component along with status about the operation. |

## GatherCmpGreen(S,float3,int2) {#GatherCmpGreen-S-float3-int2}

For four texel values that would be used in a bi-linear filtering operation, returns a comparison of their green component against a compare value.

```HLSL
float4 GatherCmpGreen(
  in SamplerComparisonState s,
  in float3 location,
  in float compare_value,
  in int2 offset
);
```

### Parameters
<i>S</i> [in] SamplerComparisonState
The zero-based sampler index.

<i>location</i> [in] float3
The texture coordinates; the first and second components contain the (u,v) coordinates.  The third component indicates the desired array slice.

<i>compare_value</i> [in] float
A value to compare each against each sampled value.

<i>offset</i> [in] int2
The offset applied to the texture coordinates before sampling.

### Returns
TemplateType

A four-component value whose type is the same as the template type.

### Remarks
The texture samples can be used for bilinear interpolation.

## GatherCmpGreen(S,float3,float,int2,int2,int2,int2) {#GatherCmpGreen-S-float3-float-int2-int2-int2-int2}

For four texel values that would be used in a bi-linear filtering operation, returns a comparison of their green component against a compare value.

```HLSL
TemplateType GatherCmpGreen(
  in SamplerComparisonState S,
  in float3       Location,
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

<i>Location</i> [in] float3
The texture coordinates; the first and second components contain the (u,v) coordinates.  The third component indicates the desired array slice.

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

## GatherCmpGreen(S,float3,float,int2,uint) {#GatherCmpGreen-S-float3-float-int2-uint}

For four texel values that would be used in a bi-linear filtering operation, returns a comparison of their green component against a compare value along with tile-mapping status.

```HLSL
TemplateType GatherCmpGreen(
  in  SamplerComparisonState S,
  in  float3       Location,
  in  float        CompareValue,
  in  int2         Offset,
  out uint         Status
);
```

### Parameters
<i>S</i> [in] SamplerComparisonState
The zero-based sampler index.

<i>Location</i> [in] float3
The texture coordinates; the first and second components contain the (u,v) coordinates.  The third component indicates the desired array slice.

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

## GatherCmpGreen(S,float3,float,int2,int2,int2,int2,uint) {#GatherCmpGreen-S-float3-float-int2-int2-int2-int2-uint}

For four texel values that would be used in a bi-linear filtering operation, returns a comparison of their green component against a compare value along with tile-mapping status.

```HLSL
TemplateType GatherCmpGreen(
  in  SamplerComparisonState S,
  in  float3       Location,
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

<i>Location</i> [in] float3
The texture coordinates; the first and second components contain the (u,v) coordinates.  The third component indicates the desired array slice.

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
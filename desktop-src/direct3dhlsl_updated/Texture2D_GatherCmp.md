# Texture2D.GatherCmp Method

Reference

## Definition

For four texel values of a [Texture2D](#Texture2D.md) that would be used in a bi-linear filtering operation, returns their comparison against a compare value.

See the documentation on gather4_c for more information describing the underlying DXBC instruction.

#### In this article

*  [Definition](#definition)
*  [Overloads](#overloads)

## Overloads

| Method | Description |
| ------ | ----------- |
| [GatherCmp(S,float2,float,int2)](#GatherCmp-S-float2-float-int2) | Samples and compares a texture and returns all four components. |
| [GatherCmp(S,float2,float,int2,uint)](#GatherCmp-S-float2-float-int2-uint) | Samples and compares a texture and returns all four components along with status about the operation. |

## GatherCmp(S,float2,float,int2) {#Gather-S-float2-float-int2}

For four texel values that would be used in a bi-linear filtering operation, returns their comparison against a compare value.

```HLSL
float4 GatherCmp(
  in SamplerComparisonState s,
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

## Gather(S,float2,float,int2,uint) {#Gather-S-float2-float-int2-uint}

For four texel values that would be used in a bi-linear filtering operation, returns their comparison against a compare value along with tile-mapping status.

```HLSL
TemplateType GatherCmp(
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

<i>location</i> [in] float
The sample coordinates (u,v).

<i>CompareValue</i> [in] float
A value to compare each against each sampled value.

<i>Offset</i> [in] int2
The offset in texels applied to the texture coordinates before sampling. Must be a literal value.

<i>status</i> [out] uint
The status of the operation. You can't access the status directly; instead, pass the status to the CheckAccessFullyMapped intrinsic function. CheckAccessFullyMapped returns TRUE if all values from the corresponding Sample, Gather, or Load operation accessed mapped tiles in a tiled resource. If any values were taken from an unmapped tile, CheckAccessFullyMapped returns FALSE.

### Returns
TemplateType

A four-component value whose type is the same as the template type.

### Remarks
The texture samples can be used for bilinear interpolation.
# Texture2D.GatherRed Method

Reference

## Definition

Samples a [Texture2D](#Texture2D.md) and returns the red component.

#### In this article

*  [Definition](#definition)
*  [Overloads](#overloads)

## Overloads

| Method | Description |
| ------ | ----------- |
| [GatherRed(S,float2,int2)](#GatherRed-S-float2-int2) | Returns the red components of the four texel values that would be used in a bi-linear filtering operation. |
| [GatherRed(S,float2,int2,int2,int2,int2)](#GatherRed-S-float2-int2-int2-int2-int2) | Returns the red components of the four texel values that would be used in a bi-linear filtering operation. |
| [GatherRed(S,float2,int2,uint)](#GatherRed-S-float2-int2-uint) | Returns the red components of the four texel values that would be used in a bi-linear filtering operation, along with tile-mapping status. |
| [GatherRed(S,float2,int2,int2,int2,int2,uint)](#GatherRed-S-float2-int2-int2-int2-int2-uint) | Returns the red components of the four texel values that would be used in a bi-linear filtering operation, along with tile-mapping status. |

## GatherRed(S,float2,int2) {#GatherRed-S-float2-int2}

Returns the red components of the four texel values that would be used in a bi-linear filtering operation, along with tile-mapping status.

```HLSL
TemplateType Gather(
  in sampler s,
  in float2 location,
  in int2 offset
);
```

### Parameters
<i>S</i> [in] sampler
The zero-based sampler index.

<i>location</i> [in] float2
The sample coordinates (u,v).

<i>offset</i> [in] int2
The offset applied to the texture coordinates before sampling.

### Returns
TemplateType

A four-component value whose type is the same as the template type.

### Remarks
The texture samples can be used for bilinear interpolation.

## GatherRed(S,float2,int2,int2,int2,int2) {#GatherRed-S-float2-int2-int2-int2-int2}

Returns the red components of the four texel values that would be used in a bi-linear filtering operation, along with tile-mapping status.

```HLSL
TemplateType Gather(
  in SamplerState S,
  in float2       Location,
  in int2         Offset1,
  in int2         Offset2,
  in int2         Offset3,
  in int2         Offset4
);
```

### Parameters
<i>S</i> [in] SamplerState
The zero-based sampler index.

<i>Location</i> [in] float2
The sample coordinates (u,v).

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

## GatherRed(S,float2,int2,uint) {#GatherRed-S-float2-int2-uint}

Returns the red components of the four texel values that would be used in a bi-linear filtering operation, along with tile-mapping status.

```HLSL
TemplateType Gather(
  in  SamplerState S,
  in  float2       Location,
  in  int2         Offset,
  out uint         Status
);
```

### Parameters
<i>S</i> [in] SamplerState
The zero-based sampler index.

<i>Location</i> [in] float2
The sample coordinates (u,v).

<i>Offset</i> [in] int2
The offset applied to the texture coordinates before sampling.

<i>Status</i> [out] uint
The status of the operation. You can't access the status directly; instead, pass the status to the CheckAccessFullyMapped intrinsic function. CheckAccessFullyMapped returns TRUE if all values from the corresponding Sample, Gather, or Load operation accessed mapped tiles in a tiled resource. If any values were taken from an unmapped tile, CheckAccessFullyMapped returns FALSE.

### Returns
TemplateType

A four-component value whose type is the same as the template type.

### Remarks
The texture samples can be used for bilinear interpolation.

## GatherRed(S,float2,int2,int2,int2,int2,uint) {#GatherRed-S-float2-int2-int2-int2-int2-uint}

Returns the red components of the four texel values that would be used in a bi-linear filtering operation, along with tile-mapping status.

```HLSL
TemplateType Gather(
  in SamplerState S,
  in float2       Location,
  in int2         Offset1,
  in int2         Offset2,
  in int2         Offset3,
  in int2         Offset4,
  out uint        Status
);
```

### Parameters
<i>S</i> [in] SamplerState
The zero-based sampler index.

<i>Location</i> [in] float2
The sample coordinates (u,v).

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
# Texture2D.Gather Method

Reference

## Definition

Samples a [Texture2D](#Texture2D.md) and returns all four components.

See the documentation on gather4 for more information describing the underlying DXBC instruction.

#### In this article

*  [Definition](#definition)
*  [Overloads](#overloads)

## Overloads

| Method | Description |
| ------ | ----------- |
| [Gather(S,float2,int2)](#Gather-S-float2-int2) | Samples a texture and returns all four components. |
| [Gather(S,float2,int2,uint)](#Gather-S-float2-int2-uint) | Returns the four texel values that would be used in a bi-linear filtering operation, along with tile-mapping status. |

## Gather(S,float2,int2) {#Gather-S-float2-int2}

Returns the four texel values that would be used in a bi-linear filtering operation.

```HLSL
TemplateType Gather(
  in Sampler S,
  in float2 Location,
  in int2 Offset
);
```

### Parameters
<i>S</i> [in] Sampler
The zero-based sampler index.

<i>Location</i> [in] float2
The sample coordinates (u,v).

<i>Offset</i> [in] int2
The offset applied to the texture coordinates before sampling.

### Returns
TemplateType

A four-component value whose type is the same as the template type.

### Remarks
The texture samples can be used for bilinear interpolation.

## Gather(S,float2,int2,uint) {#Gather-S-float2-int2-uint}

Returns the four texel values that would be used in a bi-linear filtering operation, along with tile-mapping status.

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

<i>location</i> [in] float2
The sample coordinates (u,v).

<i>offset</i> [in] int2
The offset applied to the texture coordinates before sampling.

<i>status</i> [out] uint
The status of the operation. You can't access the status directly; instead, pass the status to the CheckAccessFullyMapped intrinsic function. CheckAccessFullyMapped returns TRUE if all values from the corresponding Sample, Gather, or Load operation accessed mapped tiles in a tiled resource. If any values were taken from an unmapped tile, CheckAccessFullyMapped returns FALSE.

### Returns
TemplateType

A four-component value whose type is the same as the template type.

### Remarks
The texture samples can be used for bilinear interpolation.
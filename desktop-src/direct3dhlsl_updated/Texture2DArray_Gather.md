# Texture2DArray.Gather Method

Reference

## Definition

Returns the four texel values of a Texture2DArray that would be used in a bi-linear filtering operation.

See the documentation on gather4 for more information describing the underlying DXBC instruction.

#### In this article

*  [Definition](#definition)
*  [Overloads](#overloads)

## Overloads

| Method | Description |
| ------ | ----------- |
| [Gather(S,float3,int2)](#Gather-S-float3-int2) | Returns the four texel values that would be used in a bi-linear filtering operation. |
| [Gather(S,float3,int2,uint)](#Gather-S-float3-int2-uint) | Returns the four texel values that would be used in a bi-linear filtering operation, along with tile-mapping status. |

## Gather(S,float3,int2) {#Gather-S-float3-int2}

Returns the four texel values that would be used in a bi-linear filtering operation.

```HLSL
TemplateType Gather(
  in sampler s,
  in float3 location,
  in int2 offset
);
```

### Parameters
<i>S</i> [in] sampler
The zero-based sampler index.

<i>location</i> [in] float3
The texture coordinates; the first and second components contain the (u,v) coordinates. The third component indicates the desired array slice.

<i>offset</i> [in] int2
The offset applied to the texture coordinates before sampling.

### Returns
TemplateType

A four-component value whose type is the same as the template type.

### Remarks
The texture samples can be used for bilinear interpolation.

## Gather(S,float3,int2,uint) {#Gather-S-float3-int2-uint}

Returns the four texel values that would be used in a bi-linear filtering operation, along with tile-mapping status.

```HLSL
TemplateType Gather(
  in  SamplerState S,
  in  float3       Location,
  in  int2         Offset,
  out uint         Status
);
```

### Parameters
<i>S</i> [in] SamplerState
The zero-based sampler index.

<i>location</i> [in] float3
The texture coordinates; the first and second components contain the (u,v) coordinates. The third component indicates the desired array slice.

<i>offset</i> [in] int2
The offset applied to the texture coordinates before sampling.

<i>status</i> [out] uint
The status of the operation. You can't access the status directly; instead, pass the status to the CheckAccessFullyMapped intrinsic function. CheckAccessFullyMapped returns TRUE if all values from the corresponding Sample, Gather, or Load operation accessed mapped tiles in a tiled resource. If any values were taken from an unmapped tile, CheckAccessFullyMapped returns FALSE.

### Returns
TemplateType

A four-component value whose type is the same as the template type.

### Remarks
The texture samples can be used for bilinear interpolation.
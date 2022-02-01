# Texture2DMS.sample.Operator Method

Reference

## Definition

Retrieves a value from the resource at the location and sample index provided.

#### In this article

*  [Definition](#definition)
*  [Overloads](#overloads)

## Overloads

| Method | Description |
| ------ | ----------- |
| [sample.Operator](#sample.Operator) | Retrieves a value from the resource at the location and sample index provided. |

## sample.Operator {#sample.Operator}

Retrieves a value from the resource at the location and sample index provided.

```HLSL
R sample.Operator[][](
  in uint sampleSlice,
  in uint2 pos
);
```

### Parameters
<i>sampleSlice </i> [in] uint
The sample slice index.

<i>pos</i> [out] uint2
The index position. Contains the (x, y) coordinates. This method uses a 0-based coordinate system and not a 0.0-1.0 UV system.

### Returns
Type: R

A read-only resource variable.

### Remarks

#### Usage Example

```HLSL
Texture2DMS<float4, 8> tex;

float4 main( float3 tcoord : texturecoord0 ) : SV_Target
{
     return s_msTexture.sample[2][tcoord];
}
```
# Texture2DArray.mips.Operator Method

Reference

## Definition

Returns a read-only resource variable or a Texture2DArray.

#### In this article

*  [Definition](#definition)
*  [Overloads](#overloads)

## Overloads

| Method | Description |
| ------ | ----------- |
| [mips.Operator](#mips.Operator) | Returns a read-only resource variable. |

## mips.Operator {#mips.Operator}

Returns a read-only resource variable.

```HLSL
R mips.Operator[][](
  in uint mipSlice,
  in uint3 pos
);
```

### Parameters
<i>mipSlice </i> [in] uint
The mip slice index.

<i>pos</i> [out] uint3
The index position. The first and second components contain the (x, y) coordinates. This method uses a 0-based coordinate system and not a 0.0-1.0 UV system. The third component indicates the desired array slice.

### Returns
Type: R

A read-only resource variable.

### Remarks

#### Usage Example

```HLSL
Texture2DArray<float4> tex;
uint mip = 2;
uint2 pos_xy_and_array = {123, 456, 3};
float4 f = tex.mips[mip][pos_xy_and_array];
```
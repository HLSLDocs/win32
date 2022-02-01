# Texture2D.mips.Operator Method

Reference

## Definition

Returns a read-only resource variable.

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
  in uint2 pos
);
```

### Parameters
<i>mipSlice </i> [in] uint
The mip slice index.

<i>pos</i> [out] uint2
The index position. Contains the (x, y) coordinates. This method uses a 0-based coordinate system and not a 0.0-1.0 UV system.

### Returns
Type: R

A read-only resource variable.

### Remarks

#### Usage Example

```HLSL
Texture2D<float4> tex;
uint mip = 2;
uint2 pos_xy = {123, 456};
float4 f = tex.mips[mip][pos_xy];
```
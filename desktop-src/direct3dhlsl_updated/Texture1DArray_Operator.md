# Texture1D.Operator Method

Reference

## Definition

Returns a read-only resource variable for a Texture1D.

#### In this article

*  [Definition](#definition)
*  [Overloads](#overloads)

## Overloads

| Method | Description |
| ------ | ----------- |
| [Operator](#Operator) | Returns a read-only resource variable. |

## mips.Operator {#mips.Operator}

Returns a read-only resource variable.

```HLSL
R Operator[](
  in uint2 pos
);
```

### Parameters
<i>pos</i> [out] uint2
The index position. The first component contains the x-coordinate.  This method uses a 0-based coordinate system and not a 0.0-1.0 UV system. The second component indicates the desired array slice.

### Returns
Type: R

A read-only resource variable.

### Remarks

This method always accesses the first mip level. To specify other mip levels, use the mip.operator[][] method instead.

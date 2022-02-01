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
  in uint pos
);
```

### Parameters
<i>pos</i> [in] uint
The index position. Contains the x coordinates. This method uses a 0-based coordinate system and not a 0.0-1.0 UV system.

### Returns
Type: R

A read-only resource variable.

### Remarks

This method always accesses the first mip level. To specify other mip levels, use the mip.operator[][] method instead.

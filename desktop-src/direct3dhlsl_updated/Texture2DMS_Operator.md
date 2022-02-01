# Texture2DMS.Operator Method

Reference

## Definition

Retrieves a value from the resource at the location provided at sample index 0.

#### In this article

*  [Definition](#definition)
*  [Overloads](#overloads)

## Overloads

| Method | Description |
| ------ | ----------- |
| [Operator](#Operator) | Retrieves a value from the resource at the location provided at sample index 0. |

## mips.Operator {#mips.Operator}

Retrieves a value from the resource at the location provided at sample index 0.

```HLSL
R Operator[](
  in uint2 pos
);
```

### Parameters
<i>pos</i> [out] uint2
The index position. Contains the (x, y) coordinates.  This method uses a 0-based coordinate system and not a 0.0-1.0 UV system.

### Returns
Type: R

A read-only resource variable.

### Remarks

To select a particular sample, refer to sample.Operator[][].

This function is supported for the following types of shaders:

# Texture2DMS.GetDimensions Method

Reference

## Definition

Returns the dimensions of the resource.

#### In this article

*  [Definition](#definition)
*  [Overloads](#overloads)

## Overloads

| Method | Description |
| ------ | ----------- |
| [GetDimensions(uint,uint,uint)](#GetDimensions-uint-uint-uint) | Returns the dimensions of the resource. |

## GetDimensions(uint,uint,uint) {#GetDimensions-uint-uint-uint}

Returns the dimensions of the resource.

```HLSL
void GetDimensions(
  out uint Width,
  out uint Height,
  out uint NumberOfSamples
);
```

### Parameters
<i>Width</i> [out] uint
The resource width, in texels.

<i>Height</i> [out] uint
The resource height, in texels.

<i>NumberOfSamples</i> [out] uint
The number of sample locations.

### Returns
Nothing

### Remarks
This is a list of the overloaded versions of this method.

```HLSL
void GetDimensions( 
  out uint Width,
  out uint Height,
  out uint NumberOfSamples);
```
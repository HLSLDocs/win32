# Texture1DArray.GetDimensions Method

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
  in uint MipLevel,
  out uint Width,
  out uint Elements,
  out uint NumberOfLevels
);
```

### Parameters
<i>MipLevel</i> [in] uint
Optional. The mipmap level (must be specified if NumberOfLevels is used).

<i>Width</i> [out] uint
The resource width, in texels.

<i>Elements</i> [out] uint
The number of elements in the array.

<i>NumberOfLevels</i> [out] uint
The number of mipmap levels (requires MipLevel also).

### Returns
Nothing

### Remarks
This is a list of the overloaded versions of this method.

```HLSL

Copy
void GetDimensions(UINT MipLevel, 
  out UINT Width,
  out UINT Elements,
  out UINT NumberOfLevels);

void GetDimensions (out UINT Width,
  out UINT Elements);

void GetDimensions(UINT MipLevel,
  out float Width,
  out UINT Elements,
  out float NumberOfLevels);

void GetDimensions(out float Width,
  out UINT Elements);
```
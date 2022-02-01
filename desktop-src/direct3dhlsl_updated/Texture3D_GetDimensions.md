# Texture3D.GetDimensions Method

Reference

## Definition

Returns the dimensions of the resource.

#### In this article

*  [Definition](#definition)
*  [Overloads](#overloads)

## Overloads

| Method | Description |
| ------ | ----------- |
| [GetDimensions(uint,uint,uint,uint)](#GetDimensions-uint-uint-uint-uint) | Returns the dimensions of the resource. |

## GetDimensions(uint,uint,uint,uint) {#GetDimensions-uint-uint-uint-uint}

Returns the dimensions of the resource.

```HLSL
void GetDimensions(
  in uint MipLevel,
  out uint Width,
  out uint Height,
  out uint NumberOfLevels
);
```

### Parameters
<i>MipLevel</i> [in] uint
Optional. The mipmap level (must be specified if NumberOfLevels is used).

<i>Width</i> [out] uint
The resource width, in texels.

<i>Height</i> [out] uint
The resource height, in texels.

<i>NumberOfLevels</i> [out] uint
The number of mipmap levels (requires MipLevel also).

### Returns
Nothing

### Remarks
This is a list of the overloaded versions of this method.

```HLSL
void GetDimensions(uint MipLevel, 
  out uint Width,
  out uint Height,
  out uint NumberOfLevels);

void GetDimensions (out uint Width,
  out uint Height);

void GetDimensions(uint MipLevel,
  out float Width,
  out float Height,
  out float NumberOfLevels);

void GetDimensions(out float Width,
  out float Height);
```
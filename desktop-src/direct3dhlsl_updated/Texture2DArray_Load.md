# Texture2DArray.Load Method

Reference

## Definition

Reads texture data from a [Texture2DArray](#Texture2DArray.md).

#### In this article

*  [Definition](#definition)
*  [Overloads](#overloads)

## Overloads

| Method | Description |
| ------ | ----------- |
| [Load(int4,int2)](#Load-int4-int2) | Reads texture data. |
| [Load(int4,int2,uint)](#Load-int4-int2-uint) | Reads texture data and returns status of the operation. |

## Load(int4,int2) {#Load-int4-int2}

Returns the dimensions of the resource.

```HLSL
Object Load(
  in  int4 Location,
  in  int2 Offset
);
```

### Parameters
<i>Location</i> [in] int4
The texture coordinates; the first and second components contain the (x, y) coordinates.  This method uses a 0-based coordinate system and not a 0.0-1.0 UV system.  The third component indicates the desired array slice.  The last component specifies the mipmap level.

<i>Offset</i> [in] int2
The offset applied to the texture coordinates before sampling.

### Returns
The return type matches the type in the declaration for the Texture2DArray object.

## Load(int4,int2,uint) {#Load-int4-int2-uint}

Returns the dimensions of the resource.

```HLSL
Load(
  in int4 Location,
  in int2 Offset,
  out uint Status
);
```

### Parameters
<i>Location</i> [in] int
The texture coordinates; the first and second components contain the (x, y) coordinates.  This method uses a 0-based coordinate system and not a 0.0-1.0 UV system.  The third component indicates the desired array slice.  The last component specifies the mipmap level.

<i>Offset</i> [in] int
An offset applied to the texture coordinates before sampling.

<i>Status</i> [out] uint
The status of the operation. You can't access the status directly; instead, pass the status to the CheckAccessFullyMapped intrinsic function. CheckAccessFullyMapped returns TRUE if all values from the corresponding Sample, Gather, or Load operation accessed mapped tiles in a tiled resource. If any values were taken from an unmapped tile, CheckAccessFullyMapped returns FALSE.

### Returns
The return type matches the type in the declaration for the Texture2DArray object.
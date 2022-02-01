# Texture2D.Load Method

Reference

## Definition

Reads texture data from a [Texture2D](#Texture2D.md).

#### In this article

*  [Definition](#definition)
*  [Overloads](#overloads)

## Overloads

| Method | Description |
| ------ | ----------- |
| [Load(int3,int2)](#Load-int3-int2) | Reads texture data. |
| [Load(int3,int2,uint)](#Load-int3-int2-uint) | Reads texture data and returns status of the operation. |

## Load(int3,int2) {#Load-int3-int2}

Reads texture data and returns status of the operation.

```HLSL
Load(
  in  int3 Location,
  in  int2 Offset
);
```

### Parameters
<i>Location</i> [in] int3
The texture coordinates; the first and second components contain the (x, y) coordinates.  This method uses a 0-based coordinate system and not a 0.0-1.0 UV system.  The last component specifies the mipmap level.

<i>Offset</i> [in] int2
The offset applied to the texture coordinates before sampling.

### Returns
The return type matches the type in the declaration for the Texture2D object.

## Load(int3,int2,uint) {#Load-int3-int2-uint}

Reads texture data and returns status of the operation.

```HLSL
Load(
  in  int3 Location,
  in  int2 Offset,
  out uint Status
);
```

### Parameters
<i>Location</i> [in] int3
The texture coordinates; the first and second components contain the (x, y) coordinates.  This method uses a 0-based coordinate system and not a 0.0-1.0 UV system.  The last component specifies the mipmap level.

<i>Offset</i> [in] int2
The offset applied to the texture coordinates before sampling.

<i>Status</i> [out] uint
The status of the operation. You can't access the status directly; instead, pass the status to the CheckAccessFullyMapped intrinsic function. CheckAccessFullyMapped returns TRUE if all values from the corresponding Sample, Gather, or Load operation accessed mapped tiles in a tiled resource. If any values were taken from an unmapped tile, CheckAccessFullyMapped returns FALSE.

### Returns
The return type matches the type in the declaration for the Texture2D object.
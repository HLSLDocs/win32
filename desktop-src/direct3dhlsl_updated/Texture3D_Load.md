# Texture3D.Load Method

Reference

## Definition

Reads texture data from a [Texture3D](#Texture3D.md).

#### In this article

*  [Definition](#definition)
*  [Overloads](#overloads)

## Overloads

| Method | Description |
| ------ | ----------- |
| [Load(int4,int3)](#Load-int4-int3) | Reads texture data. |
| [Load(int4,int3,uint)](#Load-int4-int3-uint) | Reads texture data and returns status of the operation. |

## Load(int4,int3) {#Load-int4-int3}

Reads texture data and returns status of the operation.

```HLSL
Load(
  in  int4 Location,
  in  int3 Offset
);
```

### Parameters
<i>Location</i> [in] int4
The texture coordinates; the first, second, and third components contain the (x, y, z) coordinates.  This method uses a 0-based coordinate system and not a 0.0-1.0 UV system.  The last component specifies the mipmap level.

<i>Offset</i> [in] int3
The offset applied to the texture coordinates before sampling.

### Returns
The return type matches the type in the declaration for the Texture3D object.

## Load(int4,int3,uint) {#Load-int4-int3-uint}

Reads texture data and returns status of the operation.

```HLSL
Load(
  in  int4 Location,
  in  int3 Offset,
  out uint Status
);
```

### Parameters
<i>Location</i> [in] int4
The texture coordinates; the first and second components contain the (x, y, z) coordinates.  This method uses a 0-based coordinate system and not a 0.0-1.0 UV system.  The last component specifies the mipmap level.

<i>Offset</i> [in] int3
The offset applied to the texture coordinates before sampling.

<i>Status</i> [out] uint
The status of the operation. You can't access the status directly; instead, pass the status to the CheckAccessFullyMapped intrinsic function. CheckAccessFullyMapped returns TRUE if all values from the corresponding Sample, Gather, or Load operation accessed mapped tiles in a tiled resource. If any values were taken from an unmapped tile, CheckAccessFullyMapped returns FALSE.

### Returns
The return type matches the type in the declaration for the Texture3D object.
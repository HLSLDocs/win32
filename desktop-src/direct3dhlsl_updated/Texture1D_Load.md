# Texture1D.Load Method

Reference

## Definition

Reads texture data from a [Texture1D](#Texture1D.md).

#### In this article

*  [Definition](#definition)
*  [Overloads](#overloads)

## Overloads

| Method | Description |
| ------ | ----------- |
| [Load(int2,int)](#Load-int2-int) | Reads texture data. |
| [Load(int2,int,uint)](#Load-int2-int-uint) | Reads texture data and returns status of the operation. |

## Load(int2,int) {#Load-int2-int}

Reads texture data.

```HLSL
Object Load(
  in int2 Location,
  in int Offset
);
```

### Parameters
<i>Location</i> [in] int2
The texture coordinate; the first component contains the x coordinates.  This method uses a 0-based coordinate system and not a 0.0-1.0 UV system.  The last component specifies the mipmap level.

<i>Offset</i> [in] int
The offset applied to the texture coordinates before sampling.

### Returns
The return type matches the type in the Object declaration. For example, a Texture1D object that was declared as "Texture1D<uint4> myTexture;" has a return value of type uint4.

## Load(int2,int,uint) {#Load-int2-int-uint}

The return type matches the type in the declaration for the Texture1D object.

```HLSL
Load(
  in int2 Location,
  in int Offset,
  out uint Status
);
```

### Parameters
<i>Location</i> [in] int2
The texture coordinate; the first component contains the x coordinates.  This method uses a 0-based coordinate system and not a 0.0-1.0 UV system.  The last component specifies the mipmap level.

<i>Offset</i> [in] int
An offset applied to the texture coordinates before sampling.

<i>Status</i> [out] uint
The status of the operation. You can't access the status directly; instead, pass the status to the CheckAccessFullyMapped intrinsic function. CheckAccessFullyMapped returns TRUE if all values from the corresponding Sample, Gather, or Load operation accessed mapped tiles in a tiled resource. If any values were taken from an unmapped tile, CheckAccessFullyMapped returns FALSE.

### Returns
The return type matches the type in the Object declaration. For example, a Texture1D object that was declared as "Texture1D<uint4> myTexture;" has a return value of type uint4.
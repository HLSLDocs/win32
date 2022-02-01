# Texture1DArray.Load Method

Reference

## Definition

Reads texture data.

#### In this article

*  [Definition](#definition)
*  [Overloads](#overloads)

## Overloads

| Method | Description |
| ------ | ----------- |
| [Load(int3,int)](#Load-int3-int) | Reads texture data. |
| [Load(int3,int,uint)](#Load-int3-int-uint) | Reads texture data and returns status of the operation. |

## Load(int3,int) {#Load-int3-int}

Returns the dimensions of the resource.

```HLSL
Object Load(
  in  int3  Location,
  in  int  Offset
);
```

### Parameters
<i>Location</i> [in] int3
The texture coordinate; the first component contains the x coordinates.  This method uses a 0-based coordinate system and not a 0.0-1.0 UV system.  The second component indicates the desired array slice.  The last component specifies the mipmap level.

<i>Offset</i> [in] int
An optional offset applied to the texture coordinates before sampling.

### Returns
The return type matches the type in the declaration for the Texture1DArray object.

## Load(int3,int,uint) {#Load-int3-int-uint}

Returns the dimensions of the resource.

```HLSL
Load(
  in int3 Location,
  in int Offset,
  out uint Status
);
```

### Parameters
<i>Location</i> [in] int3
The texture coordinate; the first component contains the x coordinates.  This method uses a 0-based coordinate system and not a 0.0-1.0 UV system.  The second component indicates the desired array slice.  The last component specifies the mipmap level.

<i>Offset</i> [in] int
An offset applied to the texture coordinates before sampling.

<i>Status</i> [out] uint
The status of the operation. You can't access the status directly; instead, pass the status to the CheckAccessFullyMapped intrinsic function. CheckAccessFullyMapped returns TRUE if all values from the corresponding Sample, Gather, or Load operation accessed mapped tiles in a tiled resource. If any values were taken from an unmapped tile, CheckAccessFullyMapped returns FALSE.

### Returns
The return type matches the type in the declaration for the Texture1D object.
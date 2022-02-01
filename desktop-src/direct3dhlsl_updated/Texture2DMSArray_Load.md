# Texture2DMSArray.Load Method

Reference

## Definition

Reads texture data from a [Texture2DMSArray](#Texture2DMSArray.md).

#### In this article

*  [Definition](#definition)
*  [Overloads](#overloads)

## Overloads

| Method | Description |
| ------ | ----------- |
| [Load(int3,int)](#Load-int3-int) | Reads texture data. |
| [Load(int3,int,uint)](#Load-int3-int3-uint) | Reads texture data and returns status of the operation. |

## Load(int3,int) {#Load-int3-int}

Reads texture data and returns status of the operation.

```HLSL
Load(
  in  int3 Location,
  in  int sampleIndex
);
```

### Parameters
<i>Location</i> [in] int3
The texture coordinates; the first and second components contain the (x, y) coordinates.  This method uses a 0-based coordinate system and not a 0.0-1.0 UV system.  The third component indicates the desired array slice.

<i>sampleIndex</i> [in] int
The sample index.

### Returns
The return type matches the type in the declaration for the Texture2DMSArray object.

## Load(int3,int,uint) {#Load-int3-int-uint}

Reads texture data and returns status of the operation.

```HLSL
Load(
  in  int3 Location,
  in  int sampleIndex,
  in  int3 Offset,
  out uint Status
);
```

### Parameters
<i>Location</i> [in] int3
The texture coordinates; the first and second components contain the (x, y) coordinates.  This method uses a 0-based coordinate system and not a 0.0-1.0 UV system.  The third component indicates the desired array slice.

<i>sampleIndex</i> [in] int
The sample index.

<i>Offset</i> [in] int3
The offset applied to the texture coordinates before sampling.

<i>Status</i> [out] uint
The status of the operation. You can't access the status directly; instead, pass the status to the CheckAccessFullyMapped intrinsic function. CheckAccessFullyMapped returns TRUE if all values from the corresponding Sample, Gather, or Load operation accessed mapped tiles in a tiled resource. If any values were taken from an unmapped tile, CheckAccessFullyMapped returns FALSE.

### Returns
The return type matches the type in the declaration for the Texture2DMSArray object.
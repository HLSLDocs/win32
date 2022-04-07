# HLSL RWTexture1D

Object for accessing a read-write 1D texture unordered access view.

You can prefix `RWTexture1D` objects with the storage class `globallycoherent`. This storage class causes memory barriers and syncs to flush data across the entire GPU such that other groups can see writes. Without this specifier, a memory barrier or sync will flush a UAV only within the current group.

A template argument indicates the data type to use in HLSL for the texture element.

```HLSL
RWTexture1D<float> tex;
```

## Methods

| Method | Description |
| - | - |
| [GetDimensions](hlsl-method-getDimensions.md) | Gets texture size information. |
| [Load](hlsl-method-load.md) | Reads texture data. |

## Operators

| Operator | Description |
| - | - |
| [operator\[\]](hlsl-operator.md) | Reads value from buffer. |
# HLSL RWBuffer

A read/write buffer.

A resource variable can also be passed into any unordered or interlocked operation.

`RWBuffer` objects can be prefixed with the storage class `globallycoherent`. This storage class causes memory barriers and syncs to flush data across the entire GPU such that other groups can see writes. Without this specifier, a memory barrier or sync will flush a UAV only within the current group.

```HLSL
// None.
```

## Methods

| Method | Description |
| - | - |
| [GetDimensions](hlsl-method-getDimensions.md) | Gets texture size information. |
| [Load](hlsl-method-load_buffer.md) | Reads `Buffer` data. |

## Operators

| Operator | Description |
| - | - |
| [operator\[\]](hlsl-operator_buffer.md) | Reads value from buffer. |
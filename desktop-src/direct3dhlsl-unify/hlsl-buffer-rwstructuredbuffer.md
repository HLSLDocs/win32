# HLSL RWStructuredBuffer

A read/write buffer that can take a templated type.

A resource variable can also be passed into any unordered or interlocked operation.

`RWStructuredBuffer` objects can be prefixed with the storage class `globallycoherent`. This storage class causes memory barriers and syncs to flush data across the entire GPU such that other groups can see writes. Without this specifier, a memory barrier or sync will only flush a UAV within the current group.

The UAV format bound to this resource needs to be created with the `DXGI_FORMAT_UNKNOWN` format.

To find out more about [`structured buffers`](https://docs.microsoft.com/en-us/windows/desktop/direct3d11/direct3d-11-advanced-stages-cs-resources), see the overview material.

```HLSL
// None.
```

## Methods

| Method | Description |
| - | - |
| [GetDimensions](hlsl-method-getDimensions.md) | Gets texture size information. |
| [Load](hlsl-method-load_buffer.md) | Reads `Buffer` data. |
| [IncrementCounter](hlsl-method-increment-counter.md) | Increments the object's hidden counter. |
| [DecrementCounter](hlsl-method-load_buffer.md) | Decrements the object's hidden counter. |

## Operators

| Operator | Description |
| - | - |
| [operator\[\]](hlsl-operator_buffer.md) | Reads value from buffer. |
# HLSL RWByteAddressBuffer

A read/write buffer that indexes in bytes.

`RWByteAddressBuffer` objects can be prefixed with the storage class `globallycoherent`. This storage class causes memory barriers and syncs to flush data across the entire GPU such that other groups can see writes. Without this specifier, a memory barrier or sync will flush a UAV only within the current group.

The UAV format bound to this resource needs to be created with the `DXGI_FORMAT_R32_TYPELESS` format.

The UAV bound to this resource must have been created with the `D3D11_BUFFER_UAV_FLAG_RAW`.

You can use the `RWByteAddressBuffer` object type when you work with raw buffers. For more info about raw viewing of buffers, see [`Raw Views of Buffers`](https://docs.microsoft.com/en-us/windows/desktop/direct3d11/overviews-direct3d-11-resources-intro).

```HLSL
// None.
```

## Methods

| Method | Description |
| - | - |
| [GetDimensions](hlsl-method-getDimensions.md) | Gets texture size information. |
| [Load](hlsl-method-load_buffer.md) | Reads `Buffer` data. |
| [Store](hlsl-method-store_buffer.md) | Writes `Buffer` data. |
| [InterlockedAdd](hlsl-method-atomic_rwbyteaddressbuffer.md#interlockedadd) | Adds the value, atomically. |
| [InterlockedAnd](hlsl-method-atomic_rwbyteaddressbuffer.md#interlockedand) | Ands the value, atomically. |
| [InterlockedCompareExchange](hlsl-method-atomic_rwbyteaddressbuffer.md#interlockedcompareexchange) | Compares the input to the comparison value and exchanges the result, atomically. |
| [InterlockedCompareStore](hlsl-method-atomic_rwbyteaddressbuffer.md#interlockedcomparestore) | Compares the input to the comparison value, atomically. |
| [InterlockedExchange](hlsl-method-atomic_rwbyteaddressbuffer.md#interlockedexchange) | Compares the input to the comparison value and exchanges the result, atomically. |
| [InterlockedMax](hlsl-method-atomic_rwbyteaddressbuffer.md#interlockedmax) | Finds the maximum value, atomically. |
| [InterlockedMin](hlsl-method-atomic_rwbyteaddressbuffer.md#interlockedmin) | Finds the minimum value, atomically. |
| [InterlockedOr](hlsl-method-atomic_rwbyteaddressbuffer.md#interlockedor) | Performs an atmoic `OR` on the value. |
| [InterlockedXor](hlsl-method-atomic_rwbyteaddressbuffer.md#interlockedxor) | Performs an atmoic `XOR` on the value. |
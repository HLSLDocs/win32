# HLSL RWByteAddressBuffer

A read/write buffer that indexes in bytes.

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
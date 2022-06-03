# Atomic Operations

Support for 64-bit and bitwise floats in [`Shader Model 6.6`](hlsl-appendix-shader-model_6_6.md).

### InterlockedAdd

Atomically adds the provided value to that indicated by dest or indexed in the resource by dest_offset stores the result in that location and optionally returns the original input value through the original_value parameter.

```syntax
void RWByteAddressBuffer::InterlockedAdd64(in uint dest_offset, in int64_t value, out int64_t original_value);
void RWByteAddressBuffer::InterlockedAdd64(in uint dest_offset, in uint64_t value, out uint64_t original_value);

void InterlockedAdd(inout SbufType dest, in int64_t value, out int64_t original_value);
void InterlockedAdd(inout SbufType dest, in uint64_t value, out uint64_t original_value);

void InterlockedAdd(inout TresType dest, in int64_t value, out int64_t original_value);
void InterlockedAdd(inout TresType dest, in uint64_t value, out uint64_t original_value);

void InterlockedAdd(inout ShmemType dest, in int64_t value, out int64_t original_value);
void InterlockedAdd(inout ShmemType dest, in uint64_t value, out uint64_t original_value);
```

### InterlockedAnd

Atomically performs a bitwise AND of the provided unsigned 64-bit integer value and that in the given dest location or indexed in the resource by dest_offset, stores the result in that location and optionally returns the original input value through the original_value parameter.

```syntax
void RWByteAddressBuffer::InterlockedAnd64(in uint dest_offset, in uint64_t value, out uint64_t original_value);
void InterlockedAnd(inout SbufType dest, in uint64_t value, out uint64_t original_value);
void InterlockedAnd(inout TresType dest, in uint64_t value, out uint64_t original_value);
void InterlockedAnd(inout ShmemType dest, in uint64_t value, out uint64_t original_value);
```

### InterlockedOr

Atomically performs a bitwise OR of the provided unsigned 64-bit integer value and that in the given dest location or indexed in the resource by dest_offset, stores the result in that location and optionally returns the original input value through the original_value parameter.

```syntax
void RWByteAddressBuffer::InterlockedOr64(in uint dest_offset, in uint64_t value, out uint64_t original_value);
void InterlockedOr(inout SbufType dest, in uint64_t value, out uint64_t original_value);
void InterlockedOr(inout TresType dest, in uint64_t value, out uint64_t original_value);
void InterlockedOr(inout ShmemType dest, in uint64_t value, out uint64_t original_value);
```

### InterlockedXor

Atomically performs a bitwise XOR(exclusive or) of the provided unsigned 64-bit integer value and that in the given dest location or indexed in the resource by dest_offset, stores the result in that location and optionally returns the original input value through the original_value parameter.

```syntax
void RWByteAddressBuffer::InterlockedXor64(in uint dest_offset, in uint64_t value, out uint64_t original_value);
void InterlockedXor(inout SbufType dest, in uint64_t value, out uint64_t original_value);
void InterlockedXor(inout TresType dest, in uint64_t value, out uint64_t original_value);
void InterlockedXor(inout ShmemType dest, in uint64_t value, out uint64_t original_value);
```

### InterlockedMin

Atomically calculates the smaller of the provided value and that in the given dest location or indexed in the resource by dest_offset, stores the smaller value in that location and optionally returns the original input value through the original_value parameter.

```syntax
void RWByteAddressBuffer::InterlockedMin64(in uint dest_offset, in int64_t value, out int64_t original_value);
void RWByteAddressBuffer::InterlockedMin64(in uint dest_offset, in uint64_t value, out uint64_t original_value);

void InterlockedMin(inout SbufType dest, in int64_t value, out int64_t original_value);
void InterlockedMin(inout SbufType dest, in uint64_t value, out uint64_t original_value);

void InterlockedMin(inout TresType dest, in int64_t value, out int64_t original_value);
void InterlockedMin(inout TresType dest, in uint64_t value, out uint64_t original_value);

void InterlockedMin(inout ShmemType dest, in int64_t value, out int64_t original_value);
void InterlockedMin(inout ShmemType dest, in uint64_t value, out uint64_t original_value);
```

### InterlockedMax

Atomically calculates the larger of the provided value and that in the given dest location or indexed in the resource by dest_offset, stores the larger value in that location and optionally returns the original input value through the original_value parameter.

```syntax
void RWByteAddressBuffer::InterlockedMax64(in uint dest_offset, in int64_t value, out int64_t original_value);
void RWByteAddressBuffer::InterlockedMax64(in uint dest_offset, in uint64_t value, out uint64_t original_value);

void InterlockedMax(inout SbufType dest, in int64_t value, out int64_t original_value);
void InterlockedMax(inout SbufType dest, in uint64_t value, out uint64_t original_value);

void InterlockedMax(inout TresType dest, in int64_t value, out int64_t original_value);
void InterlockedMax(inout TresType dest, in uint64_t value, out uint64_t original_value);

void InterlockedMax(inout ShmemType dest, in int64_t value, out int64_t original_value);
void InterlockedMax(inout ShmemType dest, in uint64_t value, out uint64_t original_value);
```

### InterlockedExchange

Atomically assigns the provided value to the location given by dest or indexed in the resource by dest_offset, and returns the original value from that location through the original_value parameter.

The floating-point overrides of these functions simply use the same operations used by the existing integer functions. As a result, unlike the other functions, these two overrides are supported on SM 6.0 even without capability bits.

```syntax
void RWByteAddressBuffer::InterlockedExchangeFloat(in uint dest_offset, in float value, out float original_value);[issue 3](#issues)
void RWByteAddressBuffer::InterlockedExchange64(in uint dest_offset, in int64_t value, out int64_t original_value);
void RWByteAddressBuffer::InterlockedExchange64(in uint dest_offset, in uint64_t value, out uint64_t original_value);

void InterlockedExchange(inout SbufType dest, in float value, out float original_value);[issue 3](#issues)
void InterlockedExchange(inout SbufType dest, in int64_t value, out int64_t original_value);
void InterlockedExchange(inout SbufType dest, in uint64_t value, out uint64_t original_value);

void InterlockedExchange(inout TresType dest, in float value, out float original_value);[issue 3](#issues)
void InterlockedExchange(inout TresType dest, in int64_t value, out int64_t original_value);
void InterlockedExchange(inout TresType dest, in uint64_t value, out uint64_t original_value);

void InterlockedExchange(inout ShmemType dest, in float value, out float original_value);[issue 3](#issues)
void InterlockedExchange(inout ShmemType dest, in int64_t value, out int64_t original_value);
void InterlockedExchange(inout ShmemType dest, in uint64_t value, out uint64_t original_value);
```

### InterlockedCompareStore

Atomically compares and assigns the indicated value. The value in dest or indexed by dest_offset is compared to compare_value. If they are identical, the provided value is assigned to the that location.

Note that floating-point values are not accepted by InterlockedCompareStore but can be performed using InterlockedCompareStoreFloatBitwise.

```syntax
void RWByteAddressBuffer::InterlockedCompareStore64(in uint dest_offset, in int64_t compare_value, in int64_t value);
void RWByteAddressBuffer::InterlockedCompareStore64(in uint dest_offset, in uint64_t compare_value, in uint64_t value);

void InterlockedCompareStore(inout SbufType dest, in int64_t compare_value, in int64_t value);
void InterlockedCompareStore(inout SbufType dest, in uint64_t compare_value, in uint64_t value);

void InterlockedCompareStore(inout TresType dest, in int64_t compare_value, in int64_t value);
void InterlockedCompareStore(inout TresType dest, in uint64_t compare_value, in uint64_t value);

void InterlockedCompareStore(inout ShmemType dest, in int64_t compare_value, in int64_t value);
void InterlockedCompareStore(inout ShmemType dest, in uint64_t compare_value, in uint64_t value);
```

### InterlockedCompareStoreFloatBitwise

Atomically compares and assigns the indicated floating-point value using a bitwise compare. The value in dest or indexed by dest_offset is compared to compare_value using a bitwise comparison of the value without consideration for floating-point special cases. If they are bitwise identical, the provided value is assigned to the that location.

The floating-point overrides of these functions simply use the same operations used by the existing integer functions. As a result, unlike the other functions, these overrides are supported on SM 6.0 even without capability bits.

```syntax
void RWByteAddressBuffer::InterlockedCompareStoreFloatBitwise(in uint dest_offset, in float compare_value, in float value);
void InterlockedCompareStoreFloatBitwise(inout SbufType dest, in float compare_value, in float value);
void InterlockedCompareStoreFloatBitwise(inout TresType dest, in float compare_value, in float value);
void InterlockedCompareStoreFloatBitwise(inout ShmemType dest, in float compare_value, in float value);
```

### InterlockedCompareExchange

Atomically compares, returns and assigns the indicated value. The value in dest or indexed by dest_offset is compared to compare_value. If they are identical, the provided value is assigned to the that location and the original value from that location is returned through the original_value parameter. After calling this function, the user can determine if the assignment was successful by verifying that compare_value is equal to original_value.

Note that floating-point values are not accepted by InterlockedCompareExchange but can be performed using InterlockedCompareExchangeFloatBitwise.

```syntax
void RWByteAddressBuffer::InterlockedCompareExchange64(in uint dest_offset, in int64_t compare_value, in int64_t value, out int64_t original_value);
void RWByteAddressBuffer::InterlockedCompareExchange64(in uint dest_offset, in uint64_t compare_value, in uint64_t value, out uint64_t original_value);

void InterlockedCompareExchange(inout SbufType dest, in int64_t compare_value, in int64_t value, out int64_t original_value);
void InterlockedCompareExchange(inout SbufType dest, in uint64_t compare_value, in uint64_t value, out uint64_t original_value);

void InterlockedCompareExchange(inout TresType dest, in int64_t compare_value, in int64_t value, out int64_t original_value);
void InterlockedCompareExchange(inout TresType dest, in uint64_t compare_value, in uint64_t value, out uint64_t original_value);

void InterlockedCompareExchange(inout ShmemType dest, in int64_t compare_value, in int64_t value, out int64_t original_value);
void InterlockedCompareExchange(inout ShmemType dest, in uint64_t compare_value, in uint64_t value, out uint64_t original_value);
```

### InterlockedCompareExhcnageFloatBitwise

Atomically compares, returns and assigns the indicated floating-point value using a bitwise compare. The value in dest or indexed by dest_offset is compared to compare_value using a bitwise comparison of the value without consideration for floating-point special cases. If they are bitwise identical, the provided value is assigned to the that location and the original value from that location is returned through the original_value parameter. After calling this function, the user can determine if the assignment was successful by verifying that compare_value is equal to original_value.

The floating-point overrides of these functions simply use the same operations used by the existing integer functions. As a result, unlike the other functions, these overrides are supported on SM 6.0 even without capability bits.

```syntax
void RWByteAddressBuffer::InterlockedCompareExchangeFloatBitwise(in uint dest_offset, in float compare_value, in float value, out float original_value);
void InterlockedCompareExchangeFloatBitwise(inout SbufType dest, in float compare_value, in float value, out float original_value);
void InterlockedCompareExchangeFloatBitwise(inout TresType dest, in float compare_value, in float value, out float original_value);
void InterlockedCompareExchangeFloatBitwise(inout ShmemType dest, in float compare_value, in float value, out float original_value);
```
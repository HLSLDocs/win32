# Load Method (Buffer)

Gets one or more values from read-only buffer.

Method Signatures vary per supported buffer object type:

```syntax
// Buffer
uint Buffer::Load(
        in  uint    address,
    [,  out uint    status ] );

// ByteAddressBuffer
uint ByteAddressBuffer::Load(
        in  uint    address,
    [,  out uint    status ] );

uint2 ByteAddressBuffer::Load2(
        in  uint    address,
    [,  out uint    status ] );

uint3 ByteAddressBuffer::Load3(
        in  uint    address,
    [,  out uint    status ] );

uint4 ByteAddressBuffer::Load4(
        in  uint    address,
    [,  out uint    status ] );

ElementType ByteAddressBuffer<ElementType>::Load(
        in  uint    address,
    [,  out uint    status] );

// StructuredBuffer
ElementType StructuredBuffer<ElementType>::Load(
        in  uint    address,
    [,  out uint    status] );

// RWBuffer
uint RWBuffer::Load(
        in  uint    address,
    [,  out uint    status ] );

// RWByteAddressBuffer
uint RWByteAddressBuffer::Load(
        in  uint    address,
    [,  out uint    status ] );

uint2 RWByteAddressBuffer::Load2(
        in  uint    address,
    [,  out uint    status ] );

uint3 RWByteAddressBuffer::Load3(
        in  uint    address,
    [,  out uint    status ] );

uint4 RWByteAddressBuffer::Load4(
        in  uint    address,
    [,  out uint    status ] );

ElementType RWByteAddressBuffer<ElementType>::Load(
        in  uint    address,
    [,  out uint    status] );

// RWStructuredBuffer
ElementType RWStructuredBuffer<ElementType>::Load(
        in  uint    address,
    [,  out uint    status] );
```

| Parameter | Description |
| - | - |
| in [`uint address`](#uint-address) | The input address.  For `ByteAddressBuffer` and `RWByteAddressBuffer`, must be a multiple of 4. |
| out [`uint status`](#uint-status) | The status of the operation. You can't access the status directly; instead, pass the status to the CheckAccessFullyMapped intrinsic function. CheckAccessFullyMapped returns TRUE if all values from the corresponding Sample, Gather, or Load operation accessed mapped tiles in a tiled resource. If any values were taken from an unmapped tile, CheckAccessFullyMapped returns FALSE. |,.............................

<b>Example</b>

```HLSL
// None.
```

## Return Value

The method mostly returns `uint` values.  The dimensionality of the return value depends on the method signature.

The buffer objects `StructuredBuffer` and `RWStructuredBuffer` return a mandatory templated value.

The buffer objects `ByteAddressBuffer` and `RWByteAddressBuffer` return an optional templated value.

| Buffer Object | Method Signature | Return Type |
| - | - | - |
| `Buffer` | `Load` | `uint` |
| `ByteAddressBuffer` | `Load` | `uint` |
| `ByteAddressBuffer` | `Load2` | `uint2` |
| `ByteAddressBuffer` | `Load3` | `uint3` |
| `ByteAddressBuffer` | `Load4` | `uint4` |
| `ByteAddressBuffer<ElementType>` | `Load` | `ElementType` |
| `StructuredBuffer<ElementType>` | `Load` | `ElementType` |
| `RWBuffer` | `Load` | `uint` |
| `RWByteAddressBuffer` | `Load` | `uint` |
| `RWByteAddressBuffer` | `Load2` | `uint2` |
| `RWByteAddressBuffer` | `Load3` | `uint3` |
| `RWByteAddressBuffer` | `Load4` | `uint4` |
| `RWByteAddressBuffer<ElementType>` | `Load` | `ElementType` |
| `RWStructuredBuffer<ElementType>` | `Load` | `ElementType` |

## Parameters

### `uint address`

The input address.  For `ByteAddressBuffer` and `RWByteAddressBuffer`, must be a multiple of 4.

### `uint status`

The status of the operation. You can't access the status directly; instead, pass the status to the CheckAccessFullyMapped intrinsic function. CheckAccessFullyMapped returns TRUE if all values from the corresponding Sample, Gather, or Load operation accessed mapped tiles in a tiled resource. If any values were taken from an unmapped tile, CheckAccessFullyMapped returns FALSE.

## Remarks

None.

## Supported Shader Models

| Shader Model | 6.0 | 6.1 | 6.2 | 6.3 | 6.4 | 6.5 | 6.6 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Vertex | - | - | - | - | - | - | - |
| Hull | - | - | - | - | - | - | - |
| Domain | - | - | - | - | - | - | - |
| Geometry | - | - | - | - | - | - | - |
| Amplification | - | - | - | - | - | - | 1* |
| Mesh | - | - | - | - | - | - | 1* |
| Pixel | x | x | x | x | x | x | x |
| Compute | - | - | - | - | - | - | x |

| Key | Description |
| - | - |
| x | Supported |
| 1* | Supported with optional feature: `SHADER_FEATURE_DERIVATIVES_IN_MESH_AND_AMPLIFICATION_SHADERS` |

>TBD: Make optional feature into a link

Library `export` function support depends on the entry point that calls the function.
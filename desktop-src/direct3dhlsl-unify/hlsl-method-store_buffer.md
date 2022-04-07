# Store Method (Buffer)

Stores one or more values into a buffer.

```syntax
void RWByteAddressBuffer::Store(
    in  uint    address,
    in  uint    value );
    
void RWByteAddressBuffer<ElementType>::Store(
    in  uint            address,
    in  ElementType     value );

void RWByteAddressBuffer::Store2(
    in  uint    address,
    in  uint2   values );
    
void RWByteAddressBuffer::Store3(
    in  uint    address,
    in  uint3   values );

void RWByteAddressBuffer::Store4(
    in  uint    address,
    in  uint4   values );
```

| Parameter | Description |
| - | - |
| in [`uint address`] | The input address in bytes, which must be a multiple of 4. |
| in [`<StoreValue> values`] | Input values. |

<b>Example</b>

```HLSL
// None.
```

## Return value

None.

## Parameters

### `uint address`

The input address in bytes, which must be a multiple of 4.

### `<StoreValue> values`

Input values.

Type: Depends on method signature as listed in the following table.

| Method Signature | `<StoreValue>` |
| - | - |
| `RWByteAddressBuffer::Store` | `uint` |
| `RWByteAddressBuffer<ElementType>::Store` | `ElementType` |
| `RWByteAddressBuffer::Store2` | `uint2` |
| `RWByteAddressBuffer::Store3` | `uint3` |
| `RWByteAddressBuffer::Store4` | `uint4` |

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
# Operator[] (Buffer)

Reads value from buffer.

RW objects can write values to the buffer object.

Operator signatures vary per supported Buffer Object type.

```syntax
uint Buffer::Operator[](
    in uint pos );

ElementType StructuredBuffer<ElementType>::Operator[](
    in uint pos );

uint RWBuffer::Operator[](
    in uint pos );

ElementType RWStructuredBuffer<ElementType>::Operator[](
    in uint pos );
```

| Parameter | Description |
| - | - |
| in [`uint pos`](#uint-pos) | The index position. |

<b>Example</b>

```HLSL
// None.
```

## Return Value

The `Buffer` and `RWBuffer` objects returns `uint` values.  The dimensionality of the return value depends on the method signature.

The buffer objects `StructuredBuffer` and `RWStructuredBuffer` returns a mandatory templated value.

## Parameters

### `uint pos`

The index position.

## Remarks

This operator always accesses the first mip level. To specify other mip levels, use the mip.operator[][] operator instead.  RW texture objects do not support the mip.operator[][] operator. The texture samples can be used for bilinear interpolation.

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
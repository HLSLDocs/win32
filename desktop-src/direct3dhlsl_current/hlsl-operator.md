# operator[] (Texture)

Reads texel data without any filtering or sampling in the first mip level.

RW objects can write texel data to the texture object.

Operator signatures vary per supported TextureObject type:

### Signatures

#### Texture1D
```syntax
ElementType Texture1D<ElementType>::Operator[](
      in uint pos );
```

#### Texture1DArray
```syntax
ElementType Texture1DArray<ElementType>::Operator[](
      in uint2 pos );
```

#### Texture2D
```syntax
ElementType Texture2D<ElementType>::Operator[](
      in uint2 pos );
```

#### Texture2DArray
```syntax
ElementType Texture2DArray<ElementType>::Operator[](
      in uint3 pos );
```

#### Texture2DMS
```syntax
ElementType Texture2DMS<ElementType>::Operator[](
      in uint2 pos );
```

#### Texture3D
```syntax
ElementType Texture3D<ElementType>::Operator[](
      in uint3 pos );
```

#### RWTexture1D
```syntax
// RW values allow for reading and writing through the Operator[]
ElementType RWTexture1D<ElementType>::Operator[](
      in uint pos );
```

#### RWTexture1DArray
```syntax
ElementType RWTexture1DArray<ElementType>::Operator[](
      in uint2 pos );
```

#### RWTexture2D
```syntax
ElementType RWTexture2D<ElementType>::Operator[](
      in uint2 pos );
```

#### RWTexture2DArray
```syntax
ElementType RWTexture2DArray<ElementType>::Operator[](
      in uint3 pos );
```

#### RWTexture3D
```syntax
ElementType RWTexture3D<ElementType>::Operator[](
      in uint3 pos );
```

## Return Value

The return type matches the type in the Object declaration. For example, a Texture2D object that was declared as "Texture2d<uint4> myTexture;" has a return value of type uint4.

## Parameters

| Parameter | Description |
| - | - |
| in [`<PosType> pos`](#postype-pos) | The index position. |

Types that depend on texture object:

| TextureObject | [`<PosType>`](#postype-pos) |
| --- | --- |
| `Texture1D` | `int` |
| `Texture1DArray` | `int2` |
| `Texture2D` | `int2` |
| `Texture2DArray` | `int3` |
| `Texture2DMS` | `int2` |
| `Texture3D` | `int3` |
| `RWTexture1D` | `int` |
| `RWTexture1DArray` | `int2` |
| `RWTexture2D` | `int2` |
| `RWTexture2DArray` | `int3` |
| `RWTexture3D` | `int3` |

### `<PosType> pos`

 The index position.

Type: Depends on TextureObject.  Types and component meanings are defined in the following table.

| TextureObject | [`<PosType>`](#postype-pos) | Texel Index | Array Slice |
| --- | --- | --- | --- |
| `Texture1D` | `int` | x | - |
| `Texture1DArray` | `int2` | x | y |
| `Texture2D` | `int2` | xy | - |
| `Texture2DArray` | `int3` | xy | z |
| `Texture3D` | `int3` | xyz | - |
| `RWTexture1D` | `int` | x | - |
| `RWTexture1DArray` | `int2` | x | y |
| `RWTexture2D` | `int2` | xy | - |
| `RWTexture2DArray` | `int3` | xy | z |
| `RWTexture3D` | `int3` | xyz | - |

## Remarks

This operator always accesses the first mip level. To specify other mip levels, use the mip.operator[][] operator instead.  RW texture objects do not support the mip.operator[][] operator. The texture samples can be used for bilinear interpolation.

## Example

```HLSL
// None.
```

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
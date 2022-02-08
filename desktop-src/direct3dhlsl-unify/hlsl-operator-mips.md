# mips.Operator[][]

Reads texel data without any filtering or sampling.

Method Signatures vary per supported TextureObject type:

```syntax
ElementType Texture1D<ElementType>::mips.Operator[][](
      in uint mipSlice,
      in uint pos );

ElementType Texture1DArray<ElementType>::mips.Operator[][](
      in uint mipSlice,
      in uint2 pos );

ElementType Texture2D<ElementType>::mips.Operator[][](
      in uint mipSlice,
      in uint2 pos );

ElementType Texture2DArray<ElementType>::mips.Operator[][](
      in uint mipSlice,
      in uint3 pos );

ElementType Texture3D<ElementType>::mips.Operator[][](
      in uint mipSlice,
      in uint3 pos );
```

| Parameter | Description |
| - | - |
| in [`uint mipslice`](#uint-mipslice) | The mip slice index. |
| in [`<PosType> pos`](#postype-pos) | The index position. |

Types that depend on texture object:

| TextureObject | [`<PosType>`](#postype-pos) |
| --- | --- |
| `Texture1D` | `int` |
| `Texture1DArray` | `int2` |
| `Texture2D` | `int2` |
| `Texture2DArray` | `int3` |
| `Texture3D` | `int3` |

<b>Example</b>

```HLSL
Texture3D<float4> tex;
uint mip = 2;
uint3 pos_xyz = {123, 456, 789};
float4 f = tex.mips[mip][pos_xyz];
```

## Return Value

The return type matches the type in the Object declaration. For example, a Texture2D object that was declared as "Texture2d<uint4> myTexture;" has a return value of type uint4.

## Parameters

### `uint mipslice`

The mip slice index.

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
# sample.Operator[][]

Retrieves a value from the resource at the location and sample index provided.

Operator signatures vary per supported TextureObject type:

```syntax
ElementType Texture2DMS<ElementType>::sample.Operator[][](
      in uint sampleSlice,
      in uint2 pos );

ElementType Texture2DArray<ElementType>::sample.Operator[][](
      in uint sampleSlice,
      in uint3 pos );
```

| Parameter | Description |
| - | - |
| in [`uint sampleslice`](#uint-sampleslice) | The sample slice index. |
| in [`<PosType> pos`](#postype-pos) | The index position. |

Types that depend on texture object:

| TextureObject | [`<PosType>`](#postype-pos) |
| --- | --- |
| `Texture2D` | `uint2` |
| `Texture2DArray` | `uint3` |

<b>Example</b>

```HLSL
Texture2DMSArray<float4, 4> alpha;

float4 main( float3 tcoord : texturecoord0 ) : SV_Target
{
     return s_msTexture.sample[2][tcoord];
}
```

## Return Value

The return type matches the type in the Object declaration. For example, a Texture2D object that was declared as "Texture2d<uint4> myTexture;" has a return value of type uint4.

## Parameters

### `uint sampleslice`

The sample slice index.

### `<PosType> pos`

 The index position.

Type: Depends on TextureObject.  Types and component meanings are defined in the following table.

| TextureObject | [`<PosType>`](#postype-pos) | Texel Index | Array Slice |
| --- | --- | --- | --- |
| `Texture2DMS` | `int2` | xy | - |
| `Texture2DMSArray` | `int3` | xy | z |

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
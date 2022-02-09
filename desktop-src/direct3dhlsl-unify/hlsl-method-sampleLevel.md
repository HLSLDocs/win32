# SampleLevel Method

Samples a texture using a mipmap-level offset.

This function is similar to [`Sample`](#hlsl-method-sample.md) except that it uses the LOD level (in the last component of the location parameter) to choose the mipmap level. For example, a 2D texture uses the first two components for uv coordinates and the third component for the mipmap level.

Method Signatures vary per supported TextureObject type:

```syntax
ElementType Texture1D<ElementType>::SampleLevel(
      in  SamplerState  samp,
      in  float         coord,
      in  float         lod,
      in  int           offset,
   [, out uint          status ] );

ElementType Texture1DArray<ElementType>::SampleLevel(
      in  SamplerState  samp,
      in  float2        coord,
      in  float         lod,
      in  int           offset,
   [, out uint          status ] );

ElementType Texture2D<ElementType>::SampleLevel(
      in  SamplerState  samp,
      in  float2        coord,
      in  float         lod,
      in  int2          offset,
   [, out uint          status ] );

ElementType Texture2DArray<ElementType>::SampleLevel(
      in  SamplerState  samp,
      in  float3        coord,
      in  float         lod,
      in  int2          offset,
   [, out uint          status ] );

ElementType Texture3D<ElementType>::SampleLevel(
      in  SamplerState  samp,
      in  float3        coord,
      in  float         lod,
      in  int3          offset,
   [, out uint          status ] );

ElementType TextureCube<ElementType>::SampleLevel(
      in  SamplerState  samp,
      in  float3        coord,
      in  float         lod,
   [, out uint          status ] );

ElementType TextureCubeArray<ElementType>::SampleLevel(
      in  SamplerState  samp,
      in  float4        coord,
      in  float         lod,
   [, out uint          status ] );
```

| Parameter | Description |
| - | - |
| in [`SamplerState samp`](#samplerstate-samp) | SamplerState object that determines how sampling will take place. |
| in [`<CoordType> coord`](#coordtype-coord) | The texture coordinates. |
| in [`float lod`](#float-lod) | A number that specifies the mipmap level. If the value is = 0, the zero'th (biggest map) is used. The fractional value (if supplied) is used to interpolate between two mipmap levels. |
| in [`<OffsetType> offset`](#offsettype-offset) | The offset applied to the texture coordinates before sampling. |
| \[ out [`uint status`](#uint-status) \] | The status of the operation. You can't access the status directly; instead, pass the status to the CheckAccessFullyMapped intrinsic function. CheckAccessFullyMapped returns TRUE if all values from the corresponding Sample, Gather, or Load operation accessed mapped tiles in a tiled resource. If any values were taken from an unmapped tile, CheckAccessFullyMapped returns FALSE. |

Types that depend on texture object:

| TextureObject | [`<CoordType>`](#coordtype-coord) | [`<OffsetType>`](#offsettype-offset) |
| --- | --- | --- |
| `Texture1D` | `float` | `int` |
| `Texture1DArray` | `float2` | `int` |
| `Texture2D` | `float2` | `int2` |
| `Texture2DArray` | `float3` | `int2` |
| `Texture3D` | `float3` | `int3` |
| `TextureCube` | `float3` | N/A |
| `TextureCubeArray` | `float4` | N/A |

<b>Example</b>

```HLSL
// Object Declarations
Texture1D g_txRandom;

SamplerState g_samPoint
{
    Filter = MIN_MAG_MIP_POINT;
    AddressU = Wrap;
    AddressV = Wrap;
};

    
// Shader body calling the intrinsic function
float3 RandomDir(float fOffset)
{   
    float tCoord = (fOffset) / 300.0;
    return g_txRandom.SampleLevel( g_samPoint, tCoord, 0 );
   ...
```

## Return Value

The texture's template type for the element, which may be a scalar or vector.
This provides the HLSL type for an element loaded from a texture.
The format stored in the resource is based on the texture resource view's DXGI_FORMAT,
which will determine how data is translated into the type specified in HLSL.

## Parameters

### `SamplerState samp`

A Sampler state. This is an object declared in an effect file that contains state assignments.

> My alternate text:
> SamplerState object that determines how sampling will take place.

Type: `SamplerState`

> TBD: Link to document describing SamplerState object.

### `<CoordType> coord`

The texture coordinates.  The argument type is dependent on the texture-object type.

| TextureObject | `<CoordType>` | x,y,z texel coord | Array Index |
| --------------- | ------------ | ------------ | ----------- |
| `Texture1D` | `float` | x | - |
| `Texture1DArray` | `float2` | x | y |
| `Texture2D` | `float2` | xy | - |
| `Texture2DArray` | `float3` | xy | z |
| `Texture3D` | `float3` | xyz | - |
| `TextureCube` | `float3` | xyz | - |
| `TextureCubeArray` | `float4` | xyz | w |

### `float lod`

A number that specifies the mipmap level. If the value is = 0, the zero'th (biggest map) is used. The fractional value (if supplied) is used to interpolate between two mipmap levels.

### `<OffsetType> offset`

An optional texture coordinate offset, which can be used for any texture-object type; the offset is applied to the coord before sampling. The texture offsets need to be static. The argument type is dependent on the texture-object type. For more info, see Applying texture coordinate offsets.

> My alternate text:
> An integral offset in texels from the sampling coord in the texture.
> Each component must be an immediate value in the range of `[-8,7]` known at compile time.
> Cannot be used with TextureCube or TextureCubeArray objects.

Type: Depends on TextureObject.  Types and component meanings are defined in the following table.

| TextureObject | `<OffsetType>` | Integer offset in texels |
| --------------- | ------------ | ------------ |
| `Texture1D` | `int` | x |
| `Texture1DArray` | `int` | x |
| `Texture2D` | `int2` | xy |
| `Texture2DArray` | `int2` | xy |
| `Texture3D` | `int3` | xyz |

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
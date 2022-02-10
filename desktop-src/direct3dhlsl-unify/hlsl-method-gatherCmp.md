# GatherCmp Method

Gets the four samples that would be used for bilinear interpolation when sampling a texture.

Method Signatures vary per supported TextureObject type:

### `All Channels`

```syntax
ElementType Texture2D<ElementType>::GatherCmp(
      in  SamplerState  samp,
      in  float2        coord,
      in  float         compareValue,
      in  int2          offset,
   [, out uint          status ] );

ElementType Texture2DArray<ElementType>::GatherCmp(
      in  SamplerState  samp,
      in  float3        coord,
      in  float         compareValue,
      in  int2          offset,
   [, out uint          status ] );

ElementType TextureCube<ElementType>::GatherCmp(
      in  SamplerState  samp,
      in  float3        coord,
      in  float         compareValue,
   [, out uint          status ] );

ElementType TextureCubeArray<ElementType>::GatherCmp(
      in  SamplerState  samp,
      in  float4        coord,
      in  float         compareValue,
   [, out uint          status ] );
```

### `Red Channel`

```syntax
ElementType Texture2D<ElementType>::GatherCmpRed(
      in  SamplerState  samp,
      in  float2        coord,
      in  float         compareValue,
      in  int2          offset,
   [, in  int2          offset2]
   [, in  int2          offset3]
   [, in  int2          offset4]   
   [, out uint          status ] );

ElementType Texture2DArray<ElementType>::GatherCmpRed(
      in  SamplerState  samp,
      in  float3        coord,
      in  float         compareValue,
      in  int2          offset,
   [, in  int2          offset2]
   [, in  int2          offset3]
   [, in  int2          offset4]
   [, out uint          status ] );

ElementType TextureCube<ElementType>::GatherCmpRed(
      in  SamplerState  samp,
      in  float3        coord,
      in  float         compareValue,
   [, out uint          status ] );

ElementType TextureCubeArray<ElementType>::GatherCmpRed(
      in  SamplerState  samp,
      in  float4        coord,
      in  float         compareValue,
   [, out uint          status ] );
```

### `Green Channel`

```syntax
ElementType Texture2D<ElementType>::GatherCmpGreen(
      in  SamplerState  samp,
      in  float2        coord,
      in  float         compareValue,
      in  int2          offset,
   [, in  int2          offset2]
   [, in  int2          offset3]
   [, in  int2          offset4]   
   [, out uint          status ] );

ElementType Texture2DArray<ElementType>::GatherCmpGreen(
      in  SamplerState  samp,
      in  float3        coord,
      in  float         compareValue,
      in  int2          offset,
   [, in  int2          offset2]
   [, in  int2          offset3]
   [, in  int2          offset4]
   [, out uint          status ] );

ElementType TextureCube<ElementType>::GatherCmpGreen(
      in  SamplerState  samp,
      in  float3        coord,
      in  float         compareValue,
   [, out uint          status ] );

ElementType TextureCubeArray<ElementType>::GatherCmpGreen(
      in  SamplerState  samp,
      in  float4        coord,
      in  float         compareValue,
   [, out uint          status ] );
```

### `Blue Channel`

```syntax
ElementType Texture2D<ElementType>::GatherCmpBlue(
      in  SamplerState  samp,
      in  float2        coord,
      in  float         compareValue,
      in  int2          offset,
   [, in  int2          offset2]
   [, in  int2          offset3]
   [, in  int2          offset4]   
   [, out uint          status ] );

ElementType Texture2DArray<ElementType>::GatherCmpBlue(
      in  SamplerState  samp,
      in  float3        coord,
      in  float         compareValue,
      in  int2          offset,
   [, in  int2          offset2]
   [, in  int2          offset3]
   [, in  int2          offset4]
   [, out uint          status ] );

ElementType TextureCube<ElementType>::GatherCmpBlue(
      in  SamplerState  samp,
      in  float3        coord,
      in  float         compareValue,
   [, out uint          status ] );

ElementType TextureCubeArray<ElementType>::GatherCmpBlue(
      in  SamplerState  samp,
      in  float4        coord,
      in  float         compareValue,
   [, out uint          status ] );
```

### `Alpha Channel`

```syntax
ElementType Texture2D<ElementType>::GatherCmpAlpha(
      in  SamplerState  samp,
      in  float2        coord,
      in  float         compareValue,
      in  int2          offset,
   [, in  int2          offset2]
   [, in  int2          offset3]
   [, in  int2          offset4]   
   [, out uint          status ] );

ElementType Texture2DArray<ElementType>::GatherCmpAlpha(
      in  SamplerState  samp,
      in  float3        coord,
      in  float         compareValue,
      in  int2          offset,
   [, in  int2          offset2]
   [, in  int2          offset3]
   [, in  int2          offset4]
   [, out uint          status ] );

ElementType TextureCube<ElementType>::GatherCmpAlpha(
      in  SamplerState  samp,
      in  float3        coord,
      in  float         compareValue,
   [, out uint          status ] );

ElementType TextureCubeArray<ElementType>::GatherCmpAlpha(
      in  SamplerState  samp,
      in  float4        coord,
      in  float         compareValue,
   [, out uint          status ] );
```

| Parameter | Description |
| - | - |
| in [`SamplerState samp`](#samplerstate-samp) | SamplerState object that determines how sampling will take place. |
| in [`<CoordType> coord`](#coordtype-coord) | The texture coordinates. |
| in [`float compareValue`](#float-comparevalue) | A value to compare each against each sampled value. |
| in [`<OffsetType> offset`](#offsettype-offset) | The offset applied to the texture coordinates before sampling. |
| \[ out [`uint status`](#uint-status) \] | The status of the operation. You can't access the status directly; instead, pass the status to the CheckAccessFullyMapped intrinsic function. CheckAccessFullyMapped returns TRUE if all values from the corresponding Sample, Gather, or Load operation accessed mapped tiles in a tiled resource. If any values were taken from an unmapped tile, CheckAccessFullyMapped returns FALSE. |

Types that depend on texture object:

| TextureObject | [`<CoordType>`](#coordtype-coord) | [`<OffsetType>`](#offsettype-offset) |
| --- | --- | --- |
| `Texture2D` | `float2` | `int2` |
| `Texture2DArray` | `float3` | `int2` |
| `TextureCube` | `float3` | N/A |
| `TextureCubeArray` | `float4` | N/A |

<b>Example</b>

```HLSL
// N/A
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
| `Texture2D` | `float2` | xy | - |
| `Texture2DArray` | `float3` | xy | z |
| `TextureCube` | `float3` | xyz | - |
| `TextureCubeArray` | `float4` | xyz | w |

### `float compareValue`

A value to compare each against each sampled value.

### `<OffsetType> offset`

An optional texture coordinate offset, which can be used for any texture-object type; the offset is applied to the coord before sampling. The texture offsets need to be static. The argument type is dependent on the texture-object type. For more info, see Applying texture coordinate offsets.

> My alternate text:
> An integral offset in texels from the sampling coord in the texture.
> Each component must be an immediate value in the range of `[-8,7]` known at compile time.
> Cannot be used with TextureCube or TextureCubeArray objects.

Type: Depends on TextureObject.  Types and component meanings are defined in the following table.

| TextureObject | `<OffsetType>` | Integer offset in texels |
| --------------- | ------------ | ------------ |
| `Texture2D` | `int2` | xy |
| `Texture2DArray` | `int2` | xy |

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
# SampleGrad

Samples a texture using a gradient to influence the way the sample location is calculated.

Method Signatures vary per supported TextureObject type:

### Signatures

#### Texture1D
```syntax
ElementType Texture1D<ElementType>::SampleGrad(
      in  SamplerState  samp,
      in  float         coord,
      in  float         ddx,
      in  float         ddy,
      in  int           offset,
   [, in  float         clamp ]
   [, out uint          status ] );
```

#### Texture1DArray
```syntax
ElementType Texture1DArray<ElementType>::SampleGrad(
      in  SamplerState  samp,
      in  float2        coord,
      in  float         ddx,
      in  float         ddy,
      in  int           offset,
   [, in  float         clamp ]
   [, out uint          status ] );
```

#### Texture2D
```syntax
ElementType Texture2D<ElementType>::SampleGrad(
      in  SamplerState  samp,
      in  float2        coord,
      in  float2        ddx,
      in  float2        ddy,
      in  int2          offset,
   [, in  float         clamp ]
   [, out uint          status ] );
```

#### Texture2DArray
```syntax
ElementType Texture2DArray<ElementType>::SampleGrad(
      in  SamplerState  samp,
      in  float3        coord,
      in  float2        ddx,
      in  float2        ddy,
      in  int2          offset,
   [, in  float         clamp ]
   [, out uint          status ] );
```

#### Texture3D
```syntax
ElementType Texture3D<ElementType>::SampleGrad(
      in  SamplerState  samp,
      in  float3        coord,
      in  float3        ddx,
      in  float3        ddy,
      in  int3          offset,
   [, in  float         clamp ]
   [, out uint          status ] );
```

#### TextureCube
```syntax
ElementType TextureCube<ElementType>::SampleGrad(
      in  SamplerState  samp,
      in  float3        coord,
      in  float3        ddx,
      in  float3        ddy,
   [, in  float         clamp ]
   [, out uint          status ] );
```

#### TextureCubeArray
```syntax
ElementType TextureCubeArray<ElementType>::SampleGrad(
      in  SamplerState  samp,
      in  float4        coord,
      in  float3        ddx,
      in  float3        ddy,
   [, in  float         clamp ]
   [, out uint          status ] );
```

## Return Value

The texture's template type for the element, which may be a scalar or vector.
This provides the HLSL type for an element loaded from a texture.
The format stored in the resource is based on the texture resource view's DXGI_FORMAT,
which will determine how data is translated into the type specified in HLSL.

## Parameters

| Parameter | Description |
| - | - |
| in [`SamplerState samp`](#samplerstate-samp) | SamplerState object that determines how sampling will take place. |
| in [`<CoordType> coord`](#coordtype-coord) | The texture coordinates. |
| in [`<DdxType> ddx`](#ddxtype-ddx) | The rate of change of the surface geometry in the x direction. |
| in [`<DdyType> ddy`](#ddytype-ddy) | The rate of change of the surface geometry in the y direction. |
| in [`<OffsetType> offset`](#offsettype-offset) | The offset applied to the texture coordinates before sampling. |
| \[ in [`float clamp`](#float-clamp) \] | An optional value to clamp sample LOD values to. For example, if you pass 2.0f for the clamp value, you ensure that no individual sample accesses a mip level less than 2.0f. |
| \[ out [`uint status`](#uint-status) \] | The status of the operation. You can't access the status directly; instead, pass the status to the CheckAccessFullyMapped intrinsic function. CheckAccessFullyMapped returns TRUE if all values from the corresponding Sample, Gather, or Load operation accessed mapped tiles in a tiled resource. If any values were taken from an unmapped tile, CheckAccessFullyMapped returns FALSE. |

Types that depend on texture object:

| TextureObject | [`<CoordType>`](#coordtype-coord) | [`<DdxType>`](#ddxtype-ddx) | [`<DdyType>`](#ddytype-ddy) | [`<OffsetType>`](#offsettype-offset) |
| --- | --- | --- | --- | --- |
| `Texture1D` | `float` | `float` | `float` | `int` |
| `Texture1DArray` | `float2` | `float` | `float` | `int` |
| `Texture2D` | `float2` | `float2` | `float2` | `int2` |
| `Texture2DArray` | `float3` | `float2` | `float2` | `int2` |
| `Texture3D` | `float3` | `float3` | `float3` | `int3` |
| `TextureCube` | `float3` | `float3` | `float3` | N/A |
| `TextureCubeArray` | `float4` | `float3` | `float3` | N/A |

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

### `<DdxType> ddx`

The rate of change of the surface geometry in the x direction. The argument type is dependent on the texture-object type.

| TextureObject | `<DdxType>` | x change rate |
| --------------- | ------------ | ------------ |
| `Texture1D` | `float` | x |
| `Texture1DArray` | `float` | x |
| `Texture2D` | `float2` | xy |
| `Texture2DArray` | `float2` | xy |
| `Texture3D` | `float3` | xyz |
| `TextureCube` | `float3` | xyz |
| `TextureCubeArray` | `float3` | xyz |

### `<DdyType> ddy`

The rate of change of the surface geometry in the y direction. The argument type is dependent on the texture-object type.

| TextureObject | `<DdxType>` | y change rate |
| --------------- | ------------ | ------------ |
| `Texture1D` | `float` | x |
| `Texture1DArray` | `float` | x |
| `Texture2D` | `float2` | xy |
| `Texture2DArray` | `float2` | xy |
| `Texture3D` | `float3` | xyz |
| `TextureCube` | `float3` | xyz |
| `TextureCubeArray` | `float3` | xyz |

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

### `float clamp`

An optional value to clamp sample LOD values to. For example, if you pass 2.0f for the clamp value, you ensure that no individual sample accesses a mip level less than 2.0f.

### `uint status`

The status of the operation. You can't access the status directly; instead, pass the status to the CheckAccessFullyMapped intrinsic function. CheckAccessFullyMapped returns TRUE if all values from the corresponding Sample, Gather, or Load operation accessed mapped tiles in a tiled resource. If any values were taken from an unmapped tile, CheckAccessFullyMapped returns FALSE.

## Remarks

None.


## Example

```HLSL
// Object Declarations
Texture2D g_txDiffuse;

SamplerState g_samLinear
{
    Filter = ANISOTROPIC;
    MaxAnisotropy = 8;
    AddressU = Wrap;
    AddressV = Wrap;
};

struct VSSceneOut
{
    float4 Pos : SV_POSITION;
    float4 Color : COLOR0;
    float2 Tex : TEXCOORD;
    float2 Aniso : ANISOTROPY;
};

float4 PSSceneMain( VSSceneOut Input ) : SV_TARGET
{
    float2 ddx = Input.Aniso;
    float2 ddy = Input.Aniso;
    
    // Shader body calling the intrinsic function
    float4 diff = g_txDiffuse.SampleGrad( g_samLinear, Input.Tex, ddx, ddy);
    
    ...
}
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
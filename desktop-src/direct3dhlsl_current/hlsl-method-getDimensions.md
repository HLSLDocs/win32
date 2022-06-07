# GetDimensions

Gets texture size information.

### Signatures

#### Texture1D
```syntax
void Texture1D<ElementType>::GetDimensions(
      in  uint  mipLevel,
      out uint  width,
      out uint  numberOfLevels );

void Texture1D<ElementType>::GetDimensions(
      out uint  width );

void Texture1D<ElementType>::GetDimensions(
      in  uint  mipLevel,
      out float width,
      out float numberOfLevels );

void Texture1D<ElementType>::GetDimensions(
      out float width );
```

#### Texture1DArray
```syntax
// Texture1DArray
void Texture1DArray<ElementType>::GetDimensions(
      in  uint  mipLevel,
      out uint  width,
      out uint  elements,
      out uint  numberOfLevels );

void Texture1DArray<ElementType>::GetDimensions(
      out uint  width,
      out uint  numberOfLevels );

void Texture1DArray<ElementType>::GetDimensions(
      in uint   mipLevel,
      out float width,
      out uint  elements,
      out float numberOfLevels );

void Texture1DArray<ElementType>::GetDimensions(
      out float width,
      out uint elements );
```

#### Texture2D
```syntax
// Texture2D
void Texture2D<ElementType>::GetDimensions(
      in  uint  mipLevel,
      out uint  width,
      out uint  height,
      out uint  numberOfLevels );

void Texture2D<ElementType>::GetDimensions(
      out uint  width,
      out uint  height );

void Texture2D<ElementType>::GetDimensions(
      in  uint  mipLevel,
      out float width,
      out float height,
      out float numberOfLevels );

void Texture2D<ElementType>::GetDimensions(
      out float width,
      out float height );
```

#### Texture2DArray
```syntax
// Texture2DArray
void Texture2DArray<ElementType>::GetDimensions(
      in  uint  mipLevel,
      out uint  width,
      out uint  height,
      out uint  elements,
      out uint  numberOfLevels );

void Texture2DArray<ElementType>::GetDimensions(
      out uint  width,
      out float height,
      out float elements );

void Texture2DArray<ElementType>::GetDimensions(
      in  uint   mipLevel,
      out float  width,
      out float  height,
      out float  elements,
      out float  numberOfLevels );

void Texture2DArray<ElementType>::GetDimensions(
      out float  width,
      out float  height,
      out float  elements );
```

#### Texture3D
```syntax
// Texture3D
void Texture3D<ElementType>::GetDimensions(
      in  uint  mipLevel,
      out uint  width,
      out uint  height,
      out uint  depth,
      out uint  numberOfLevels );

void Texture3D<ElementType>::GetDimensions(
      out uint  width,
      out uint  height,
      out uint  depth );

void Texture3D<ElementType>::GetDimensions(
      in  uint  mipLevel,
      out float width,
      out float height,
      out float depth,
      out float numberOfLevels );

void Texture3D<ElementType>::GetDimensions(
      out float width,
      out float height,
      out float depth );
```

#### Texture2DMS
```syntax
// Texture2DMS
void Texture2DMS<ElementType>::GetDimensions(
      out uint  width,
      out uint  height,
      out uint  numberOfSamples );
```

#### Texture2DMSArray
```syntax
// Texture2DMSArray
void Texture2DMSArray<ElementType>::GetDimensions(
      out uint  width,
      out uint  height,
      out uint  elements,
      out uint  numberOfSamples );
```

#### Buffer
```syntax
// Buffer
void Buffer::GetDimensions(
      out uint dim );
```

#### ByteAddressBuffer
```syntax
// ByteAddressBuffer
void Buffer::GetDimensions(
      out uint dim );
```

#### StructuredBuffer
```syntax
// StructuredBuffer
void StructuredBuffer<ElementType>::GetDimensions(
      out uint numStructs,
      out uint stride );
```

#### RWTexture1D
```syntax
// RWTexture1D
void RWTexture1D<ElementType>::GetDimensions(
      out uint width );
```

#### RWTexture1DArray
```syntax
// RWTexture1DArray
void RWTexture1DArray<ElementType>::GetDimensions(
      out uint width,
      out uint elements );
```

#### RWTexture2D
```syntax
// RWTexture2D
void RWTexture2D<ElementType>::GetDimensions(
      out uint width,
      out uint height );
```

#### RWTexture2DArray
```syntax
// RWTexture2DArray
void RWTexture2DArray<ElementType>::GetDimensions(
      out uint width,
      out uint height,
      out uint elements );
```

#### RWTexture3D
```syntax
// RWTexture3D
void RWTexture3D<ElementType>::GetDimensions(
      out uint width,
      out uint height,
      out uint depth );
```

#### RWBuffer
```syntax
// RWBuffer
void RWBuffer::GetDimensions(
      out uint dim );
```

#### RWByteAddressBuffer
```syntax
// RWByteAddressBuffer
void RWByteAddressBuffer::GetDimensions(
      out uint dim );
```

#### RWStructuredBuffer
```syntax
// RWStructuredBuffer
void RWStructuredBuffer<ElementType>::GetDimensions(
      out uint numStructs,
      out uint stride );
```

#### AppendStructuredBuffer
```syntax
// AppendStructuredBuffer
void AppendStructuredBuffer<ElementType>::GetDimensions(
      out uint numStructs,
      out uint stride );
```

#### ConsumeStructuredBuffer
```syntax
// ConsumeStructuredBuffer
void ConsumeStructuredBuffer<ElementType>::GetDimensions(
      out uint numStructs,
      out uint stride );
```

## Return Value

None.

## Parameters

| Parameter | Description |
| - | - |
| in [`uint mipLevel`](#uint-miplevel) | A zero-based index that identifies the mipmap level. If this argument is not used, the first mip level is assumed. |
| out [`<UintFloat> width`](#uintfloat-width) | The texture width, in texels. |
| out [`<UintFloat> numberOfLevels`](#uintfloat-numberOfLevels) | The number of mipmap levels. |
| out [`<UintFloat> elements`](#uintfloat-elements) | The number of elements in an array. |
| out [`<UintFloat> height`](#uintfloat-height) | The texture height, in texels. |
| out [`<UintFloat> depth`](#uintfloat-depth) | The texture depth, in texels. |
| out [`uint numberOfSamples`](#uint-numberofsamples) | The number of samples. |
| out [`uint dim`](#uint-dim) | The length, in bytes, of the buffer. |
| out [`uint numStructs`](#uint-numstructs) | The number of structures in the resource. |
| out [`uint stride`](#uint-stride) | The stride, in bytes, of each structure element. |

### `uint mipLevel`

A zero-based index that identifies the mipmap level. If this argument is not used, the first mip level is assumed.

### `<UintFloat> width`

The texture width, in texels.

Can be uint or float.

### `<UintFloat> numberOfLevels`

The number of mipmap levels.

Can be uint or float.

### `<UintFloat> elements`

The number of elements in an array.

Can be uint or float.

### `<UintFloat> height`

The texture height, in texels.

Can be uint or float.

### `<UintFloat> depth`

The texture depth, in texels.

Can be uint or float.

### `uint numberOfSamples`

The number of samples.

### `uint dim`

The length, in bytes, of the buffer.

### `uint numStructs`

The number of structures in the resource.

### `uint stride`

The stride, in bytes, of each structure element.

## Remarks

None.

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
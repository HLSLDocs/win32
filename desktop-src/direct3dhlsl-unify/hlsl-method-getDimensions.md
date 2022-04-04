# GetDimensions

Gets texture size information.

```syntax
// Texture1D
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

// Texture2DMS
void Texture2DMS<ElementType>::GetDimensions(
      out uint  width,
      out uint  height,
      out uint  numberOfSamples );

// Texture2DMSArray
void Texture2DMSArray<ElementType>::GetDimensions(
      out uint  width,
      out uint  height,
      out uint  elements,
      out uint  numberOfSamples );

// Buffer
void Buffer::GetDimensions(
      out uint dim );

// ByteAddressBuffer
void Buffer::GetDimensions(
      out uint dim );

// StructuredBuffer
void StructuredBuffer<ElementType>::GetDimensions(
      out uint numStructs,
      out uint stride );

// RWTexture1D
void RWTexture1D<ElementType>::GetDimensions(
      out uint width );

// RWTexture1DArray
void RWTexture1DArray<ElementType>::GetDimensions(
      out uint width,
      out uint elements );

// RWTexture2D
void RWTexture2D<ElementType>::GetDimensions(
      out uint width,
      out uint height );

// RWTexture2DArray
void RWTexture2DArray<ElementType>::GetDimensions(
      out uint width,
      out uint height,
      out uint elements );

// RWTexture3D
void RWTexture3D<ElementType>::GetDimensions(
      out uint width,
      out uint height,
      out uint depth );

// RWBuffer
void RWBuffer::GetDimensions(
      out uint dim );

// RWByteAddressBuffer
void RWByteAddressBuffer::GetDimensions(
      out uint dim );

// RWStructuredBuffer
void RWStructuredBuffer<ElementType>::GetDimensions(
      out uint numStructs,
      out uint stride );

// AppendStructuredBuffer
void AppendStructuredBuffer<ElementType>::GetDimensions(
      out uint numStructs,
      out uint stride );

// ConsumeStructuredBuffer
void ConsumeStructuredBuffer<ElementType>::GetDimensions(
      out uint numStructs,
      out uint stride );
```

| Parameter | Description |
| - | - |
| in [`uint mipLevel`](#uint-mipLevel) | A zero-based index that identifies the mipmap level. If this argument is not used, the first mip level is assumed. |
| out [`<UintFloat> width`](#uint-width) | The texture width, in texels. |
| out [`<UintFloat> numberOfLevels`](#uint-numberOfLevels) | The number of mipmap levels. |
| out [`<UintFloat> elements`](#uint-elements) | The number of elements in an array. |
| out [`<UintFloat> height`](#uint-height) | The texture height, in texels. |
| out [`<UintFloat> depth`](#uint-depth) | The texture depth, in texels. |
| out [`uint numberOfSamples`](#uint-numberOfSamples) | The number of samples. |
| out [`uint dim`](#uint-dim) | The length, in bytes, of the buffer. |
| out [`uint numStructs`](#uint-numStructs) | The number of structures in the resource. |
| out [`uint stride`](#uint-stride) | The stride, in bytes, of each structure element. |

<b>Example</b>

```HLSL
// None.
```

## Return Value

None.

## Parameters

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
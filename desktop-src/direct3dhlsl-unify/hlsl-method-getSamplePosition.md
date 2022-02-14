# GetSamplePosition

Gets the sample position for the sample index provided.

```syntax
// Texture2DMS
float2 Texture2DMS<ElementType>::GetSamplePosition(
      in int2 sampleIndex );

// Texture2DMSArray
float2 Texture2DMSArray<ElementType>::GetSamplePosition(
      in int2 sampleIndex );
```

| Parameter | Description |
| - | - |
| in [`int sampleIndex`](#uint-sampleIndex) | The zero-based index of a sample location. |

<b>Example</b>

```HLSL
// None.
```

## Return Value

Type: float2

A sample location.

## Parameters

### `int sampleIndex`

The zero-based index of a sample location.

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
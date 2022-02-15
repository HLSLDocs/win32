# HLSL Texture1DArray Object

Object for accessing a read-only 1D texture array shader resource view.  See [SRV Textures](hlsl-resource-objects.md#srv-textures).
A template argument indicates the data type to use in HLSL for the texture element.
Textures are typed resources, so a data conversion step will translate between the DXGI_FORMAT and the element type declared in HLSL.

```HLSL
// prototype
template<typename ElementType = float4> class Texture1DArray;

// example declarations:
Texture1DArray ColorTexture;
Texture1DArray<float> DepthTexture;
```

## Methods

| Method | Description |
| - | - |
| [GetDimensions](#hlsl-method-getDimensions.md) | Gets texture size information. |
| [Load](#hlsl-method-load.md) | Reads texel data without any filtering or sampling. |
| [Sample](#hlsl-method-sample.md) | Samples a texture. |
| [SampleBias](#hlsl-method-sampleBias.md) | Samples a texture, after applying the bias value to the mipmap level. |
| [SampleCmp](#hlsl-method-sampleCmp-separated.md) | Samples a texture and returns the comparison against a provided value. |
| [SampleCmpLevelZero](#hlsl-method-sampleCmpLevelZero.md) | Samples a texture on mip level zero and returns the comparison against a provided value. |
| [SampleGrad](#hlsl-method-sampleGrad.md) | Samples a texture using a gradient to influence the way the sample location is calculated. |
| [SampleLevel](#hlsl-method-sampleLevel.md) | Samples a texture using a mipmap-level offset.  This function is similar to [Sample](#hlsl-method-sample.md) except that it uses the LOD level (in the last component of the location parameter) to choose the mipmap level. |

## Operators

| Operator | Description |
| - | - |
| [operator \[\]](#hlsl-operator.md) | Reads texel data without any filtering or sampling in the first mip level. |
| [mips operator /[ /] /[ /]](#hlsl-operator-mips.md) | Reads texel data without any filtering or sampling. |
# Texture1DArray Class

## Definition

TODO: require exposition on Texture1DArray class

#### In this Article

*  [Definition](#definition)
*  [Methods](#methods)

```HLSL
Texture1DArray<float4> MyTex;
```

## Methods

| Method | Description |
| ------ | ----------- |
| [GetDimensions](#Texture1DArray_GetDimensions.md) | Returns the dimensions of the resource. |
| [Load](#Texture1DArray_Load.md) | Reads texture data. |
| [mips_Operator](#Texture1DArray_mips_Operator.md) | Returns a read-only resource variable. |
| [Operator](#Texture1DArray_Operator.md) | Returns a read-only resource variable. |
| [Sample](#Texture1DArray_Sample.md) | Samples a texture. |
| [SampleBias](#Texture1DArray_SampleBias.md) | Samples a texture, after applying the bias value to the mipmap level. |
| [SampleCmp](#Texture1DArray_SampleCmp.md) | Samples a texture, using a comparison value to reject samples. |
| [SampleCmpLevelZero](#Texture1DArray_SampleCmpLevelZero.md) | Samples a texture on mipmap level 0 only, using a comparison value to reject samples. |
| [SampleGrad](#Texture1DArray_SampleGrad.md) | Samples a texture using a gradient to influence the way the sample location is calculated. |
| [SampleLevel](#Texture1DArray_SampleLevel.md) | Samples a texture on the specified mipmap level. |
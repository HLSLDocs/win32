# Texture2DArray Class

## Definition

TODO: require exposition on Texture2DArray class

#### In this Article

*  [Definition](#definition)
*  [Methods](#methods)

```HLSL
Texture2DArray <float4> MyTex;
```

## Methods

| Method | Description |
| ------ | ----------- |
| [GetDimensions](#Texture2DArray_GetDimensions.md) | Returns the dimensions of the resource. |
| [Load](#Texture2DArray_Load.md) | Reads texture data. |
| [mips_Operator](#Texture2DArray_mips_Operator.md) | Returns a read-only resource variable. |
| [Operator](#Texture2DArray_Operator.md) | Returns a read-only resource variable. |
| [Sample](#Texture2DArray_Sample.md) | Samples a Texture2DArray. |
| [SampleBias](#Texture2DArray_SampleBias.md) | Samples a Texture2DArray, after applying the bias value to the mipmap level. |
| [SampleCmp](#Texture2DArray_SampleCmp.md) | Samples a Texture2DArray, using a comparison value to reject samples. |
| [SampleCmpLevelZero](#Texture2DArray_SampleCmpLevelZero.md) | Samples a Texture2DArray on mipmap level 0 only, using a comparison value to reject samples. |
| [SampleGrad](#Texture2DArray_SampleGrad.md) | Samples a Texture2DArray using a gradient to influence the way the sample location is calculated. |
| [SampleLevel](#Texture2DArray_SampleLevel.md) | Samples a Texture2DArray on the specified mipmap level. |
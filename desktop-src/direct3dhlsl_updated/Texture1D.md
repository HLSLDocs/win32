# Texture1D Class

## Definition

TODO: require exposition on Texture1D class

#### In this Article

*  [Definition](#definition)
*  [Methods](#methods)

```HLSL
Texture1D <float4> MyTex;
```

## Methods

| Method | Description |
| ------ | ----------- |
| [GetDimensions](#Texture1D_GetDimensions.md) | Returns the dimensions of the resource. |
| [Load](#Texture1D_Load.md) | Reads texture data from a Texture1D. |
| [mips_Operator](#Texture1D_mips_Operator.md) | Returns a read-only resource variable. |
| [Operator](#Texture1D_Operator.md) | Returns a read-only resource variable. |
| [Sample](#Texture1D_Sample.md) | Samples a Texture1D. |
| [SampleBias](#Texture1D_SampleBias.md) | Samples a Texture1D, after applying the bias value to the mipmap level. |
| [SampleCmp](#Texture1D_SampleCmp.md) | Samples a Texture1D, using a comparison value to reject samples. |
| [SampleCmpLevelZero](#Texture1D_SampleCmpLevelZero.md) | Samples a Texture1D on mipmap level 0 only, using a comparison value to reject samples. |
| [SampleGrad](#Texture1D_SampleGrad.md) | Samples a Texture1D using a gradient to influence the way the sample location is calculated. |
| [SampleLevel](#Texture1D_SampleLevel.md) | Samples a Texture1D on the specified mipmap level. |
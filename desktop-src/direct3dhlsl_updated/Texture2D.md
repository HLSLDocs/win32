# Texture2D Class

## Definition

TODO: require exposition on Texture2D class

#### In This Article

*  [Definition](#definition)
*  [Methods](#methods)

```HLSL
Texture2D <float4> MyTex;
```

## Methods

| Method | Description |
| ------ | ----------- |
| [Gather](#Texture2D_Gather.md) | Samples a Texture2D and returns all four components. |
| [GatherAlpha](#Texture2D_GatherAlpha.md) | Samples a Texture2D and returns the alpha component. |
| [GatherBlue](#Texture2D_GatherBlue.md) | Samples a Texture2D and returns the blue component. |
| [GatherGreen](#Texture2D_GatherGreen.md) | Samples a Texture2D and returns the green component. |
| [GatherRed](#Texture2D_GatherRed.md) | Samples a Texture2D and returns the red component. |
| [GatherCmpAlpha](#Texture2D_GatherCmpAlpha.md) | Samples and compares a Texture2D and returns the alpha component. |
| [GatherCmpBlue](#Texture2D_GatherCmpBlue.md) | Samples and compares a Texture2D and returns the blue component. |
| [GatherCmpGreen](#Texture2D_GatherCmpGreen.md) | Samples and compares a Texture2D and returns the green component. |
| [GatherCmpRed](#Texture2D_GatherCmpRed.md) |  Samples and compares a Texture2D and returns the red component. |
| [GetDimensions](#Texture2D_GetDimensions.md) | Returns the dimensions of the resource. |
| [Load](#Texture2D_Load.md) | Reads texture data from a Texture2D. |
| [mips_Operator](#Texture2D_mips_Operator.md) | Returns a read-only resource variable. |
| [Operator](#Texture2D_Operator.md) | Returns a read-only resource variable. |
| [Sample](#Texture2D_Sample.md) | Samples a Texture2D. |
| [SampleBias](#Texture2D_SampleBias.md) | Samples a Texture2D, after applying the bias value to the mipmap level. |
| [SampleCmp](#Texture2D_SampleCmp.md) | Samples a Texture2D, using a comparison value to reject samples. |
| [SampleCmpLevelZero](#Texture2D_SampleCmpLevelZero.md) | Samples a Texture2D on mipmap level 0 only, using a comparison value to reject samples. |
| [SampleGrad](#Texture2D_SampleGrad.md) | Samples a Texture2D using a gradient to influence the way the sample location is calculated. |
| [SampleLevel](#Texture2D_SampleLevel.md) | Samples a Texture2D on the specified mipmap level. |
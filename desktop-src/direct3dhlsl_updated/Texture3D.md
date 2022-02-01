# Texture3D Class

## Definition

TODO: require exposition on Texture3D class

#### In This Article

*  [Definition](#definition)
*  [Methods](#methods)

```HLSL
Texture3D <float4> MyTex;
```

## Methods

| Method | Description |
| ------ | ----------- |
| [GetDimensions](#Texture3D_GetDimensions.md) | Returns the dimensions of the resource. |
| [Load](#Texture3D_Load.md) | Reads texture data from a Texture3D. |
| [mips_Operator](#Texture3D_mips_Operator.md) | Returns a read-only resource variable. |
| [Operator](#Texture3D_Operator.md) | Returns a read-only resource variable. |
| [Sample](#Texture3D_Sample.md) | Samples a Texture3D. |
| [SampleBias](#Texture3D_SampleBias.md) | Samples a Texture3D, after applying the bias value to the mipmap level. |
| [SampleCmp](#Texture3D_SampleCmp.md) | Samples a Texture3D, using a comparison value to reject samples. |
| [SampleCmpLevelZero](#Texture3D_SampleCmpLevelZero.md) | Samples a Texture3D on mipmap level 0 only, using a comparison value to reject samples. |
| [SampleGrad](#Texture3D_SampleGrad.md) | Samples a Texture3D using a gradient to influence the way the sample location is calculated. |
| [SampleLevel](#Texture3D_SampleLevel.md) | Samples a Texture3D on the specified mipmap level. |
# Texture2DArray.SampleBias Method

Reference

## Definition

Samples a texture, after applying the bias value to the mipmap level.

#### In this article

*  [Definition](#definition)
*  [Overloads](#overloads)

## Overloads

| Method | Description |
| ------ | ----------- |
| [SampleBias(S,float3,float,int2)](#SampleBias-S-float3-float-int2) | Samples a texture, after applying the bias value to the mipmap level. |
| [SampleBias(S,float3,float,int2,float)](#SampleBias-S-float3-float-int2-float) | 	Samples a texture, after applying the bias value to the mipmap level, with an optional value to clamp sample level-of-detail (LOD) values to. |
| [SampleBias(S,float3,float,int2,float,uint)](#SampleBias-S-float3-float-int2-float-uint) | Samples a texture, after applying the bias value to the mipmap level, with an optional value to clamp sample level-of-detail (LOD) values to. Returns status about the operation. |

## SampleBias(S,float3,float,int2) {#SampleBias-S-float3-float-int2}

Samples a texture, after applying the bias value to the mipmap level.

```HLSL
DXGI_FORMAT SampleBias(
  in SamplerState S,
  in float3       Location,
  in float        Bias,
  in int2         Offset
);
```

### Parameters
<i>S</i> [in] SamplerState
A Sampler state. This is an object declared in an effect file that contains state assignments.

<i>location</i> [in] float3
The texture coordinates; the first and second components contain the (u,v) coordinates.  The third component indicates the desired array slice.

<i>Bias</i> [in] float
The bias value, which is a floating-point number between 0.0 and 1.0 inclusive, is applied to a mip level before sampling.

<i>offset</i> [in] int2
The offset applied to the texture coordinates before sampling.

### Returns
Type: DXGI_FORMAT

The texture format, which is one of the typed values listed in DXGI_FORMAT.

## SampleBias(S,float3,float,int2,float) {#SampleBias-S-float3-float-int2-float}

Samples a texture, after applying the bias value to the mipmap level, with an optional value to clamp sample level-of-detail (LOD) values to.

```HLSL
DXGI_FORMAT SampleBias(
  in SamplerState S,
  in float3       Location,
  in float        Bias,
  in int2         Offset,
  in float        Clamp
);
```

### Parameters
<i>S</i> [in] SamplerState
A Sampler state. This is an object declared in an effect file that contains state assignments.

<i>location</i> [in] float3
The texture coordinates; the first and second components contain the (u,v) coordinates.  The third component indicates the desired array slice.

<i>Bias</i> [in] float
The bias value, which is a floating-point number between 0.0 and 1.0 inclusive, is applied to a mip level before sampling.

<i>offset</i> [in] int2
The offset applied to the texture coordinates before sampling.

<i>Clamp</i> [in] float
An optional value to clamp sample LOD values to. For example, if you pass 2.0f for the clamp value, you ensure that no individual sample accesses a mip level less than 2.0f.

### Returns
Type: DXGI_FORMAT

The texture format, which is one of the typed values listed in DXGI_FORMAT.

## SampleBias(S,float3,float,int2,float,uint) {#SampleBias-S-float3-float-int2-float-uint}

Samples a texture, after applying the bias value to the mipmap level, with an optional value to clamp sample level-of-detail (LOD) values to. Returns status about the operation.

```HLSL
DXGI_FORMAT SampleBias(
  in SamplerState S,
  in float3       Location,
  in float        Bias,
  in int2         Offset,
  in float        Clamp,
  out uint        Status
);
```

### Parameters
<i>S</i> [in] SamplerState
A Sampler state. This is an object declared in an effect file that contains state assignments.

<i>location</i> [in] float3
The texture coordinates; the first and second components contain the (u,v) coordinates.  The third component indicates the desired array slice.

<i>Bias</i> [in] float
The bias value, which is a floating-point number between 0.0 and 1.0 inclusive, is applied to a mip level before sampling.

<i>offset</i> [in] int2
The offset applied to the texture coordinates before sampling.

<i>Clamp</i> [in] float
An optional value to clamp sample LOD values to. For example, if you pass 2.0f for the clamp value, you ensure that no individual sample accesses a mip level less than 2.0f.

<i>Status</i> [out] uint
The status of the operation. You can't access the status directly; instead, pass the status to the CheckAccessFullyMapped intrinsic function. CheckAccessFullyMapped returns TRUE if all values from the corresponding Sample, Gather, or Load operation accessed mapped tiles in a tiled resource. If any values were taken from an unmapped tile, CheckAccessFullyMapped returns FALSE.

### Returns
Type: DXGI_FORMAT

The texture format, which is one of the typed values listed in DXGI_FORMAT.
# Texture1DArray.SampleGrad Method

Reference

## Definition

Samples a texture using a gradient to influence the way the sample location is calculated.
#### In this article

*  [Definition](#definition)
*  [Overloads](#overloads)

## Overloads

| Method | Description |
| ------ | ----------- |
| [SampleGrad(S,float2,float,float,int)](#SampleGrad-S-float2-float-float-int) | Samples a texture, using a gradient to influence the way the sample location is calculated. |
| [SampleCmp(S,float2,float,float,int,float)](#SampleCmp-S-float2-float-float-int-float) | Samples a texture, using a gradient to influence the way the sample location is calculated, with an optional value to clamp sample level-of-detail (LOD) values to. |
| [SampleCmp(S,float2,float,float,int,float,uint)](#SampleCmp-S-float2-float-float-int-float-uint) | Samples a texture, using a gradient to influence the way the sample location is calculated, with an optional value to clamp sample level-of-detail (LOD) values to. Returns status about the operation. |

## SampleGrad(S,float2,float,float,int) {#SampleGrad-S-float2-float-float-int}

Samples a texture, using a gradient to influence the way the sample location is calculated.

```HLSL
DXGI_FORMAT SampleCmp(
  in SamplerState S,
  in float2       Location,
  in float        DDX,
  in float        DDY,
  in int          Offset
);
```

### Parameters
<i>S</i> [in] SamplerState
A Sampler state. This is an object declared in an effect file that contains state assignments.

<i>location</i> [in] float2
The index position. The first component contains the u coordinate. The second component indicates the desired array slice.

<i>DDX</i> [in] float
The rate of change of the surface geometry in the x direction.

<i>DDY</i> [in] float
The rate of change of the surface geometry in the y direction.

<i>Offset</i> [in] int
The offset applied to the texture coordinates before sampling.

### Returns
Type: DXGI_FORMAT

The texture format, which is one of the typed values listed in DXGI_FORMAT.

## SampleGrad(S,float2,float,float,int,float) {#SampleGrad-S-float2-float-float-int-float}

Samples a texture, using a gradient to influence the way the sample location is calculated, with an optional value to clamp sample level-of-detail (LOD) values to.

```HLSL
DXGI_FORMAT SampleCmp(
  in SamplerState S,
  in float2       Location,
  in float        DDX,
  in float        DDY,
  in int          Offset,
  in float        Clamp
);
```

### Parameters
<i>S</i> [in] SamplerState
A Sampler state. This is an object declared in an effect file that contains state assignments.

<i>location</i> [in] float2
The index position. The first component contains the u coordinate. The second component indicates the desired array slice.

<i>DDX</i> [in] float
The rate of change of the surface geometry in the x direction.

<i>DDY</i> [in] float
The rate of change of the surface geometry in the y direction.

<i>Offset</i> [in] int
The offset applied to the texture coordinates before sampling.

<i>Clamp</i> [in] float
An optional value to clamp sample LOD values to. For example, if you pass 2.0f for the clamp value, you ensure that no individual sample accesses a mip level less than 2.0f.

### Returns
Type: DXGI_FORMAT

The texture format, which is one of the typed values listed in DXGI_FORMAT.

## SampleGrad(S,float2,float,float,int,float) {#SampleGrad-S-float2-float-float-int-float}

Samples a texture, using a gradient to influence the way the sample location is calculated, with an optional value to clamp sample level-of-detail (LOD) values to.

```HLSL
DXGI_FORMAT SampleCmp(
  in SamplerState S,
  in float2       Location,
  in float        DDX,
  in float        DDY,
  in int          Offset,
  in float        Clamp,
  out uint        Status
);
```

### Parameters
<i>S</i> [in] SamplerState
A Sampler state. This is an object declared in an effect file that contains state assignments.

<i>location</i> [in] float2
The index position. The first component contains the u coordinate. The second component indicates the desired array slice.

<i>DDX</i> [in] float
The rate of change of the surface geometry in the x direction.

<i>DDY</i> [in] float
The rate of change of the surface geometry in the y direction.

<i>Offset</i> [in] int
The offset applied to the texture coordinates before sampling.

<i>Clamp</i> [in] float
An optional value to clamp sample LOD values to. For example, if you pass 2.0f for the clamp value, you ensure that no individual sample accesses a mip level less than 2.0f.

<i>Status</i> [out] uint
The status of the operation. You can't access the status directly; instead, pass the status to the CheckAccessFullyMapped intrinsic function. CheckAccessFullyMapped returns TRUE if all values from the corresponding Sample, Gather, or Load operation accessed mapped tiles in a tiled resource. If any values were taken from an unmapped tile, CheckAccessFullyMapped returns FALSE.

### Returns
Type: DXGI_FORMAT

The texture format, which is one of the typed values listed in DXGI_FORMAT.
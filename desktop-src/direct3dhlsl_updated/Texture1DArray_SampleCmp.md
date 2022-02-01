# Texture1DArray.SampleCmp Method

Reference

## Definition

Samples a texture, using a comparison value to reject samples.

#### In this article

*  [Definition](#definition)
*  [Overloads](#overloads)

## Overloads

| Method | Description |
| ------ | ----------- |
| [SampleCmp(S,float2,float,int)](#SampleCmp-S-float2-float-int) | Samples a texture, using a comparison value to reject samples. |
| [SampleCmp(S,float2,float,int,float)](#SampleCmp-S-float2-float-int-float) | Samples a texture, using a comparison value to reject samples, with an optional value to clamp sample level-of-detail (LOD) values to. |
| [SampleCmp(S,float2,float,int,float,uint)](#SampleCmp-S-float2-float-int-float-uint) | Samples a texture, using a comparison value to reject samples, with an optional value to clamp sample level-of-detail (LOD) values to. Returns status about the operation. |

## SampleCmp(S,float2,float,int) {#SampleCmp-S-float2-float-int}

Samples a texture, using a comparison value to reject samples.

```HLSL
DXGI_FORMAT SampleCmp(
  in SamplerComparisonState S,
  in float2       Location,
  in float        CompareValue,
  in int          Offset
);
```

### Parameters
<i>S</i> [in] SamplerComparisonState
A Sampler state. This is an object declared in an effect file that contains state assignments.

<i>location</i> [in] float2
The index position. The first component contains the u coordinate. The second component indicates the desired array slice.

<i>CompareValue</i> [in] float
A floating-point value to use as a comparison value.

<i>Offset</i> [in] int
The offset applied to the texture coordinates before sampling.

### Returns
Type: DXGI_FORMAT

The texture format, which is one of the typed values listed in DXGI_FORMAT.

## SampleCmp(S,float2,float,int,float) {#SampleCmp-S-float2-float-int-float}

Samples a Texture1D, using a comparison value to reject samples, with an optional value to clamp sample level-of-detail (LOD) values to.

```HLSL
DXGI_FORMAT SampleCmp(
  in SamplerComparisonState S,
  in float2       Location,
  in float        CompareValue,
  in int          Offset,
  in float        Clamp
);
```

### Parameters
<i>S</i> [in] SamplerComparisonState
A Sampler state. This is an object declared in an effect file that contains state assignments.

<i>location</i> [in] float2
The index position. The first component contains the u coordinate. The second component indicates the desired array slice.

<i>CompareValue</i> [in] float
A floating-point value to use as a comparison value.

<i>Offset</i> [in] int
The offset applied to the texture coordinates before sampling.

<i>Clamp</i> [in] float
An optional value to clamp sample LOD values to. For example, if you pass 2.0f for the clamp value, you ensure that no individual sample accesses a mip level less than 2.0f.

### Returns
Type: DXGI_FORMAT

The texture format, which is one of the typed values listed in DXGI_FORMAT.

## SampleCmp(S,float2,float,int,float,uint) {#SampleCmp-S-float2-float-int-float-uint}

Samples a texture, using a comparison value to reject samples, with an optional value to clamp sample level-of-detail (LOD) values to. Returns status about the operation.

```HLSL
DXGI_FORMAT SampleBias(
  in SamplerComparisonState S,
  in float2       Location,
  in float        CompareValue,
  in int          Offset,
  in float        Clamp,
  out uint        Status
);
```

### Parameters
<i>S</i> [in] SamplerComparisonState
A Sampler state. This is an object declared in an effect file that contains state assignments.

<i>location</i> [in] float2
The index position. The first component contains the u coordinate. The second component indicates the desired array slice.

<i>CompareValue</i> [in] float
A floating-point value to use as a comparison value.

<i>Offset</i> [in] int
The offset applied to the texture coordinates before sampling.

<i>Clamp</i> [in] float
An optional value to clamp sample LOD values to. For example, if you pass 2.0f for the clamp value, you ensure that no individual sample accesses a mip level less than 2.0f.

<i>Status</i> [out] uint
The status of the operation. You can't access the status directly; instead, pass the status to the CheckAccessFullyMapped intrinsic function. CheckAccessFullyMapped returns TRUE if all values from the corresponding Sample, Gather, or Load operation accessed mapped tiles in a tiled resource. If any values were taken from an unmapped tile, CheckAccessFullyMapped returns FALSE.

### Returns
Type: DXGI_FORMAT

The texture format, which is one of the typed values listed in DXGI_FORMAT.
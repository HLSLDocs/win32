# Helper Operations

### D3DCOLORtoUBYTE4

Converts a floating-point, 4D vector set by a D3DCOLOR to a UBYTE4.



| *ret* D3DCOLORtoUBYTE4(*x*) |
|-----------------------------|



 

This function swizzles and scales components of the *x* parameter. Use this function to compensate for the lack of UBYTE4 support in some hardware.

#### Parameters



| Item                                                   | Description                                              |
|--------------------------------------------------------|----------------------------------------------------------|
| <span id="x"></span><span id="X"></span>*x*<br/> | \[in\] The floating-point vector4 to convert.<br/> |



 

#### Return Value

The UBYTE4 representation of the *x* parameter.

#### Type Description



| Name  | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                       | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md) | Size |
|-------|-------------------------------------------------------------------------------------|----------------------------------------------------------------|------|
| *x*   | [**vector**](dx-graphics-hlsl-intrinsic-functions.md) | [**float**](/windows/desktop/WinProg/windows-data-types)                        | 4    |
| *ret* | [**vector**](dx-graphics-hlsl-intrinsic-functions.md) | [**integer**](/windows/desktop/WinProg/windows-data-types)                      | 4    |

### Process2DQuadTessFactorsAvg function

Generates the corrected tessellation factors for a quad patch.

#### Syntax

``` syntax
void Process2DQuadTessFactorsAvg(
  in  float4 RawEdgeFactors,
  in  float2 InsideScale,
  out float4 RoundedEdgeTessFactors,
  out float2 RoundedInsideTessFactors,
  out float2 UnroundedInsideTessFactors
);
```

#### Parameters

<dl> <dt>

*RawEdgeFactors* \[in\]
</dt> <dd>

Type: **float4**

The edge tessellation factors, passed into the tessellator stage.

</dd> <dt>

*InsideScale* \[in\]
</dt> <dd>

Type: **float2**

The scale factor applied to the UV tessellation factors computed by the tessellation stage. The allowable range for InsideScale is 0.0 to 1.0.

</dd> <dt>

*RoundedEdgeTessFactors* \[out\]
</dt> <dd>

Type: **float4**

The rounded edge-tessellation factors calculated by the tessellator stage.

</dd> <dt>

*RoundedInsideTessFactors* \[out\]
</dt> <dd>

Type: **float2**

The rounded tessellation factors calculated by the tessellator stage for inside edges.

</dd> <dt>

*UnroundedInsideTessFactors* \[out\]
</dt> <dd>

Type: **float2**

The tessellation factors calculated by the tessellator stage for inside edges.

</dd> </dl>

#### Return value

This function does not return a value.

#### Remarks

Generates the corrected tessellation factors for a quad patch, computing the inside tessellation factors as the average of the edge tessellation factors. The U and V inside tessellation factors are computed independently using the average of opposing sides of the domain, then are scaled by InsideScale. The result is then rounded based on the partitioning mode, but the unrounded results are available using the UnroundedInsideTessFactors parameter.

### Process2DQuadTessFactorsMax function

Generates the corrected tessellation factors for a quad patch.

#### Syntax

``` syntax
void Process2DQuadTessFactorsMax(
  in  float4 RawEdgeFactors,
  in  float2 InsideScale,
  out float4 RoundedEdgeTessFactors,
  out float2 RoundedInsideTessFactors,
  out float2 UnroundedInsideTessFactors
);
```

#### Parameters

<dl> <dt>

*RawEdgeFactors* \[in\]
</dt> <dd>

Type: **float4**

The edge tessellation factors, passed into the tessellator stage.

</dd> <dt>

*InsideScale* \[in\]
</dt> <dd>

Type: **float2**

The scale factor applied to the UV tessellation factors computed by the tessellation stage. The allowable range for InsideScale is 0.0 to 1.0.

</dd> <dt>

*RoundedEdgeTessFactors* \[out\]
</dt> <dd>

Type: **float4**

The rounded edge-tessellation factors calculated by the tessellator stage.

</dd> <dt>

*RoundedInsideTessFactors* \[out\]
</dt> <dd>

Type: **float2**

The rounded tessellation factors calculated by the tessellator stage for inside edges.

</dd> <dt>

*UnroundedInsideTessFactors* \[out\]
</dt> <dd>

Type: **float2**

The tessellation factors calculated by the tessellator stage for inside edges.

</dd> </dl>

#### Return value

This function does not return a value.

#### Remarks

Generates the corrected tessellation factors for a quad patch, computing the inside tessellation factors as the maximum of the edge tessellation factors. The U and V inside tessellation factors are computed independently using the maximums of opposing sides of the domain, then are scaled by InsideScale. The result is then rounded based on the partitioning mode, but the unrounded results are available using the UnroundedInsideTessFactors parameter.

### Process2DQuadTessFactorsMin function

Generates the corrected tessellation factors for a quad patch.

#### Syntax

``` syntax
void Process2DQuadTessFactorsMin(
  in  float4 RawEdgeFactors,
  in  float2 InsideScale,
  out float4 RoundedEdgeTessFactors,
  out float2 RoundedInsideTessFactors,
  out float2 UnroundedInsideTessFactors
);
```

#### Parameters

<dl> <dt>

*RawEdgeFactors* \[in\]
</dt> <dd>

Type: **float4**

The edge tessellation factors, passed into the tessellator stage.

</dd> <dt>

*InsideScale* \[in\]
</dt> <dd>

Type: **float2**

The scale factor applied to the UV tessellation factors computed by the tessellation stage. The allowable range for InsideScale is 0.0 to 1.0.

</dd> <dt>

*RoundedEdgeTessFactors* \[out\]
</dt> <dd>

Type: **float4**

The rounded edge-tessellation factors calculated by the tessellator stage.

</dd> <dt>

*RoundedInsideTessFactors* \[out\]
</dt> <dd>

Type: **float2**

The rounded tessellation factors calculated by the tessellator stage for inside edges.

</dd> <dt>

*UnroundedInsideTessFactors* \[out\]
</dt> <dd>

Type: **float2**

The tessellation factors calculated by the tessellator stage for inside edges.

</dd> </dl>

#### Return value

This function does not return a value.

#### Remarks

Generates the corrected tessellation factors for a quad patch, computing the inside tessellation factors as the minimum of the edge tessellation factors. The U and V inside tessellation factors are computed independently using the minimums of opposing sides of the domain, then are scaled by InsideScale. The result is then rounded based on the partitioning mode, but the unrounded results are available using the UnroundedInsideTessFactors parameter.

### ProcessIsolineTessFactors function

Generates the rounded tessellation factors for an isoline.

#### Syntax

``` syntax
void ProcessIsolineTessFactors(
  in  float RawDetailFactor,
  in  float RawDensityFactor,
  out float RoundedDetailFactor,
  out float RoundedDensityFactor
);
```

#### Parameters

<dl> <dt>

*RawDetailFactor* \[in\]
</dt> <dd>

Type: **float**

The desired detail factor.

</dd> <dt>

*RawDensityFactor* \[in\]
</dt> <dd>

Type: **float**

The desired density factor.

</dd> <dt>

*RoundedDetailFactor* \[out\]
</dt> <dd>

Type: **float**

The rounded detail factor clamped to a range that can be used by the tessellator.

</dd> <dt>

*RoundedDensityFactor* \[out\]
</dt> <dd>

Type: **float**

The rounded density factor clamped to a rangethat can be used by the tessellator.

</dd> </dl>

#### Return value

This function does not return a value.

### ProcessQuadTessFactorsAvg function

Generates the corrected tessellation factors for a quad patch.

#### Syntax

``` syntax
void ProcessQuadTessFactorsAvg(
  in  float4 RawEdgeFactors,
  in  float InsideScale,
  out float4 RoundedEdgeTessFactors,
  out float2 RoundedInsideTessFactors,
  out float2 UnroundedInsideTessFactors
);
```

#### Parameters

<dl> <dt>

*RawEdgeFactors* \[in\]
</dt> <dd>

Type: **float4**

The edge tessellation factors, passed into the tessellator stage.

</dd> <dt>

*InsideScale* \[in\]
</dt> <dd>

Type: **float**

The scale factor applied to the UV tessellation factors computed by the tessellation stage. The allowable range for InsideScale is 0.0 to 1.0.

</dd> <dt>

*RoundedEdgeTessFactors* \[out\]
</dt> <dd>

Type: **float4**

The rounded edge-tessellation factors calculated by the tessellator stage.

</dd> <dt>

*RoundedInsideTessFactors* \[out\]
</dt> <dd>

Type: **float2**

The rounded tessellation factors calculated by the tessellator stage for inside edges.

</dd> <dt>

*UnroundedInsideTessFactors* \[out\]
</dt> <dd>

Type: **float2**

The tessellation factors calculated by the tessellator stage for inside edges.

</dd> </dl>

#### Return value

This function does not return a value.

#### Remarks

Generates the corrected tessellation factors for a quad patch, computing the inside tessellation factors as the average of the edge tessellation factors. The inside tess factors will be identical values determined by the average of all four edges scaled by InsideScale. The result is then rounded based on the partitioning mode, but the unrounded results are available using the UnroundedInsideTessFactors parameter.

### ProcessQuadTessFactorsMax function

Generates the corrected tessellation factors for a quad patch.

#### Syntax

``` syntax
void ProcessQuadTessFactorsMax(
  in  float4 RawEdgeFactors,
  in  float InsideScale,
  out float4 RoundedEdgeTessFactors,
  out float2 RoundedInsideTessFactors,
  out float2 UnroundedInsideTessFactors
);
```

#### Parameters

<dl> <dt>

*RawEdgeFactors* \[in\]
</dt> <dd>

Type: **float4**

The edge tessellation factors, passed into the tessellator stage.

</dd> <dt>

*InsideScale* \[in\]
</dt> <dd>

Type: **float**

The scale factor applied to the UV tessellation factors computed by the tessellation stage. The allowable range for InsideScale is 0.0 to 1.0.

</dd> <dt>

*RoundedEdgeTessFactors* \[out\]
</dt> <dd>

Type: **float4**

The rounded edge-tessellation factors calculated by the tessellator stage.

</dd> <dt>

*RoundedInsideTessFactors* \[out\]
</dt> <dd>

Type: **float2**

The rounded tessellation factors calculated by the tessellator stage for inside edges.

</dd> <dt>

*UnroundedInsideTessFactors* \[out\]
</dt> <dd>

Type: **float2**

The tessellation factors calculated by the tessellator stage for inside edges.

</dd> </dl>

#### Return value

This function does not return a value.

#### Remarks

Generates the corrected tessellation factors for a quad patch, computing the inside tessellation factors as the maximum of the edge tessellation factors. The inside tess factors will be identical values determined by the maximum of all four edges scaled by InsideScale. The result is then rounded based on the partitioning mode, but the unrounded results are available using the *UnroundedInsideTessFactors* parameter.

### ProcessQuadTessFactorsMin function

Generates the corrected tessellation factors for a quad patch.

#### Syntax

``` syntax
void ProcessQuadTessFactorsMin(
  in  float4 RawEdgeFactors,
  in  float InsideScale,
  out float4 RoundedEdgeTessFactors,
  out float2 RoundedInsideTessFactors,
  out float2 UnroundedInsideTessFactors
);
```

#### Parameters

<dl> <dt>

*RawEdgeFactors* \[in\]
</dt> <dd>

Type: **float4**

The edge tessellation factors, passed into the tessellator stage.

</dd> <dt>

*InsideScale* \[in\]
</dt> <dd>

Type: **float**

The scale factor applied to the UV tessellation factors computed by the tessellation stage. The allowable range for InsideScale is 0.0 to 1.0.

</dd> <dt>

*RoundedEdgeTessFactors* \[out\]
</dt> <dd>

Type: **float4**

The rounded edge-tessellation factors calculated by the tessellator stage.

</dd> <dt>

*RoundedInsideTessFactors* \[out\]
</dt> <dd>

Type: **float2**

The rounded tessellation factors calculated by the tessellator stage for inside edges.

</dd> <dt>

*UnroundedInsideTessFactors* \[out\]
</dt> <dd>

Type: **float2**

The tessellation factors calculated by the tessellator stage for inside edges.

</dd> </dl>

#### Return value

This function does not return a value.

#### Remarks

Generates the corrected tessellation factors for a quad patch, computing the inside tessellation factors as the minimum of the edge tessellation factors. The inside tess factors will be identical values determined by the minimum of all four edges scaled by InsideScale. The result is then rounded based on the partitioning mode, but the unrounded results are available using the UnroundedInsideTessFactors parameter.

### ProcessQuadTessFactorsAvg function

Generates the corrected tessellation factors for a quad patch.

#### Syntax

``` syntax
void ProcessQuadTessFactorsAvg(
  in  float4 RawEdgeFactors,
  in  float InsideScale,
  out float4 RoundedEdgeTessFactors,
  out float2 RoundedInsideTessFactors,
  out float2 UnroundedInsideTessFactors
);
```

#### Parameters

<dl> <dt>

*RawEdgeFactors* \[in\]
</dt> <dd>

Type: **float4**

The edge tessellation factors, passed into the tessellator stage.

</dd> <dt>

*InsideScale* \[in\]
</dt> <dd>

Type: **float**

The scale factor applied to the UV tessellation factors computed by the tessellation stage. The allowable range for InsideScale is 0.0 to 1.0.

</dd> <dt>

*RoundedEdgeTessFactors* \[out\]
</dt> <dd>

Type: **float4**

The rounded edge-tessellation factors calculated by the tessellator stage.

</dd> <dt>

*RoundedInsideTessFactors* \[out\]
</dt> <dd>

Type: **float2**

The rounded tessellation factors calculated by the tessellator stage for inside edges.

</dd> <dt>

*UnroundedInsideTessFactors* \[out\]
</dt> <dd>

Type: **float2**

The tessellation factors calculated by the tessellator stage for inside edges.

</dd> </dl>

#### Return value

This function does not return a value.

#### Remarks

Generates the corrected tessellation factors for a quad patch, computing the inside tessellation factors as the average of the edge tessellation factors. The inside tess factors will be identical values determined by the average of all four edges scaled by InsideScale. The result is then rounded based on the partitioning mode, but the unrounded results are available using the UnroundedInsideTessFactors parameter.

### ProcessTriTessFactorsMax function

Generates the corrected tessellation factors for a tri patch.

#### Syntax

``` syntax
void ProcessTriTessFactorsMax(
  in  float3 RawEdgeFactors,
  in  float InsideScale,
  out float3 RoundedEdgeTessFactors,
  out float RoundedInsideTessFactor,
  out float UnroundedInsideTessFactor
);
```

#### Parameters

<dl> <dt>

*RawEdgeFactors* \[in\]
</dt> <dd>

Type: **float3**

The edge tessellation factors, passed into the tessellator stage.

</dd> <dt>

*InsideScale* \[in\]
</dt> <dd>

Type: **float**

The scale factor applied to the UV tessellation factors computed by the tessellation stage. The allowable range for InsideScale is 0.0 to 1.0.

</dd> <dt>

*RoundedEdgeTessFactors* \[out\]
</dt> <dd>

Type: **float3**

The rounded edge-tessellation factors calculated by the tessellator stage.

</dd> <dt>

*RoundedInsideTessFactor* \[out\]
</dt> <dd>

Type: **float**

The tessellation factors calculated by the tessellator stage, and rounded.

</dd> <dt>

*UnroundedInsideTessFactor* \[out\]
</dt> <dd>

Type: **float**

The original, unrounded, UV tessellation factors computed by the tessellation stage.

</dd> </dl>

#### Return value

This function does not return a value.

#### Remarks

Generates the corrected tessellation factors for a tri patch, computing the inside tessellation factor as the maximum of the edge tessellation factors, which is then scaled by InsideScale. The result is then rounded based on the partitioning mode, but the unrounded results are available using the UnroundedInsideTessFactor parameter.

### ProcessTriTessFactorsMin function

Generates the corrected tessellation factors for a tri patch.

#### Syntax

``` syntax
void ProcessTriTessFactorsMin(
  in  float3 RawEdgeFactors,
  in  float InsideScale,
  out float3 RoundedEdgeTessFactors,
  out float RoundedInsideTessFactors,
  out float UnroundedInsideTessFactors
);
```

#### Parameters

<dl> <dt>

*RawEdgeFactors* \[in\]
</dt> <dd>

Type: **float3**

The edge tessellation factors, passed into the tessellator stage.

</dd> <dt>

*InsideScale* \[in\]
</dt> <dd>

Type: **float**

The scale factor applied to the UV tessellation factors computed by the tessellation stage. The allowable range for InsideScale is 0.0 to 1.0.

</dd> <dt>

*RoundedEdgeTessFactors* \[out\]
</dt> <dd>

Type: **float3**

The rounded edge-tessellation factors calculated by the tessellator stage.

</dd> <dt>

*RoundedInsideTessFactors* \[out\]
</dt> <dd>

Type: **float**

The rounded tessellation factors calculated by the tessellator stage for inside edges.

</dd> <dt>

*UnroundedInsideTessFactors* \[out\]
</dt> <dd>

Type: **float**

The tessellation factors calculated by the tessellator stage for inside edges.

</dd> </dl>

#### Return value

This function does not return a value.

#### Remarks

Generates the corrected tessellation factors for a tri patch, computing the inside tessellation factor as the minimum of the edge tessellation factors, which is then scaled by InsideScale. The result is then rounded based on the partitioning mode, but the unrounded results are available using the UnroundedInsideTessFactor parameter.

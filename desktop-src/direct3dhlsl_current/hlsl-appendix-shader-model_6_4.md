# Shader Model 6.4

- The new shader model adds the following 3 intrinsics to accelerate dot products on reduced precision data:
    - [`Unsigned Integer Dot-Product of 4 Elements and Accumulate`](dx-graphics-hlsl.md)
    - [`Signed Integer Dot-Product of 4 Elements and Accumulate`](dx-graphics-hlsl.md)
    - [`Single Precision Floating Point 2-Element Dot-Product and Accumulate`](dx-graphics-hlsl.md)
- Support for Variable Rate Shading
    - Variable rate shading is supported as of this shader model. Only one token was added to HLSL.  [`SV_ShadingRate`](dx-graphics-hlsl.md) Indicates the number of samples per pixel during operation of the current pixel shader thread.  See the variable rate shading [`spec`](https://microsoft.github.io/DirectX-Specs/d3d/VariableRateShading.html) for more details.
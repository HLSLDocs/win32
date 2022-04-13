# High-level shader language (HLSL)

HLSL is the C-like high-level shader language that you use with programmable shaders in DirectX.

For example, you can use HLSL to write a [vertex shader](../direct3d11/vertex-shader-stage.md), or a [pixel shader](../direct3d11/pixel-shader-stage.md), and use those shaders in the implementation of the renderer in your [Direct3D](../direct3d12/directx-12-programming-guide.md) application.

Or you could use HLSL to write a compute shader, perhaps to implement a physics simulation. However, if for example you're inclined to write your own convolution operator (for image processing) as HLSL in a compute shader, then you'll get better performance in that scenario if you use [Direct Machine Learning (DirectML)](/windows/ai/directml/dml) instead.

HLSL was created (starting with DirectX 9) to set up the programmable 3D [pipeline](../direct3d11/overviews-direct3d-11-graphics-pipeline.md). You can program the entire pipeline with HLSL instructions.
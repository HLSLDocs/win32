# High-level shader language (HLSL)

HLSL is the C-like high-level shader language that you use with programmable shaders in DirectX.

For example, you can use HLSL to write a [vertex shader](../direct3d11/vertex-shader-stage.md), or a [pixel shader](../direct3d11/pixel-shader-stage.md), and use those shaders in the implementation of the renderer in your [Direct3D](../direct3d12/directx-12-programming-guide.md) application.

Or you could use HLSL to write a compute shader, perhaps to implement a physics simulation. However, if for example you're inclined to write your own convolution operator (for image processing) as HLSL in a compute shader, then you'll get better performance in that scenario if you use [Direct Machine Learning (DirectML)](https://docs.microsoft.com/en-us/windows/ai/directml/dml) instead.

This HLSL refers to the language supported by `dxc.exe`.  At a minimum, this compiler supports `Shader Model 6.0` and `HLSL Language Set 2016`.

## [`Using the Compiler`](hlsl-using_compiler_landing.md) 

This section describes the development environment for using the DirectX 12 shader compiler `DXC`.

## [`HLSL Language`](hlsl-language_landing.md)

The shader compiler `DXC` compiles and deploys the shader language `HLSL` for custom behavior in fixed-function pipeline stages. This section describes language elements used in the high-level shading language `HLSL`.

## [`HLSL Built-ins`](hlsl-built-ins_landing.md)

`HLSL` contains reserved language elements built in to the `DXC` development environment.

## [`Appendix`](hlsl-appendix-landing.md)

The appendix lists [`language features`](hlsl-language_landing.md) and [`built-ins`](hlsl-built-ins_landing.md) included in [`language sets`](hlsl-appendix-language-versions.md) and [`shader model`](hlsl-appendix-shader-models.md) versions.
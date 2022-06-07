# Migrating to Current Compiler

DXC supports a command-line interface (dxc.exe) and a .dll interface (dxcompiler.dll, dxcompiler.lib, dxcapi.h, and d3d12shader.h). 

For Windows, the latest compiler binaries can be downloaded from GitHub. We recommend always updating to the [latest release](https://github.com/microsoft/DirectXShaderCompiler/releases).  

Windows
```
dxc_<version>\dxc.exe
dxc_<version>\dxcompiler.dll
dxc_<version>\dxcapi.h
dxc_<version>\d3d12shader.h
dxc_<version>\dxcompiler.lib
```

## D3DCompiler DXC Bridge

The d3dcompiler_dxc_bridge.dll is a DLL that will forward many of the D3DCompiler API calls into DirectX Shader Compiler calls in dxcompiler. It can be used to recompile the runtime-compiled shaders of an app into shader model 6 without having to rebuild it or modify any of its source files.

### Usage

The use the library, copy d3dcompiler_dxc_bridge.dll next to the app you're interested in, and rename it d3dcompiler_47.dll. You should also copy dxcompiler.dll and dxil.dll next to the app, so the compiler and validator can be found.

### Gotchas

d3dcompiler_47.dll is the most common DLL these days, but an app or game might be trying to use a prior version, such as d3dcompiler_43.dll. Make sure you rename to the name that the app is using. If necessary, you can have more than one copy of the file with different names.

Some flags aren't implemented because they're not applicable or supported (D3DCOMPILE_ENABLE_STRICTNESS, D3DCOMPILE_PARTIAL_PRECISION). These are simply ignored in the bridge.

The include handler functionality in dxcompiler has a significantly different design and can't really be reimplemented. The dxcompiler version of the handler has no memory of the history of calls and will return file-not-found if a file isn't found with a specific name. The d3dcompiler version instead had to track open/close pairs and reimplement rules for local and system includes. Because of this limitation, there is no support for using a custom include handler (see [`this thread`](https://github.com/Microsoft/DirectXShaderCompiler/issues/161) for more information).

It's possible that we're missing some API call you care deeply about - if so, please file an Issue and we can discuss how to resolve your case.

### Sources

The sources are available under tools\clang\tools\d3dcomp.

## Resource Binding in FXC and DXC

### Resource binding on FXC with SM5.0

```C++
// Resource bindings:
//
// Name                                 Type  Format         Dim      HLSL Bind  Count
// ------------------------------ ---------- ------- ----------- -------------- ------
// Tex1[1]                           texture  float4          2d             t4      1
```

### Resource binding on FXC with SM5.1
```C++
// Resource bindings:
//
// Name                                 Type  Format         Dim      ID      HLSL Bind  Count
// ------------------------------ ---------- ------- ----------- ------- -------------- ------
// Tex1                              texture  float4          2d      T0             t0      2
```

### Resource binding on DXC with SM6.0 without the `-flegacy-resource-reservation` flag

```C++
// Resource bindings:
//
// Name                                 Type  Format         Dim      ID      HLSL Bind  Count
// ------------------------------ ---------- ------- ----------- ------- -------------- ------
// Tex1                              texture     f32          2d      T0             t0     2
```

### Resource binding on DXC with SM6.0 with the `-flegacy-resource-reservation` flag

```C++
// Resource bindings:
//
// Name                                 Type  Format         Dim      ID      HLSL Bind  Count
// ------------------------------ ---------- ------- ----------- ------- -------------- ------
// Tex1                              texture     f32          2d      T0             t3     2
```

## Unsupported FXC behaviors

### Effect framework
Features related to the effects framework are no longer supported.

### Uniform parameters on entry functions
Uniform parameters on entry functions are no longer supported.

There is a rewriter utility that may help port shaders that use this feature to DXC.  The command line tool is called dxr.exe, and the API is in [dxctools.h](https://github.com/microsoft/DirectXShaderCompiler/blob/master/include/dxc/dxctools.h).

The option to use is `-extract-entry-uniforms`, along with the entry name, and any other options necessary to parse the shader, such as `-I` include and `-D` define options.  See `dxr.exe -?` for a full option list.  For the API, use the IDxcRewriter2::RewriteWithOptions method.

Rewritten HLSL will have the uniform resource and values extracted into the global scope for a single entry point.  Name collisions are possible if parameter names collide with global names.  It's meant to be used on one entry for one compilation, not on all entries in one file, otherwise name collisions will likely occur.  Additionally, resources will only be extracted if identified with the `uniform` keyword at this time.

Uniform values extracted into global space will be placed in a constant buffer named `_Params`, since the equivalent in FXC would have been to put them in a constant buffer named `$Params`.

Example:

```C++
float4 main(float4 color : INPUT,
    uniform float scale,
    uniform SamplerState sam,
    uniform Texture2D<float2> tex,
    uniform RWStructuredBuffer<float2> buf : register(u1)
    ) : SV_TARGET
{
  buf[int(color.x)] = tex.SampleLevel(sam, color.xy * scale, 0).xy;
  return color;
}
```

Use the rewriter tool:

```cmd
dxr.exe example.hlsl -extract-entry-uniforms -E main -Fo output.hlsl
```

To produce something like this in `output.hlsl`:

```C++
uniform SamplerState sam;
uniform Texture2D<float2> tex;
uniform RWStructuredBuffer<float2> buf : register(u1);
cbuffer _Params {
uniform float scale;
}
float4 main(float4 color : INPUT) : SV_TARGET {
  buf[int(color.x)] = tex.SampleLevel(sam, color.xy * scale, 0).xy;
  return color;
}
```

### Interfaces
Interfaces are no longer supported.

### Dimension-specific texture sample functions no longer supported
Support for [tex1D](https://docs.microsoft.com/windows/desktop/direct3dhlsl/dx-graphics-hlsl-tex1d), [tex2D](https://docs.microsoft.com/windows/desktop/direct3dhlsl/dx-graphics-hlsl-tex2d), and similar functions for sampling are now deprecated. To learn how to port to supported sampling functions, see the following example.

#### Example using the old syntax for sampling, which is no longer supported

```C++
sampler FontTextureSampler : register(s0);
struct VS_OUT
{
   float2 TexCoord0 : TEXCOORD0;
};

float4 PSMain_Unsupported( VS_OUT In ) : SV_Target
{
    return tex2D( FontTextureSampler, In.TexCoord0 ).zyxw; // tex2D is unsupported.
}
```

#### Example showing supported syntax for sampling

```C++
SamplerState FontTextureSampler : register(s0);
Texture2D FontTexture2D : register( t0 ); // Step 1. Declare texture.

struct VS_OUT
{
   float2 TexCoord0 : TEXCOORD0;
};

float4 PSMain( VS_OUT In ) : SV_Target
{
    // Step 2. Use "Sample" method of the texture declared in the previous step.
    return FontTexture2D.Sample( FontTextureSampler, In.TexCoord0 ).zyxw;
}
```

### Semantic overlap not supported
DXC disallows the use of duplicate semantics. For example, the following shader will fail compilation on DXC.

```C++
uint main(uint a : SV_VertexID, uint b : SV_VertexID) : OUT
{
    return a + b;
}
```

### "ConstantBuffer" as constant buffer name not supported

Starting with SM5.1, HLSL supports [indexable constant buffers](https://docs.microsoft.com/windows/desktop/direct3d12/resource-binding-in-hlsl#constant-buffers) by using the _ConstantBuffer_ template construct. Therefore, _ConstantBuffer_ is a reserved keyword
and DXC disallows using it as a buffer name.


```C++
cbuffer ConstantBuffer : register(b0) // ConstantBuffer as buffer name not allowed.
{
 float2 field1;
 float field2;
}
```
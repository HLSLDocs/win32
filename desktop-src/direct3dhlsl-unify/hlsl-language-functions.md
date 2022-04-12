# Functions

Functions encapsulate HLSL statements. This enables you to debug a set of functions and then reuse them across shaders or effects. You may want to create a function that encapsulates the functionality of a vertex shader, pixel shader or texture shader. Other times, you may want to write a helper function that performs some commonly used task, and then call that helper function from your shader function. The rules for writing shader functions for HLSL are very similar to writing C functions.

## Function Declaration Syntax

```syntax
[StorageClass] [clipplanes()] [precise] Return_Value Name ( [ArgumentList] ) [: Semantic] {   [StatementBlock] };
```

<b>Examples</b>

This example is from BasicHLSL10.fx from the [`BasicHLSL10 Sample`](https://msdn.microsoft.com/library/Ee416395(v=VS.85).aspx).

```HLSL
struct VS_OUTPUT
{
    float4 Position   : SV_POSITION; 
    float4 Diffuse    : COLOR0;
    float2 TextureUV  : TEXCOORD0;
};

VS_OUTPUT RenderSceneVS( float4 vPos : POSITION,
                         float3 vNormal : NORMAL,
                         float2 vTexCoord0 : TEXCOORD,
                         uniform int nNumLights,
                         uniform bool bTexture,
                         uniform bool bAnimate )
{
    VS_OUTPUT Output;
    ...
    return Output;    
}
```

This example from AdvancedParticles.fx from the [`AdvancedParticles`](https://msdn.microsoft.com/library/Ee416394(v=VS.85).aspx) Sample, illustrates using a semantic for the return type.

```HLSL
//
// PS for particles
//
float4 PSPointSprite(PSSceneIn input) : SV_Target
{   
    return g_txDiffuse.Sample( g_samLinear, input.tex ) * input.color;
}
```

### Parameters

#### `StorageClass`

Modifier that redefines a function declaration. `inline` is currently the only modifier value. The modifier value must be `inline` because it is also the default value. Therefore, a function is inline regardless of whether you specify `inline`, and all functions in HLSL are inline. An inline function generates a copy of the function body (when compiling) for each function call. This is done to decrease the overhead of calling the function.

#### `Clipplanes`

Optional list of clip planes, which is up to 6 user-specified clip planes. This is an alternate mechanism for `SV_ClipDistance`.

#### `Name`

An ASCII string that uniquely identifies the name of the shader function.

#### `ArgumentList`

Optional argument list, which is a comma-separated list of `arguments` passed into a function.

#### `Semantic`

Optional string that identifies the intended usage of the return data.

#### `StatementBlock`

Optional `statements` that make up the body of the function. A function defined without a body is called a function prototype; the body of a prototype function must be defined elsewhere before the function can be called.

### Return Value

The return type can be any one of these `HLSL types`.

### Remarks

The syntax on this page describes almost every type of HLSL function, this includes vertex shaders, pixel shaders, and helper functions. While a geometry shader is also implemented with a function, its syntax is a little more complicated, so there is a separate page that defines a geometry shader function declaration (see `Geometry-Shader Object (DirectX HLSL)`).

A function can be overloaded as long as it is given a unique combination of parameter types and/or parameter order. HLSL also implements a number of built in, or `intrinsic functions`.

You can specify user-specific clip planes with the clipplanes attribute. Windows applies these clip planes to all of the primitives drawn. The clipplanes attribute works like `SV_ClipDistance`.

## Function Arguments

A function takes one or more input arguments; use the following syntax to declare each argument.

If there are multiple function arguments, they are separated by commas.

```syntax
[InputModifier] Type Name [: Semantic] [InterpolationModifier] [= Initializers]
```

This example (from the [`BasicHLSL10 Sample`](https://msdn.microsoft.com/library/Ee416395(v=VS.85).aspx)) illustrates uniform and non-uniform inputs to a vertex shader function.

<b>Examples</b>

```HLSL
VS_OUTPUT RenderSceneVS( 
  float4 vPos : POSITION,
  float3 vNormal : NORMAL,
  float2 vTexCoord0 : TEXCOORD,
  uniform int nNumLights,
  uniform bool bTexture,
  uniform bool bAnimate )
{
  ...
}
```

This example (from the [`ContentStreaming Sample`](https://msdn.microsoft.com/library/Ee416397(v=VS.85).aspx)) uses an input structure to pass arguments to a pixel shader function.

```HLSL
VSBasicIn input
struct VSBasicIn
{
  float4 Pos    : POSITION;
  float3 Norm   : NORMAL;
  float2 Tex    : TEXCOORD0;
};

PSBasicIn VSBasic(VSBasicIn input)
{
  ...
}
```

### Parameters

#### `InputModifier`

Optional term that identifies an argument as an input, an output, or both.

| Value | Description |
| - | - |
| `in` | Input Only |
| `inout` | Input and an output |
| `out` | Output Only |
| `uniform` | Input only constant data |

Parameters are always passed by value. in indicates that the value of the parameter should be copied in from the calling application before the function begins. out indicates that the last value of the parameter should be copied out, and returned to the calling application when the function returns. inout is a shorthand for specifying both.

A uniform value comes from a constant register; each vertex shader or pixel shader invocation see the same initial value for a uniform variable. Global variables are treated as if they are declared uniform. For non-top-level functions, uniform is synonymous with `in`. If no parameter usage is specified, the parameter usage is assumed to be `in`.

#### `Type`

The argument type; can be any valid HLSL `type`.

#### `Name`

An ASCII string that uniquely identifies the name of the shader function.

#### `Semantic`

Optional string that identifies the intended usage of the data (see `Semantics (DirectX HLSL)`).

#### `Interpolation Modifier`
	
Optional `interpolation modifier` which allows a shader to determine the method of interpolation. An interpolation modifier on a function argument only applies to an argument used as an input to a pixel shader function.

#### `Initializers`

Optional values for initialization; multiple values are required to initialize multi-component data types.

### Remarks

Function arguments are listed in a comma-separated argument list in a function declaration. As in C functions, each argument must have a parameter name and type declared; an argument to an HLSL function optionally can include a semantic, an initial value, and a pixel shader input can include an interpolation type.

The Type of a function argument could be a structure, which could include a per-member interpolation modifier. If the function argument also has an interpolation modifier, the function argument modifier overrides interpolation modifiers declared within the Type.

## return Statement

A return statement signals the end of a function.

```syntax
return [value];
```

The simplest return statement returns control from the function to the calling program; it returns no value.

```HLSL
void main()
{
    return ;
}
```

However, a return statement can return one or more values. This example returns a literal value:

```HLSL
float main( float input : COLOR0) : COLOR0
{
    return 0;
}
```

This example returns the scalar result of an expression.

```HLSL
return  light.enabled = true ;
```

This example returns a four-component vector that is constructed from a local variable and a literal.

```HLSL
return  float4(color.rgb, 1) ;
```

This example returns a four-component vector that is constructed from the result that is returned from an intrinsic function, together with literal values.

```HLSL
float4 func(float2 a: POSITION): COLOR
{
    return float4(sin(length(a) * 100.0) * 0.5 + 0.5, sin(a.y * 50.0), 0, 1);
}
```

This example returns a structure that contains one or more members.

```HLSL
float4x4 WorldViewProj;

struct VS_OUTPUT
{
    float4 Pos  : POSITION;
};

VS_OUTPUT VertexShader_Tutorial_1(float4 inPos : POSITION )
{
    VS_OUTPUT out;
    out.Pos = mul(inPos, WorldViewProj );
    return out;
};
```

## Signatures

A shader signature is a list of the parameters that are either input to or output from a shader function. In Direct3D 10, adjacent stages effectively share a register array, where the output shader (or pipeline stage) writes data to specific locations in the register array and the input shader must read from the same locations. The API uses shader signatures to bind shader outputs with inputs without the overhead of semantic resolution.

In Direct3D 10, input signatures are generated from a shader-input declaration and the output signature is generated from a shader-output declaration. An input signature is said to be compatible with an output signature when the output signature is a strict subset (argument type and order match) of the input signature. The most straightforward way to achieve this is to link corresponding shader inputs and outputs by the same structure type.

Here is an example of compatible signatures.

```HLSL
// Vertex Shader Output Signature
Struct VSOut
{
  float4 Pos: SV_Position;
  float3 MyNormal: Normal;
  float2 MyTex : Texcoord0;
}

// Pixel Shader Input Signature
Struct PSInWorks
{
  float4 Pos: SV_Position;
  float3 MyNormal: Normal;
}
```

Here is an example of incompatible signatures; the order of parameters in the input signature does not match the order in the output signature.

```HLSL
// Vertex Shader Output Signature
Struct VSOut
{
  float4 Pos: SV_Position;
  float3 MyNormal: Normal;
  float2 MyTex : Texcoord0;
}

// Pixel Shader Input Signature
Struct PSInFails
{
  float3 MyNormal: Normal;
  float4 Pos: SV_Position;
}
```

PSInWorks is a compatible subset of VSOut (the first two entries match both type and order with the first two entries in VSOut). However, PSInFails is incompatible because the ordering does not match with VSOut.
# Variable Syntax

```syntax
[Storage_Class] [Type_Modifier] Type Name[Index] [: Semantic] [: Packoffset] [: Register]; [Annotations] [= Initial_Value]
```



## Parameters

### Storage_Class

Optional storage-class modifiers that give the compiler hints about variable scope and lifetime; the modifiers can be specified in any order.

| Value | Description |
| - | - |
| extern | Mark a global variable as an external input to the shader; this is the default marking for all global variables. Cannot be combined with <b>static</b>. |
| nointerpolation | Do not interpolate the outputs of a vertex shader before passing them to a pixel shader. |
| precise | The precise keyword when applied to a variable will restrict any calculations used to produce the value assigned to that variable in the following ways:* Separate operations are kept separate. For example, where a mul and add operation might have been fused into a mad operation, precise forces the operations to remain separate. Instead, you must explicitly use the mad intrinsic function.* Order of operations are maintained. Where the order of instructions might have been shuffled to improve performance, precise ensures that the compiler preserves the order as written.* IEEE unsafe operations are restricted. Where the compiler might have used fast math operations that don't account for NaN (not a number) and INF (infinite) values, precise forces IEEE requirements concerning NaN and INF values to be respected. Without precise, these optimizations and mathematical operations are not IEEE safe.* Qualifying a variable precise doesn't make operations that use the variable precise. Since precise propagates only to operations that contribute to the values that are assigned to the precise-qualified variable, correctly making desired calculations precise can be tricky, so we recommended that you mark the shader outputs precise directly where you declare them, whether that's on a structure field, or on an output parameter, or the return type of the entry function. The ability to control optimizations in this way maintains result invariance for the modified output variable by disabling optimizations that might affect final results due to differences in accumulated precision differences. It is useful when you want shaders for tessellation to maintain water-tight patch seams or match depth values over multiple passes. [Sample code:](https://github.com/microsoft/DirectXShaderCompiler/blob/master/tools/clang/test/HLSLFileCheck/hlsl/types/modifiers/precise/precise4.hlsl) ```HLSLmatrix g_mWorldViewProjection;void main(in float3 InPos : Position, out precise float4 OutPos : SV_Position){ // operation is precise because it contributes to the precise parameter OutPos OutPos = mul( float4( InPos, 1.0 ), g_mWorldViewProjection );}``` |
| shared | Mark a variable for sharing between effects; this is a hint to the compiler. |
| groupshared | Mark a variable for thread-group-shared memory for compute shaders. In D3D10 the maximum total size of all variables with the groupshared storage class is 16kb, in D3D11 the maximum size is 32kb. See examples. |
| static | Mark a local variable so that it is initialized one time and persists between function calls. If the declaration does not include an initializer, the value is set to zero. A global variable marked static is not visible to an application. |
| uniform | Mark a variable whose data is constant throughout the execution of a shader (such as a material color in a vertex shader); global variables are considered uniform by default. |
| volatile | 	Mark a variable that changes frequently; this is a hint to the compiler. This storage class modifier only applies to a local variable. The HLSL compiler currently ignores this storage class modifier. |

### Type_Modifier

Optional variable-type modifier.

| Value | Description |
| - | - |
| const | Mark a variable that cannot be changed by a shader, therefore, it must be initialized in the variable declaration. Global variables are considered const by default (suppress this behavior by supplying the /Gec flag to the compiler). |
| row_major | Mark a variable that stores four components in a single row so they can be stored in a single constant register. |
| column_major | Mark a variable that stores 4 components in a single column to optimize matrix math. |

>**Note:** If you do not specify a type-modifier value, the compiler uses column_major as the default value.

### Type

Any Type listed in [`Data Types (DirectX HLSL)`](hlsl-variables-dataTypes.md)

### Name[Index]

ASCII string that uniquely identifies a shader variable. To define an optional array, use index for the array size, which is a positive integer = 1.

### Semantic

Optional parameter-usage information, used by the compiler to link shader inputs and outputs. There are several predefined [`semantics`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/dx-graphics-hlsl-semantics) for vertex and pixel shaders. The compiler ignores semantics unless they are declared on a global variable, or a parameter passed into a shader.

### Packoffset

Optional keyword for manually packing shader constants. See [`packoffset (DirectX HLSL)`](hlsl-language-packoffset.md).

### Register

Optional keyword for manually assigning a shader variable to a particular register. See [`register (DirectX HLSL)`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/dx-graphics-hlsl-variable-register).

### Initial_Value

Optional initial value(s); the number of values should match the number of components in Type. Each global variable marked extern must be initialized with a literal value; each variable marked static must be initialized with a constant.

Global variables that are not marked static or extern are not compiled into the shader. The compiler does not automatically set default values for global variables and cannot use them in optimizations. To initialize this type of global variable, use reflection to get its value and then copy the value to a constant buffer. For example, you can use the [`ID3D11ShaderReflection::GetVariableByName`](https://docs.microsoft.com/en-us/windows/desktop/api/d3d11shader/nf-d3d11shader-id3d11shaderreflection-getvariablebyname) method to get the variable, use the [`ID3D11ShaderReflectionVariable::GetDesc`](https://docs.microsoft.com/en-us/windows/desktop/api/d3d11shader/nf-d3d11shader-id3d11shaderreflectionvariable-getdesc) method to get the shader-variable description, and get the initial value from the DefaultValue member of the [`D3D11_SHADER_VARIABLE_DESC`](https://docs.microsoft.com/en-us/windows/desktop/api/d3d11shader/ns-d3d11shader-d3d11_shader_variable_desc) structure. To copy the value to the constant buffer, you must ensure that the buffer was created with CPU write access ([`D3D11_CPU_ACCESS_WRITE`](https://docs.microsoft.com/en-us/windows/desktop/api/d3d11/ne-d3d11-d3d11_cpu_access_flag)). For more information about how to create a constant buffer, see [`How to: Create a Constant Buffer`](https://docs.microsoft.com/en-us/windows/desktop/direct3d11/overviews-direct3d-11-resources-buffers-constant-how-to).

You can also use the [`effects framework`](https://docs.microsoft.com/en-us/windows/win32/direct3d11/d3d11-graphics-programming-guide-effects) to automatically process the reflecting and setting the initial value. For example, you can use the [`ID3DX11EffectPass::Apply`](https://docs.microsoft.com/en-us/windows/desktop/direct3d11/id3dx11effectpass-apply) method.

## Examples

Here are several examples of shader-variable declarations.

```
float fVar;
```

```
float4 color;
float fVar = 3.1f;

int iVar[3];

int iVar[3] = {1,2,3};

uniform float4 position : SV_POSITION; 
const float4 lightDirection = {0,0,1};
```

## Remarks

### GroupShared

HLSL enables threads of a compute shader to exchange values via shared memory. HLSL provides barrier primitives such as [`GroupMemoryBarrierWithGroupSync`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/groupmemorybarrierwithgroupsync), and so on to ensure the correct ordering of reads and writes to shared memory in the shader and to avoid data races.

>**Note:** Hardware executes threads in groups (warps or wave-fronts), and barrier synchronization can sometimes be omitted to increase performance when only synchronizing threads that belong to the same group is correct. But we highly discourage this omission for these reasons: <ul><li>This omission results in non-portable code, which might not work on some hardware and doesn't work on software rasterizers that typically execute threads in smaller groups.</li><li>The performance improvements that you might achieve with this omission will be minor compared to using all-thread barrier.</li></ul>

There is no synchronization of threads when writing to groupshared, so this means that each thread is limited to a single location in an array for writing. Use the SV_GroupIndex system value to index into this array when writing to ensure that no two threads can collide. In terms of reading, all threads have access to the entire array for reading.

```
struct GSData
{
    float4 Color;
    float Factor;
}

groupshared GSData data[5*5*1];

[numthreads(5,5,1)]
void main( uint index : SV_GroupIndex )
{
    data[index].Color = (float4)0;
    data[index].Factor = 2.0f;
    GroupMemoryBarrierWithGroupSync();
    ...
}
```

### Packing

Pack subcomponents of vectors and scalars whose size is large enough to prevent crossing register boundariess. For example, these are all valid:

```
cbuffer MyBuffer
{
    float4 Element1 : packoffset(c0);
    float1 Element2 : packoffset(c1);
    float1 Element3 : packoffset(c1.y);
}
```

Cannot mix packing types.

Like the register keyword, a packoffset can be target specific. Subcomponent packing is only available with the packoffset keyword, not the register keyword. Inside a cbuffer declaration, the register keyword is ignored for Direct3D 10 targets as it is assumed to be for cross-platform compatibility.

Packed elements may overlap and the compiler will give no error or warning. In this example, Element2 and Element3 will overlap with Element1.x and Element1.y.

```
cbuffer MyBuffer
{
    float4 Element1 : packoffset(c0);
    float1 Element2 : packoffset(c0);
    float1 Element3 : packoffset(c0.y);
}
```

A sample that uses packoffset is: [`HLSLWithoutFX10 Sample`](https://msdn.microsoft.com/library/Ee416414(v=VS.85).aspx).

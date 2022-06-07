# Global Blocks

In Shader Model 4, shader constants are stored in one or more buffer resources in memory. They can be organized into two types of buffers: constant buffers (cbuffers) and texture buffers (tbuffers). Constant buffers are optimized for constant-variable usage, which is characterized by lower-latency access and more frequent update from the CPU. For this reason, additional size, layout, and access restrictions apply to these resources. Texture buffers are accessed like textures and perform better for arbitrarily indexed data. Regardless of which type of resource you use, there is no limit to the number of constant buffers or texture buffers an application can create.

Declaring a constant buffer or a texture buffer looks very much like a structure declaration in C, with the addition of the **register** and **packoffset** keywords for manually assigning registers or packing data.

```syntax
BufferType [Name] [: register(b#)] { VariableDeclaration [: packoffset(c#.xyzw)]; ... };
```

## Constant Buffer Packing

#### Packing Rules for Constant Variables

Packing rules dictate how tightly data can be arranged when it is stored. HLSL implements packing rules for VS output data, GS input and output data, and PS input and output data. (Data is not packed for VS inputs because the IA stage cannot unpack data.)

HLSL packing rules are similar to performing a <b>#pragma pack 4</b> with Visual Studio, which packs data into 4-byte boundaries. Additionally, HLSL packs data so that it does not cross a 16-byte boundary. Variables are packed into a given four-component vector until the variable will straddle a 4-vector boundary; the next variables will be bounced to the next four-component vector.

Each structure forces the next variable to start on the next four-component vector. This sometimes generates padding for arrays of structures. The resulting size of any structure will always be evenly divisible by <b>sizeof</b>(<i>four-component vector</i>).

Arrays are not packed in HLSL by default. To avoid forcing the shader to take on ALU overhead for offset computations, every element in an array is stored in a four-component vector. Note that you can achieve packing for arrays (and incur the addressing calculations) by using casting.

Following are examples of structures and their corresponding packed sizes (given: a <b>float1</b> occupies 4 bytes):

```hlsl
//  2 x 16byte elements
cbuffer IE
{
    float4 Val1;
    float2 Val2;  // starts a new vector
    float2 Val3;
};

//  3 x 16byte elements
cbuffer IE
{
    float2 Val1;
    float4 Val2;  // starts a new vector
    float2 Val3;  // starts a new vector
};

//  1 x 16byte elements
cbuffer IE
{
    float1 Val1;
    float1 Val2;
    float2 Val3;
};

//  1 x 16byte elements
cbuffer IE
{
    float1 Val1;
    float2 Val2;
    float1 Val3;
};

//  2 x 16byte elements
cbuffer IE
{
    float1 Val1;
    float1 Val1;
    float1 Val1;
    float2 Val2;    // starts a new vector
};


//  1 x 16byte elements
cbuffer IE
{
    float3 Val1;
    float1 Val2;
};

//  1 x 16byte elements
cbuffer IE
{
    float1 Val1;
    float3 Val2;
};

//  2 x 16byte elements
cbuffer IE
{
    float1 Val1;
    float1 Val1;
    float3 Val2;        // starts a new vector
};


// 3 x 16byte elements
cbuffer IE
{
    float1 Val1;

    struct     {
        float4 SVal1;    // starts a new vector
        float1 SVal2;    // starts a new vector
    } Val2;
};

// 3 x 16byte elements
cbuffer IE
{
    float1 Val1;  
    struct     {
        float1 SVal1;     // starts a new vector
        float4 SVal2;     // starts a new vector
    } Val2;
};

// 3 x 16byte elements
cbuffer IE
{
    struct     {
        float4 SVal1;
        float1 SVal2;    // starts a new vector
    } Val1;

    float1 Val2; 
};
```

You could pack an array more aggressively. For instance, given an array of float variables:

```hlsl
float4 array[16];
```

You could choose to pack it like this, without any spaces in the array:

```hlsl
static float2 aggressivePackArray[32] = (float2[32])array;
```

The tighter packing is a trade off versus the need for additional shader instructions for address computation.

### "Legacy" Constant Buffer Basics (excluding min-precision or 16-bit types)

1. The Constant Buffer is arranged like an array of 16-byte rows.
1. Certain basic types will be packed into the last used row if they fit into the available space, starting at the next available aligned position. If they do not fit, they will start a new 16-byte aligned row.
    1. [`Scalars`](hlsl-variables-dataTypes.md#scalar-types)
    1. [`Vectors`](hlsl-variables-dataTypes.md#vector-types)
    1. [`Matrix`](hlsl-variables-dataTypes.md#matrix-type) with only one row in row_major equivalent storage layout.
1. [`Matrix`](hlsl-variables-dataTypes.md#matrix-type) types with more than one row in row_major equivalent storage layout are aligned to the 16-byte row. Each row in storage layout (each column for column_major matrix) is aligned to a 16-byte row.
1. Aggregates (arrays and [`struct`](hlsl-language-type-struct.md) type) are always 16-byte row-aligned. If the aggregate ends in an element that does not completely fill a row, the remaining space on the last row may be used by the next value.
1. [`Struct`](hlsl-language-type-struct.md) members follow these same rules. Because structures are always 16-byte row-aligned, the offset layout within the structure (for use in legacy constant buffers) is independent of the particular structure instance location.

### "Legacy" Layout in min-precision mode (default)

In addition to the rules above, min-precision values introduce extra packing constraints. A row with min-precision values cannot also contain fixed precision values (such as float, bool, half, uint, double, uint64_t, etc...). Therefore, no min-precision value will be packed into the remaining space on the last row if the last row contains fixed precision values, and no fixed precision value will be packed into a row containing min-precision values. In each case, a new row is started.

### [`"Legacy" Layout in native 16-bit types mode`](hlsl_using_compiler_cl.md#"legacy"-layout-in-native-16-bit-types-mode--enable-16bit-types)

### [`"Non-Legacy" packing`](hlsl_using_compiler_cl.md#"non-legacy"-packing--no-legacy-cbuf-layout)

## Parameters

<dl> <dt>

<span id="BufferType"></span><span id="buffertype"></span><span id="BUFFERTYPE"></span>*BufferType*
</dt> <dd>

\[in\] The buffer type.



| BufferType | Description     |
|------------|-----------------|
| cbuffer    | constant buffer |
| tbuffer    | texture buffer  |



 

</dd> <dt>

<span id="Name"></span><span id="name"></span><span id="NAME"></span>*Name*
</dt> <dd>

\[in\] Optional, ASCII string containing a unique buffer name.

</dd> <dt>

<span id="register_b__"></span><span id="REGISTER_B__"></span>**register**(b\#)
</dt> <dd>

\[in\] Optional keyword, used to manually pack constant data. Constants can be packed in a register only in a constant buffer, where the starting register is given by the register number (*\#*).

</dd> <dt>

<span id="VariableDeclaration"></span><span id="variabledeclaration"></span><span id="VARIABLEDECLARATION"></span>*VariableDeclaration*
</dt> <dd>

\[in\] Variable declaration, similar to a structure member declaration. This can be any HLSL type or effect object (except a texture or a sampler object).

</dd> <dt>

<span id="packoffset_c_.xyzw_"></span><span id="PACKOFFSET_C_.XYZW_"></span>**packoffset**(c\#.xyzw)
</dt> <dd>

\[in\] Optional keyword, used to manually pack constant data. Constants can be packed in any constant buffer, where the register number is given by (*\#*). Sub-component packing (using xyzw swizzling) is available for constants whose size fit within a single register (do not cross a register boundary). For instance, a float4 could not be packed in a single register starting with the y-component because it would not fit in a four-component register.

</dd> </dl>

## Remarks

Constant buffers reduce the bandwidth required to update shader constants by allowing shader constants to be grouped together and committed at the same time rather than making individual calls to commit each constant separately.

A constant buffer is a specialized buffer resource that is accessed like a buffer. Each constant buffer can hold up to 4096 [vectors](hlsl-variables-dataTypes.md#vector-types); each vector contains up to four 32-bit values. You can bind up to 14 constant buffers per pipeline stage (2 additional slots are reserved for internal use).

A texture buffer is a specialized buffer resource that is accessed like a texture. Texture access (as compared with buffer access) can have better performance for arbitrarily indexed data. You can bind up to 128 texture buffers per pipeline stage.

A buffer resource is designed to minimize the overhead of setting shader constants. The effect framework (see [**ID3D10Effect Interface**](/windows/desktop/api/d3d10effect/nn-d3d10effect-id3d10effect)) will manage updating constant and texture buffers, or you can use the Direct3D API to update buffers (see [Copying and Accessing Resource Data (Direct3D 10)](/windows/desktop/direct3d10/d3d10-graphics-programming-guide-resources-mapping) for information). An application can also copy data from another buffer (such as a render target or a stream-output target) into a constant buffer.

For more info on using constant buffers in a D3D10 application, see [Resource Types (Direct3D 10)](/windows/desktop/direct3d10/d3d10-graphics-programming-guide-resources-types) and [Creating Buffer Resources (Direct3D 10)](/windows/desktop/direct3d10/d3d10-graphics-programming-guide-resources-creating).

For morel info on using constant buffers in a D3D11 application, see [Introduction to Buffers in Direct3D 11](/windows/desktop/direct3d11/overviews-direct3d-11-resources-buffers-intro) and [How to: Create a Constant Buffer](/windows/desktop/direct3d11/overviews-direct3d-11-resources-buffers-constant-how-to).

A constant buffer does not require a [view](/windows/desktop/direct3d10/d3d10-graphics-programming-guide-resources-access-views) to be bound to the pipeline. A texture buffer, however, requires a view and must be bound to a texture slot (or must be bound with [**SetTextureBuffer**](/windows/desktop/api/d3d10effect/nf-d3d10effect-id3d10effectconstantbuffer-settexturebuffer) when using an effect).

There are two ways to pack constants data: using the [register](hlsl-language-register.md) and [packoffset](hlsl-language-packoffset.md) keywords.

Differences between Direct3D 9 and Direct3D 10 and 11:

- Unlike the auto-allocation of constants in Direct3D 9, which did not perform packing and instead assigned each variable to a set of float4 registers, HLSL constant variables follow packing rules in Direct3D 10 and 11.



 

### Organizing constant buffers

Constant buffers reduce the bandwidth required to update shader constants by allowing shader constants to be grouped together and committed at the same time rather than making individual calls to commit each constant separately.

The best way to efficiently use constant buffers is to organize shader variables into constant buffers based on their frequency of update. This allows an application to minimize the bandwidth required for updating shader constants. For example, a shader might declare two constant buffers and organize the data in each based on their frequency of update: data that needs to be updated on a per-object basis (like a world matrix) is grouped into a constant buffer which could be updated for each object. This is separate from data that characterizes a scene and is therefore likely to be updated much less often (when the scene changes).


```
cbuffer myObject
{       
    float4x4 matWorld;
    float3   vObjectPosition;
    int      arrayIndex;
}
 
cbuffer myScene
{
    float3   vSunPosition;
    float4x4 matView;
}
        
```



### Default constant buffers

There are two default constant buffers available, $Global and $Param. Variables that are placed in the global scope are added implicitly to the $Global cbuffer, using the same packing method that is used for cbuffers. Uniform parameters in the parameter list of a function appear in the $Param constant buffer when a shader is compiled outside of the effects framework. When compiled inside the effects framework, all uniforms must resolve to variables defined in the global scope.

## Examples

Here is an example from [Skinning10 Sample](https://msdn.microsoft.com/library/Ee416429(v=VS.85).aspx) that is a texture buffer made up of an array of matrices.


```
tbuffer tbAnimMatrices
{
    matrix g_mTexBoneWorld[MAX_BONE_MATRICES];
};
      
```



This example declaration manually assigns a constant buffer to start at a particular register, and also packs particular elements by subcomponents.


```
cbuffer MyBuffer : register(b3)
{
    float4 Element1 : packoffset(c0);
    float1 Element2 : packoffset(c1);
    float1 Element3 : packoffset(c1.y);
}
      
```
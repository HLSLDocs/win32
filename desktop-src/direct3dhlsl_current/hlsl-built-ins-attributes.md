# Built-in Attributes

Built-in [`attributes`](dx-graphics-hlsl.md) describe additional behavior when place before language elements.

## Entry Function Attributes

### domain

Defines the patch type used in the HS.


```
[domain(X)]      
```



#### Remarks

X is either **tri**, **quad**, or **isoline**.

### earlydepthstencil

Forces depth-stencil testing before a shader executes.


```
[earlydepthstencil]   
```



#### Remarks

Depth-stencil testing is normally done during pixel processing by a pixel shader. Forcing early depth-stencil testing causes the testing to be done prior to the shader execution; the purpose is to improve per-pixel performance by culling/reducing/avoiding unnecessary pixel processing.

An application can force early depth-stencil testing by supplying the attribute or the hardware may execute early depth-stencil testing provided no depth values are written and no unordered access operations are performed in a shader as an optimization.

### instance

Use this attribute to instance a geometry shader.


```
]instance(X)]   
```



#### Remarks

X is an integer index that indicates the number of instances to be executed for each drawn item (for example, for each triangle). When using this attribute, use [SV\_GSInstanceID](sv-gsinstanceid.md) to identify which instance of a geometry shader is being executed.

### maxtessfactor

Indicates the maximum value that the hull shader would return for any tessellation factor.


```
[maxtessfactor(X)]   
```



#### Remarks

This attribute puts an upper bound on the amount of tessellation requested to help a driver determine the maximum amount of resources required for tessellation.

### numthreads

Defines the number of threads to be executed in a single thread group when a compute shader is dispatched (see [**ID3D11DeviceContext::Dispatch**](/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-dispatch)).


```
[numthreads(X, Y, Z)]    
```



The X, Y and Z values indicate the size of the thread group in a particular direction and the total of X\*Y\*Z gives the number of threads in the group. The ability to specify the size of the thread group across three dimensions allows individual threads to be accessed in a manner that logically 2D and 3D data structures.

For example, if a compute shader is doing 4x4 matrix addition then numthreads could be set to numthreads(4,4,1) and the indexing in the individual threads would automatically match the matrix entries. The compute shader could also declare a thread group with the same number of threads (16) using numthreads(16,1,1), however it would then have to calculate the current matrix entry based on the current thread number.

The allowable parameter values for **numthreads** depends on the compute shader version.



| Compute Shader | Maximum Z | Maximum Threads (X\*Y\*Z) |
|----------------|-----------|---------------------------|
| cs\_4\_x       | 1         | 768                       |
| cs\_5\_0       | 64        | 1024                      |



 

The following illustration shows the relationship between the parameters passed to [**ID3D11DeviceContext::Dispatch**](/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-dispatch), Dispatch(5,3,2), the values specified in the numthreads attribute, numthreads(10,8,3), and values that will passed to the compute shader for the thread related system values ([SV\_GroupIndex](sv-groupindex.md),[SV\_DispatchThreadID](sv-dispatchthreadid.md),[SV\_GroupThreadID](sv-groupthreadid.md),[SV\_GroupID](sv-groupid.md)).

![illustration of the relationship between dispatch, thread groups, and threads](images/threadgroupids.png)

### outputcontrolpoints

Defines the number of output control points (per thread) that will be created in the hull shader.


```
[outputcontrolpoints(X)]
```



#### Remarks

This will be the number of times the main function will be executed.

### outputtopology

Defines the output primitive type for the tessellator.


```
[outputtopology(X)]      
```



#### Remarks

X must be either [**point**](dx-graphics-hlsl-geometry-shader.md), **line**, **triangle\_cw**, or **triangle\_ccw** and must be inside quotes. Here are the valid options for this attribute:


```
[outputtopology("point")]
[outputtopology("line")]
[outputtopology("triangle_cw")]
[outputtopology("triangle_ccw")]
```

### partitioning

Defines the tesselation scheme to be used in the hull shader.


```
[partitioning(X)]    
```



#### Remarks

Can be **integer**, **fractional\_even**, **fractional\_odd**, or **pow2**.

### patchconstantfunc

Defines the function for computing patch constant data.


```
[patchconstantfunc("function_name")]
```



#### Remarks

*function\_name* is the name of a separate function that outputs the patch-constant data.

## Flow Control

| Attribute | Description |
|-----------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| fastopt   | Reduces the compile time but produces less aggressive optimizations. If you use this attribute, the compiler will not unroll loops.<br/> This attribute affects only shader model targets that support [break](dx-graphics-hlsl-break.md) instructions. This attribute is available in shader model [vs\_2\_x](dx9-graphics-reference-asm-vs-2-x.md) and [shader model 3](dx-graphics-hlsl-sm3.md) and later. It is particularly useful in [shader model 4](dx-graphics-hlsl-sm4.md) and later when the compiler compiles loops. The compiler simulates loops by default to evaluate whether it can unroll them. If you do not want the compiler to unroll loops, use this attribute to reduce compile time.<br/> |

### for Statement

When no attribute is specified the compiler will first attempt to emit a rolled version of the loop, and if that fails, or if some operations would be easier if the loop was unrolled, will fall back to an unrolled version of the loop.

| Attribute             | Description |
|-----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| unroll(x)             | Unroll the loop until it stops executing. Can optionally specify the maximum number of times the loop is to execute. Not compatible with the **\[loop\]** attribute.                                                    

When the **unroll** attribute is applied on a loop and if the loop-trip&ndash;count can't be ascertained at compile-time or if it's above a certain threshold, then by default, DXC fails to compile shaders such as the following. To turn this failure into a warning, set the language version to 2016. When the following shader is compiled on DXC with the `-HV 2016` flag, it compiles successfully without unrolling the loop and generates a warning message: `warning: Could not unroll the loop.`                                                             ```hlsl
uint main(uint x : IN) : OUT
{
   uint r = 0;
   [unroll]
   for(uint i=0; i<x; i++)
    r+=i;
   return r;
}
```                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| loop                  | Generate code that uses flow control to execute each iteration of the loop. Not compatible with the **\[unroll\]** attribute.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| fastopt               | Reduces the compile time but produces less aggressive optimizations. If you use this attribute, the compiler will not unroll loops.<br/> This attribute affects only shader model targets that support [break](dx-graphics-hlsl-break.md) instructions. This attribute is available in shader model [vs\_2\_x](dx9-graphics-reference-asm-vs-2-x.md) and [shader model 3](dx-graphics-hlsl-sm3.md) and later. It is particularly useful in [shader model 4](dx-graphics-hlsl-sm4.md) and later when the compiler compiles loops. The compiler simulates loops by default to evaluate whether it can unroll them. If you do not want the compiler to unroll loops, use this attribute to reduce compile time. <br/> |
| allow\_uav\_condition | Allows a compute shader loop termination condition to be based off of a UAV read. The loop must not contain synchronization intrinsics. |

#### Remarks

The **\[unroll\]** and **\[loop\]** attributes are mutually exclusive and will generate compiler errors when both are specified.

The **\[fastopt\]** and **\[allow\_uav\_condition\]** attributes are ignored if **\[unroll\]** is specified.

### if Statement

| Attribute | Description | 
|-----------|-------------|
| branch | Evaluate only one side of the if statement depending on the given condition.<blockquote>[!Note]<br />When you use <a href="dx-graphics-hlsl-sm2.md">Shader Model 2.x</a> or <a href="dx-graphics-hlsl-sm3.md">Shader Model 3.0</a>, each time you use dynamic branching you consume resources. So, if you use dynamic branching excessively when you target these profiles, you can receive compilation errors.</blockquote><br /> | 
| flatten | Evaluate both sides of the if statement and choose between the two resulting values. | 

#### Remarks

When the compiler uses the branch method for compiling an if statement it will generate code that will evaluate only one side of the if statement depending on the given condition. For example, in the if statement:


```
[branch] if(x)
{
    x = sqrt(x);
}
```



The **if** statement has an implicit else block, which is equivalent to x = x. Because we have told the compiler to use the branch method with the preceding branch attribute, the compiled code will evaluate x and execute only the side that should be executed; if x is zero, then it will execute the **else** side, and if it is non-zero it will execute the **then** side.

Conversely, if the **flatten** attribute is used, then the compiled code will evaluate both sides of the **if** statement and choose between the two resulting values using the original value of x. Here is an example of a usage of the flatten attribute:


```
[flatten] if(x)
{
    x = sqrt(x);
}
```



There are certain cases where using the branch or flatten attributes may generate a compile error. The branch attribute may fail if either side of the if statement contains a gradient function, such as [**tex2D**](dx-graphics-hlsl-tex2d.md). The flatten attribute may fail if either side of the if statement contains a stream append statement or any other statement that has side-effects.

An **if** statement can also use an optional else block. If the **if** expression is true, the code in the statement block associated with the if statement is processed. Otherwise, the statement block associated with the optional else block is processed.

### switch Statement

| Attribute | Description | 
|-----------|-------------|
| flatten | Compile the statement as a series of <strong>if</strong> statements, each with the <strong>flatten</strong> attribute. | 
| branch | Compile the statement as a series of <strong>if</strong> statements each with the <strong>branch</strong> attribute.<blockquote>[!Note]<br />When you use <a href="dx-graphics-hlsl-sm2.md">Shader Model 2.x</a> or <a href="dx-graphics-hlsl-sm3.md">Shader Model 3.0</a>, each time you use dynamic branching you consume resources. So, if you use dynamic branching excessively when you target these profiles, you can receive compilation errors.</blockquote><br /> | 
| forcecase | Force a switch statement in the hardware.<blockquote>[!Note]<br />Requires <a href="/windows/desktop/direct3d11/overviews-direct3d-11-devices-downlevel-intro">feature level</a> 10_0 or later hardware.</blockquote><br /> | 
| call | The bodies of the individual cases in the switch will be moved into hardware subroutines and the switch will be a series of subroutine calls.<blockquote>[!Note]<br />Requires <a href="/windows/desktop/direct3d11/overviews-direct3d-11-devices-downlevel-intro">feature level</a> 10_0 or later hardware.</blockquote><br /> | 

#### Remarks


```
[branch] switch(a)
{
    case 0:
        return 0; 
    case 1:
        return 1; 
    case 2:
        return 3; 
    default:
        return 6; 
}
```



Is equivalent to:


```
[branch] if( a == 2 )
    return 3;
else if( a == 1 )
    return 1;
else if( a == 0 )
    return 0;
else
    return 6;
```



Here are example usages of forcecase and call flow control attributes:


```
[forcecase] switch(a)
{
    case 0:
        return 0; 
    case 1:
        return 1; 
    case 2:
        return 3; 
    default:
        return 6; 
}

[call] switch(a)
{
    case 0:
        return 0; 
    case 1:
        return 1; 
    case 2:
        return 3; 
    default:
        return 6; 
}
```

### while Statement

| Attribute             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|-----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| unroll(x)             | Unroll the loop until it stops executing. Optionally, you can specify the maximum number of times the loop can execute.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| loop                  | Use flow-control statements in the compiled shader; do not unroll the loop.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| fastopt               | Reduces the compile time but produces less aggressive optimizations. If you use this attribute, the compiler will not unroll loops.<br/> This attribute affects only shader model targets that support [break](dx-graphics-hlsl-break.md) instructions. This attribute is available in shader model [vs\_2\_x](dx9-graphics-reference-asm-vs-2-x.md) and [shader model 3](dx-graphics-hlsl-sm3.md) and later. It is particularly useful in [shader model 4](dx-graphics-hlsl-sm4.md) and later when the compiler compiles loops. The compiler simulates loops by default to evaluate whether it can unroll them. If you do not want the compiler to unroll loops, use this attribute to reduce compile time.<br/> |
| allow\_uav\_condition | Allows a compute shader loop termination condition to be based off of a UAV read. The loop must not contain synchronization intrinsics. |

## Functions

## Raytracing
# Built-in Attributes

## General

### domain

Defines the patch type used in the HS.


```
domain(X)      
```



#### Remarks

X is either **tri**, **quad**, or **isoline**.

### earlydepthstencil

Forces depth-stencil testing before a shader executes.


```
earlydepthstencil   
```



#### Remarks

Depth-stencil testing is normally done during pixel processing by a pixel shader. Forcing early depth-stencil testing causes the testing to be done prior to the shader execution; the purpose is to improve per-pixel performance by culling/reducing/avoiding unnecessary pixel processing.

An application can force early depth-stencil testing by supplying the attribute or the hardware may execute early depth-stencil testing provided no depth values are written and no unordered access operations are performed in a shader as an optimization.

### instance

Use this attribute to instance a geometry shader.


```
instance(X)   
```



#### Remarks

X is an integer index that indicates the number of instances to be executed for each drawn item (for example, for each triangle). When using this attribute, use [SV\_GSInstanceID](sv-gsinstanceid.md) to identify which instance of a geometry shader is being executed.

### maxtessfactor

Indicates the maximum value that the hull shader would return for any tessellation factor.


```
maxtessfactor(X)   
```



#### Remarks

This attribute puts an upper bound on the amount of tessellation requested to help a driver determine the maximum amount of resources required for tessellation.

### numthreads

Defines the number of threads to be executed in a single thread group when a compute shader is dispatched (see [**ID3D11DeviceContext::Dispatch**](/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-dispatch)).


```
numthreads(X, Y, Z)    
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
outputcontrolpoints(X)
```



#### Remarks

This will be the number of times the main function will be executed.

### outputtopology

Defines the output primitive type for the tessellator.


```
outputtopology(X)      
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
partitioning(X)    
```



#### Remarks

Can be **integer**, **fractional\_even**, **fractional\_odd**, or **pow2**.

### patchconstantfunc

Defines the function for computing patch constant data.


```
patchconstantfunc("function_name")
```



#### Remarks

*function\_name* is the name of a separate function that outputs the patch-constant data.

## Flow Control

### break Statement

Exit the surrounding loop ([do](dx-graphics-hlsl-do.md), [for](dx-graphics-hlsl-for.md), [while](dx-graphics-hlsl-while.md)).

break;



 

#### Parameters

None


### continue Statement

Stop executing the current loop ([do](dx-graphics-hlsl-do.md), [for](dx-graphics-hlsl-for.md), [while](dx-graphics-hlsl-while.md)), update the loop conditions, and begin executing from the top of the loop.

continue;



 

#### Parameters

None

### discard Statement

Do not output the result of the current pixel.

discard;



 

#### Parameters

None

#### Remarks

This statement can only be called from a pixel shader; it is not supported within a geometry shader or a vertex shader.

### do Statement

Execute a series of statements continuously until the conditional expression fails.

\[*Attribute*\] do {   *Statement Block*; } while( *Conditional* );



 

#### Parameters

<dl> <dt>

<span id="Attribute"></span><span id="attribute"></span><span id="ATTRIBUTE"></span>*Attribute*
</dt> <dd>

An optional parameter that controls how the statement is compiled.



| Attribute | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|-----------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| fastopt   | Reduces the compile time but produces less aggressive optimizations. If you use this attribute, the compiler will not unroll loops.<br/> This attribute affects only shader model targets that support [break](dx-graphics-hlsl-break.md) instructions. This attribute is available in shader model [vs\_2\_x](dx9-graphics-reference-asm-vs-2-x.md) and [shader model 3](dx-graphics-hlsl-sm3.md) and later. It is particularly useful in [shader model 4](dx-graphics-hlsl-sm4.md) and later when the compiler compiles loops. The compiler simulates loops by default to evaluate whether it can unroll them. If you do not want the compiler to unroll loops, use this attribute to reduce compile time.<br/> |



 

</dd> <dt>

<span id="Statement_Block"></span><span id="statement_block"></span><span id="STATEMENT_BLOCK"></span>*Statement Block*
</dt> <dd>

One or more [statements](dx-graphics-hlsl-statement-blocks.md).

</dd> <dt>

<span id="Conditional"></span><span id="conditional"></span><span id="CONDITIONAL"></span>*Conditional*
</dt> <dd>

A conditional [expression](dx-graphics-hlsl-expressions.md). The statement block is executed before the expression is evaluated. The loop is exited when the expression evaluates to false.

</dd> </dl>

## Requirements



| Requirement | Value |
|-------------------|------------------------------------------------------------------------------------|
| Header<br/> | <dl> <dt>Ocidl.h</dt> </dl> |

### for Statement

Iteratively executes a series of statements, based on the evaluation of the conditional expression.

\[*Attribute*\] for ( *Initializer; Conditional; Iterator* ) {   *Statement Block*; }



 

#### Parameters

<dl> <dt>

<span id="Attribute"></span><span id="attribute"></span><span id="ATTRIBUTE"></span>*Attribute*
</dt> <dd>

An optional parameter that controls how the statement is compiled. When no attribute is specified the compiler will first attempt to emit a rolled version of the loop, and if that fails, or if some operations would be easier if the loop was unrolled, will fall back to an unrolled version of the loop.



| Attribute             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
|-----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| unroll(x)             | Unroll the loop until it stops executing. Can optionally specify the maximum number of times the loop is to execute. Not compatible with the **\[loop\]** attribute.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| loop                  | Generate code that uses flow control to execute each iteration of the loop. Not compatible with the **\[unroll\]** attribute.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| fastopt               | Reduces the compile time but produces less aggressive optimizations. If you use this attribute, the compiler will not unroll loops.<br/> This attribute affects only shader model targets that support [break](dx-graphics-hlsl-break.md) instructions. This attribute is available in shader model [vs\_2\_x](dx9-graphics-reference-asm-vs-2-x.md) and [shader model 3](dx-graphics-hlsl-sm3.md) and later. It is particularly useful in [shader model 4](dx-graphics-hlsl-sm4.md) and later when the compiler compiles loops. The compiler simulates loops by default to evaluate whether it can unroll them. If you do not want the compiler to unroll loops, use this attribute to reduce compile time. <br/> |
| allow\_uav\_condition | Allows a compute shader loop termination condition to be based off of a UAV read. The loop must not contain synchronization intrinsics.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |



 

</dd> <dt>

<span id="Initializer"></span><span id="initializer"></span><span id="INITIALIZER"></span>*Initializer*
</dt> <dd>

The initial value of the loop counter.

</dd> <dt>

<span id="Conditional"></span><span id="conditional"></span><span id="CONDITIONAL"></span>*Conditional*
</dt> <dd>

A conditional [expression](dx-graphics-hlsl-expressions.md). If the conditional expression evaluates to true, the statement block is executed. The loop ends when the expression evaluates to false.

</dd> <dt>

<span id="Iterator"></span><span id="iterator"></span><span id="ITERATOR"></span>*Iterator*
</dt> <dd>

Update the value of the loop counter.

</dd> <dt>

<span id="Statement_Block"></span><span id="statement_block"></span><span id="STATEMENT_BLOCK"></span>*Statement Block*
</dt> <dd>

One or more [HLSL statements](dx-graphics-hlsl-statement-blocks.md).

</dd> </dl>

#### Remarks

The **\[unroll\]** and **\[loop\]** attributes are mutually exclusive and will generate compiler errors when both are specified.

The **\[fastopt\]** and **\[allow\_uav\_condition\]** attributes are ignored if **\[unroll\]** is specified.

### if Statement

Conditionally execute a series of statements, based on the evaluation of the conditional expression.

\[*Attribute*\] if ( *Conditional* ) {   *Statement Block*; }



 

#### Parameters

<dl> <dt>

<span id="Attribute"></span><span id="attribute"></span><span id="ATTRIBUTE"></span>*Attribute*
</dt> <dd>

An optional parameter that controls how the statement is compiled.




| Attribute | Description | 
|-----------|-------------|
| branch | Evaluate only one side of the if statement depending on the given condition.<blockquote>[!Note]<br />When you use <a href="dx-graphics-hlsl-sm2.md">Shader Model 2.x</a> or <a href="dx-graphics-hlsl-sm3.md">Shader Model 3.0</a>, each time you use dynamic branching you consume resources. So, if you use dynamic branching excessively when you target these profiles, you can receive compilation errors.</blockquote><br /> | 
| flatten | Evaluate both sides of the if statement and choose between the two resulting values. | 




 

</dd> <dt>

<span id="Conditional"></span><span id="conditional"></span><span id="CONDITIONAL"></span>*Conditional*
</dt> <dd>

A conditional [expression](dx-graphics-hlsl-expressions.md). The expression is evaluated, and if true, the statement block is executed.

</dd> <dt>

<span id="Statement_Block"></span><span id="statement_block"></span><span id="STATEMENT_BLOCK"></span>*Statement Block*
</dt> <dd>

One or more [HLSL statements](dx-graphics-hlsl-statement-blocks.md).

</dd> </dl>

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

Transfer control to a different statement block within the switch body depending on the value of a selector.


\[*Attribute*\] switch( *Selector* ) {   case 0 :     { *StatementBlock*; }   break;   case 1 :     { *StatementBlock*; }   break;   case n :     { *StatementBlock*; }   break;   default :     { *StatementBlock*; }   break;



 

#### Parameters

<dl> <dt>

<span id="Attribute"></span><span id="attribute"></span><span id="ATTRIBUTE"></span>*Attribute*
</dt> <dd>

An optional parameter that controls how the statement is compiled. When no attribute is specified, the compiler may use a hardware switch or emit a series of **if** statements.




| Attribute | Description | 
|-----------|-------------|
| flatten | Compile the statement as a series of <strong>if</strong> statements, each with the <strong>flatten</strong> attribute. | 
| branch | Compile the statement as a series of <strong>if</strong> statements each with the <strong>branch</strong> attribute.<blockquote>[!Note]<br />When you use <a href="dx-graphics-hlsl-sm2.md">Shader Model 2.x</a> or <a href="dx-graphics-hlsl-sm3.md">Shader Model 3.0</a>, each time you use dynamic branching you consume resources. So, if you use dynamic branching excessively when you target these profiles, you can receive compilation errors.</blockquote><br /> | 
| forcecase | Force a switch statement in the hardware.<blockquote>[!Note]<br />Requires <a href="/windows/desktop/direct3d11/overviews-direct3d-11-devices-downlevel-intro">feature level</a> 10_0 or later hardware.</blockquote><br /> | 
| call | The bodies of the individual cases in the switch will be moved into hardware subroutines and the switch will be a series of subroutine calls.<blockquote>[!Note]<br />Requires <a href="/windows/desktop/direct3d11/overviews-direct3d-11-devices-downlevel-intro">feature level</a> 10_0 or later hardware.</blockquote><br /> | 




 

</dd> <dt>

<span id="Selector"></span><span id="selector"></span><span id="SELECTOR"></span>*Selector*
</dt> <dd>

A variable. The case statements inside the curly brackets will each check this variable to see if the SwitchValue matches their particular CaseValue.

</dd> <dt>

<span id="StatementBlock"></span><span id="statementblock"></span><span id="STATEMENTBLOCK"></span>*StatementBlock*
</dt> <dd>

One or more [statements](dx-graphics-hlsl-statement-blocks.md).

</dd> </dl>

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



#### Requirements



| Requirement | Value |
|-------------------|-------------------------------------------------------------------------------------|
| Header<br/> | <dl> <dt>Urlmon.h</dt> </dl> |

### while Statement

Executes a statement block until the conditional expression fails.

\[*Attribute*\] while ( *Conditional* ) {   *Statement Block*; }



 

#### Parameters

<dl> <dt>

<span id="Attribute"></span><span id="attribute"></span><span id="ATTRIBUTE"></span>*Attribute*
</dt> <dd>

An optional parameter that controls how the statement is compiled.



| Attribute             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|-----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| unroll(x)             | Unroll the loop until it stops executing. Optionally, you can specify the maximum number of times the loop can execute.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| loop                  | Use flow-control statements in the compiled shader; do not unroll the loop.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| fastopt               | Reduces the compile time but produces less aggressive optimizations. If you use this attribute, the compiler will not unroll loops.<br/> This attribute affects only shader model targets that support [break](dx-graphics-hlsl-break.md) instructions. This attribute is available in shader model [vs\_2\_x](dx9-graphics-reference-asm-vs-2-x.md) and [shader model 3](dx-graphics-hlsl-sm3.md) and later. It is particularly useful in [shader model 4](dx-graphics-hlsl-sm4.md) and later when the compiler compiles loops. The compiler simulates loops by default to evaluate whether it can unroll them. If you do not want the compiler to unroll loops, use this attribute to reduce compile time.<br/> |
| allow\_uav\_condition | Allows a compute shader loop termination condition to be based off of a UAV read. The loop must not contain synchronization intrinsics.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |



 

</dd> <dt>

<span id="Conditional"></span><span id="conditional"></span><span id="CONDITIONAL"></span>*Conditional*
</dt> <dd>

A conditional [expression](dx-graphics-hlsl-expressions.md). If the expression evaluates to true, the statement block is executed. The loop ends when the expression evaluates to false.

</dd> <dt>

<span id="Statement_Block"></span><span id="statement_block"></span><span id="STATEMENT_BLOCK"></span>*Statement Block*
</dt> <dd>

One or more [statements](dx-graphics-hlsl-statement-blocks.md).

</dd> </dl>

## Functions


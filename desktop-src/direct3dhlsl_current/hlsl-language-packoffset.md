# Pack Offset

Optional shader constant packing keyword, which uses the following syntax:

```
: packoffset( c[Subcomponent][.component] )
```

## Parameters

### packoffset

Required keyword

### c

Packing applies to constant registers (c) only.

### [Subcomponent][.component]

Optional subcomponents and components. A subcomponent is a register number, which is an integer. A component is in the form of [.xyzw].

## Remarks

Use this keyword to manually pack a shader constant when [`declaring a variable type`]().

When packing a constant, you cannot mix constant types.

The compiler behaves slightly differently for global constants and uniform constants:

<ul>
    <li>A global constant. A global variable is added as a global constant to a $Global cbuffer by the compiler. Automatically packed elements (those declared without packoffset) will appear after the last manually packed variable. You may mix types when packing global constants.</li>
    <li>A uniform constant. A uniform parameter in the parameter list of a function will be added to a $Param constant buffer by the compiler when the shader is compiled outside of the effects framework. When compiled inside the effect framework, a uniform constant must resolve to a uniform variable defined in global scope. A uniform constant cannot be manually offset; their recommend use is only for specialization of shaders where they alias back to globals, not as a means of passing application data into the shader.</li>
</ul>

## Examples

Pack subcomponents of vectors and scalars whose size is large enough to prevent crossing register boundaries. For example, these are all valid:

```
cbuffer MyBuffer
{
    float4 Element1 : packoffset(c0);
    float1 Element2 : packoffset(c1);
    float1 Element3 : packoffset(c1.y);
}
```
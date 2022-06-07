# Math and Logic Operations

### abs

Returns the absolute value of the specified value.



| ret abs(*x*) |
|--------------|



 

#### Parameters



| Item                                                   | Description                            |
|--------------------------------------------------------|----------------------------------------|
| <span id="x"></span><span id="X"></span>*x*<br/> | \[in\] The specified value.<br/> |



 

#### Return Value

The absolute value of the *x* parameter.

#### Type Description



| Name  | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                                                  | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md)                 | Size                           |
|-------|----------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------|--------------------------------|
| *x*   | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md), **vector**, or **matrix** | [**float**](/windows/desktop/WinProg/windows-data-types), [**int**](/windows/desktop/WinProg/windows-data-types) | any                            |
| *ret* | same as input *x*                                                                                              | same as input *x*                                                              | same dimension(s) as input *x* |


### acos

Returns the arccosine of the specified value.



| *ret* acos(*x*) |
|-----------------|



 

#### Parameters



| Item                                                   | Description                                                                                                         |
|--------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------|
| <span id="x"></span><span id="X"></span>*x*<br/> | \[in\] The specified value. Each component should be a floating-point value within the range of -1 to 1.<br/> |



 

#### Return Value

The arccosine of the *x* parameter.

#### Type Description



| Name  | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                                                  | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md) | Size                           |
|-------|----------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|--------------------------------|
| *x*   | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md), **vector**, or **matrix** | [**float**](/windows/desktop/WinProg/windows-data-types)                        | any                            |
| *ret* | same as input *x*                                                                                              | [**float**](/windows/desktop/WinProg/windows-data-types)                        | same dimension(s) as input *x* |

### all

Determines if all components of the specified value are non-zero.



| *ret* all(*x*) |
|----------------|



 

#### Parameters



| Item                                                   | Description                            |
|--------------------------------------------------------|----------------------------------------|
| <span id="x"></span><span id="X"></span>*x*<br/> | \[in\] The specified value.<br/> |



 

#### Return Value

**True** if all components of the *x* parameter are non-zero; otherwise, **false**.

#### Remarks

This function is similar to the [**any**](dx-graphics-hlsl-any.md) HLSL intrinsic function. The **any** function determines if any components of the specified value are non-zero, while the **all** function determines if all components of the specified value are non-zero.

#### Type Description



| Name  | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                                                  | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md)                                                         | Size |
|-------|----------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------|------|
| *x*   | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md), **vector**, or **matrix** | [**float**](/windows/desktop/WinProg/windows-data-types), [**int**](/windows/desktop/WinProg/windows-data-types), [**bool**](/windows/desktop/WinProg/windows-data-types) | any  |
| *ret* | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md)                            | [**bool**](/windows/desktop/WinProg/windows-data-types)                                                                                 | 1    |

### any

Determines if any components of the specified value are non-zero.



| *ret* any(*x*) |
|----------------|



 

#### Parameters



| Item                                                   | Description                            |
|--------------------------------------------------------|----------------------------------------|
| <span id="x"></span><span id="X"></span>*x*<br/> | \[in\] The specified value.<br/> |



 

#### Return Value

**True** if any components of the *x* parameter are non-zero; otherwise, **false**.

#### Remarks

This function is similar to the [**all**](dx-graphics-hlsl-all.md) HLSL intrinsic function. The **any** function determines if any components of the specified value are non-zero, while the **all** function determines if all components of the specified value are non-zero.

#### Type Description



| Name  | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                                                  | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md)                                                         | Size |
|-------|----------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------|------|
| *x*   | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md), **vector**, or **matrix** | [**float**](/windows/desktop/WinProg/windows-data-types), [**int**](/windows/desktop/WinProg/windows-data-types), [**bool**](/windows/desktop/WinProg/windows-data-types) | any  |
| *ret* | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md)                            | [**bool**](/windows/desktop/WinProg/windows-data-types)                                                                                 | 1    |

### asdouble function

Reinterprets a cast value (two 32-bit values) into a double.

#### Syntax

``` syntax
double asdouble(
  in uint lowbits,
  in uint highbits
);
```

#### Parameters

<dl> <dt>

*lowbits* \[in\]
</dt> <dd>

Type: **uint**

The low 32-bit pattern of the input value.

</dd> <dt>

*highbits* \[in\]
</dt> <dd>

Type: **uint**

The high 32-bit pattern of the input value.

</dd> </dl>

#### Return value

Type: **double**

The input (two 32-bit values) recast as a double.

#### Remarks

The following overloaded version is also available:

``` syntax
double2 asdouble(uint2 lowbits, uint2 highbits);
```

If the input value is two 32-bit components, the return type will contain one double. If the input value is four 32-bit components, the return type will contain two doubles. If the input value is a 64-bit type, the returned value will have the same number of components as the input value.

### asfloat

Interprets the bit pattern of *x* as a floating-point number.



| ret asfloat(*x*) |
|------------------|



 

#### Parameters



| Item                                                   | Description                        |
|--------------------------------------------------------|------------------------------------|
| <span id="x"></span><span id="X"></span>*x*<br/> | \[in\] The input value.<br/> |



 

#### Return Value

The input interpreted as a floating-point number.

#### Type Description



| Name  | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                                                  | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md)                                                         | Size                           |
|-------|----------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------|--------------------------------|
| *x*   | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md), **vector**, or **matrix** | [**float**](/windows/desktop/WinProg/windows-data-types), [**int**](/windows/desktop/WinProg/windows-data-types), [**uint**](/windows/desktop/WinProg/windows-data-types) | any                            |
| *ret* | same as input *x*                                                                                              | [**float**](/windows/desktop/WinProg/windows-data-types)                                                                                | same dimension(s) as input *x* |



 

#### Function Overloads

<dl> `float&lt;x&gt; asfloat(float&lt;x&gt; value);`  
`float&lt;x&gt; asfloat(int&lt;x&gt; value);`  
`float&lt;x&gt; asfloat(uint&lt;x&gt; value);`  
</dl>



 

#### Remarks

Older compilers incorrectly allowed `asfloat(bool)`, but note that bool inputs are not supported.

### asin

Returns the arcsine of the specified value.



| *ret* asin(*x*) |
|-----------------|



 

#### Parameters



| Item                                                   | Description                            |
|--------------------------------------------------------|----------------------------------------|
| <span id="x"></span><span id="X"></span>*x*<br/> | \[in\] The specified value.<br/> |



 

#### Return Value

The arcsine of the *x* parameter.

#### Remarks

Each component of the *x* parameter should be within the range of -π/2 to π/2.

#### Type Description



| Name  | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                                                  | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md) | Size                           |
|-------|----------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|--------------------------------|
| *x*   | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md), **vector**, or **matrix** | [**float**](/windows/desktop/WinProg/windows-data-types)                        | any                            |
| *ret* | same as input *x*                                                                                              | [**float**](/windows/desktop/WinProg/windows-data-types)                        | same dimension(s) as input *x* |

### asint

Interprets the bit pattern of *x* as an integer.



| ret asint(*x*) |
|----------------|



 

#### Parameters



| Item                                                   | Description                        |
|--------------------------------------------------------|------------------------------------|
| <span id="x"></span><span id="X"></span>*x*<br/> | \[in\] The input value.<br/> |



 

#### Return Value

The input interpreted as an integer.

#### Type Description



| Name  | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                                                  | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md)                  | Size                           |
|-------|----------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------|--------------------------------|
| *x*   | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md), **vector**, or **matrix** | [**float**](/windows/desktop/WinProg/windows-data-types), [**uint**](/windows/desktop/WinProg/windows-data-types) | any                            |
| *ret* | same as input *x*                                                                                              | [**int**](/windows/desktop/WinProg/windows-data-types)                                           | same dimension(s) as input *x* |

### asuint

Interprets the bit pattern of *x* as an unsigned integer.



| ret asuint(*x*) |
|-----------------|



 

#### Parameters



| Item                                                   | Description                        |
|--------------------------------------------------------|------------------------------------|
| <span id="x"></span><span id="X"></span>*x*<br/> | \[in\] The input value.<br/> |



 

#### Return Value

The input interpreted as an unsigned integer.

#### Type Description



| Name  | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                                                  | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md)                 | Size                           |
|-------|----------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------|--------------------------------|
| *x*   | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md), **vector**, or **matrix** | [**float**](/windows/desktop/WinProg/windows-data-types), [**int**](/windows/desktop/WinProg/windows-data-types) | any                            |
| *ret* | same as input *x*                                                                                              | [**uint**](/windows/desktop/WinProg/windows-data-types)                                         | same dimension(s) as input *x* |

### atan

Returns the arctangent of the specified value.



| *ret* atan(*x*) |
|-----------------|



 

#### Parameters



| Item                                                   | Description                            |
|--------------------------------------------------------|----------------------------------------|
| <span id="x"></span><span id="X"></span>*x*<br/> | \[in\] The specified value.<br/> |



 

#### Return Value

The arctangent of the *x* parameter. This value is within the range of -π/2 to π/2.

#### Type Description



| Name  | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                                                  | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md) | Size                           |
|-------|----------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|--------------------------------|
| *x*   | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md), **vector**, or **matrix** | [**float**](/windows/desktop/WinProg/windows-data-types)                        | any                            |
| *ret* | same as input *x*                                                                                              | [**float**](/windows/desktop/WinProg/windows-data-types)                        | same dimension(s) as input *x* |

### atan2

Returns the arctangent of two values (x,y).



| *ret* atan2(*y*, *x*) |
|-----------------------|



 

#### Parameters



| Item                                                   | Description                    |
|--------------------------------------------------------|--------------------------------|
| <span id="y"></span><span id="Y"></span>*y*<br/> | \[in\] The y value.<br/> |
| <span id="x"></span><span id="X"></span>*x*<br/> | \[in\] The x value.<br/> |



 

#### Return Value

The arctangent of (y,x).

#### Remarks

The signs of the *x* and *y* parameters are used to determine the quadrant of the return values within the range of -π to π. The **atan2** HLSL intrinsic function is well-defined for every point other than the origin, even if *y* equals 0 and *x* does not equal 0.

#### Type Description



| Name  | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                                                  | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md) | Size                           |
|-------|----------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|--------------------------------|
| *y*   | same as input *x*                                                                                              | [**float**](/windows/desktop/WinProg/windows-data-types)                        | same dimension(s) as input *x* |
| *x*   | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md), **vector**, or **matrix** | [**float**](/windows/desktop/WinProg/windows-data-types)                        | any                            |
| *ret* | same as input *x*                                                                                              | [**float**](/windows/desktop/WinProg/windows-data-types)                        | same dimension(s) as input *x* |

### ceil

Returns the smallest integer value that is greater than or equal to the specified value.



| *ret* ceil(*x*) |
|-----------------|



 

#### Parameters



| Item                                                   | Description                            |
|--------------------------------------------------------|----------------------------------------|
| <span id="x"></span><span id="X"></span>*x*<br/> | \[in\] The specified value.<br/> |



 

#### Return Value

The smallest integer value (returned as a floating-point type) that is greater than or equal to the *x* parameter.

#### Type Description



| Name  | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                                                  | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md) | Size                           |
|-------|----------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|--------------------------------|
| *x*   | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md), **vector**, or **matrix** | [**float**](/windows/desktop/WinProg/windows-data-types)                        | any                            |
| *ret* | same as input *x*                                                                                              | [**float**](/windows/desktop/WinProg/windows-data-types)                        | same dimension(s) as input *x* |

### clamp

Clamps the specified value to the specified minimum and maximum range.



| *ret* clamp(*x*, *min*, *max*) |
|--------------------------------|



 

#### Parameters



| Item                                                         | Description                                    |
|--------------------------------------------------------------|------------------------------------------------|
| <span id="x"></span><span id="X"></span>*x*<br/>       | \[in\] A value to clamp.<br/>            |
| <span id="min"></span><span id="MIN"></span>*min*<br/> | \[in\] The specified minimum range.<br/> |
| <span id="max"></span><span id="MAX"></span>*max*<br/> | \[in\] The specified maximum range.<br/> |



 

#### Return Value

The clamped value for the *x* parameter.

#### Remarks

For values of -INF or INF, clamp will behave as expected. However for values of NaN, the results are undefined.

#### Type Description



| Name  | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                                                  | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md)                 | Size                           |
|-------|----------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------|--------------------------------|
| *x*   | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md), **vector**, or **matrix** | [**float**](/windows/desktop/WinProg/windows-data-types), [**int**](/windows/desktop/WinProg/windows-data-types) | any                            |
| *min* | same as input *x*                                                                                              | [**float**](/windows/desktop/WinProg/windows-data-types), [**int**](/windows/desktop/WinProg/windows-data-types) | same dimension(s) as input *x* |
| *max* | same as input *x*                                                                                              | [**float**](/windows/desktop/WinProg/windows-data-types), [**int**](/windows/desktop/WinProg/windows-data-types) | same dimension(s) as input *x* |
| *ret* | same as input *x*                                                                                              | [**float**](/windows/desktop/WinProg/windows-data-types), [**int**](/windows/desktop/WinProg/windows-data-types) | same dimension(s) as input *x* |

### clip

Discards the current pixel if the specified value is less than zero.



| clip(*x*) |
|-----------|



 

#### Parameters



| Item                                                   | Description                            |
|--------------------------------------------------------|----------------------------------------|
| <span id="x"></span><span id="X"></span>*x*<br/> | \[in\] The specified value.<br/> |



 

#### Return Value

None.

#### Remarks

Use the **clip** HLSL intrinsic function to simulate clipping planes if each component of the *x* parameter represents the distance from a plane.

Also, use the **clip** function to test for alpha behavior, as shown in the following example:


```
clip( Input.Color.A < 0.1f ? -1:1 );
```



#### Type Description



| Name | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                                                  | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md) | Size |
|------|----------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|------|
| *x*  | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md), **vector**, or **matrix** | [**float**](/windows/desktop/WinProg/windows-data-types)                        | any  |

### cos

Returns the cosine of the specified value.



| *ret* cos(*x*) |
|----------------|



 

#### Parameters



| Item                                                   | Description                                        |
|--------------------------------------------------------|----------------------------------------------------|
| <span id="x"></span><span id="X"></span>*x*<br/> | \[in\] The specified value, in radians.<br/> |



 

#### Return Value

The cosine of the *x* parameter.

#### Type Description



| Name  | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                                                  | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md) | Size                           |
|-------|----------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|--------------------------------|
| *x*   | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md), **vector**, or **matrix** | [**float**](/windows/desktop/WinProg/windows-data-types)                        | any                            |
| *ret* | same as input *x*                                                                                              | [**float**](/windows/desktop/WinProg/windows-data-types)                        | same dimension(s) as input *x* |

### cosh

Returns the hyperbolic cosine of the specified value.



| *ret* cosh(*x*) |
|-----------------|



 

#### Parameters



| Item                                                   | Description                                        |
|--------------------------------------------------------|----------------------------------------------------|
| <span id="x"></span><span id="X"></span>*x*<br/> | \[in\] The specified value, in radians.<br/> |



 

#### Return Value

The hyperbolic cosine of the *x* parameter.

#### Type Description



| Name  | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                                                  | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md) | Size                           |
|-------|----------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|--------------------------------|
| *x*   | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md), **vector**, or **matrix** | [**float**](/windows/desktop/WinProg/windows-data-types)                        | any                            |
| *ret* | same as input *x*                                                                                              | [**float**](/windows/desktop/WinProg/windows-data-types)                        | same dimension(s) as input *x* |

### countbits function

Counts the number of bits (per component) set in the input integer.

#### Syntax

``` syntax
uint countbits(
  in uint value
);
```

#### Parameters

<dl> <dt>

*value* \[in\]
</dt> <dd>

Type: **uint**

The input value.

</dd> </dl>

#### Return value

Type: **uint**

The number of bits.

#### Remarks

The following overloaded versions are also available:

``` syntax
uint count_bits(uint value);
uint2 count_bits(uint2 value);
uint3 count_bits(uint3 value);
uint4 count_bits(uint4 value);
```

### cross

Returns the cross product of two floating-point, 3D vectors.



| *ret* cross(*x*, *y*) |
|-----------------------|



 

#### Parameters



| Item                                                   | Description                                             |
|--------------------------------------------------------|---------------------------------------------------------|
| <span id="x"></span><span id="X"></span>*x*<br/> | \[in\] The first floating-point, 3D vector.<br/>  |
| <span id="y"></span><span id="Y"></span>*y*<br/> | \[in\] The second floating-point, 3D vector.<br/> |



 

#### Return Value

The cross product of the *x* parameter and the *y* parameter.

#### Type Description



| Name  | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                       | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md) | Size |
|-------|-------------------------------------------------------------------------------------|----------------------------------------------------------------|------|
| *x*   | [**vector**](dx-graphics-hlsl-intrinsic-functions.md) | [**float**](/windows/desktop/WinProg/windows-data-types)                        | 3    |
| *y*   | [**vector**](dx-graphics-hlsl-intrinsic-functions.md) | [**float**](/windows/desktop/WinProg/windows-data-types)                        | 3    |
| *ret* | [**vector**](dx-graphics-hlsl-intrinsic-functions.md) | [**float**](/windows/desktop/WinProg/windows-data-types)                        | 3    |

## Derivative Operations

>**Note:** Enabled in Compute, Mesh and Amplification Shaders through [`Shader Model 6.6`](hlsl-appendix-shader-model_6_6.md).


### ddx

Returns the partial derivative of the specified value with respect to the screen-space x-coordinate.



| *ret* ddx(*x*) |
|----------------|



 

This function computes the partial derivative with respect to the screen-space x-coordinate. To compute the partial derivative with respect to the screen-space y-coordinate, use the [**ddy**](dx-graphics-hlsl-ddy.md) function.

This function is only supported in pixel shaders.

#### Parameters



| Item                                                   | Description                            |
|--------------------------------------------------------|----------------------------------------|
| <span id="x"></span><span id="X"></span>*x*<br/> | \[in\] The specified value.<br/> |



 

#### Return Value

The partial derivative of the *x* parameter.

#### Type Description



| Name  | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                                                  | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md) | Size                           |
|-------|----------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|--------------------------------|
| *x*   | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md), **vector**, or **matrix** | [**float**](/windows/desktop/WinProg/windows-data-types)                        | any                            |
| *ret* | same as input *x*                                                                                              | [**float**](/windows/desktop/WinProg/windows-data-types)                        | same dimension(s) as input *x* |

### ddx\_coarse function

Computes a low precision partial derivative with respect to the screen-space x-coordinate.

#### Syntax

``` syntax
float ddx_coarse(
  in float value
);
```

#### Parameters

<dl> <dt>

*value* \[in\]
</dt> <dd>

Type: **float**

The input value.

</dd> </dl>

#### Return value

Type: **float**

The low precision partial derivative of *value*.

#### Remarks

The following overloaded versions are also available:

``` syntax
float2 ddx_coarse(float2 value);
float3 ddx_coarse(float3 value);
float4 ddx_coarse(float4 value);
```

### ddx\_fine function

Computes a high precision partial derivative with respect to the screen-space x-coordinate.

#### Syntax

``` syntax
float ddx_fine(
  in float value
);
```

#### Parameters

<dl> <dt>

*value* \[in\]
</dt> <dd>

Type: **float**

The input value.

</dd> </dl>

#### Return value

Type: **float**

The high precision partial derivative of *value*.

#### Remarks

The following overloaded versions are also available:

``` syntax
float2 ddx_fine(float2 value);
float3 ddx_fine(float3 value);
float4 ddx_fine(float4 value);
```

### ddy

Returns the partial derivative of the specified value with respect to the screen-space y-coordinate.



| *ret* ddy(*x*) |
|----------------|



 

This function computes the partial derivative with respect to the screen-space y-coordinate. To compute the partial derivative with respect to the screen-space x-coordinate, use the [**ddx**](dx-graphics-hlsl-ddx.md) function.

This function is only supported in pixel shaders.

#### Parameters



| Item                                                   | Description                            |
|--------------------------------------------------------|----------------------------------------|
| <span id="x"></span><span id="X"></span>*x*<br/> | \[in\] The specified value.<br/> |



 

#### Return Value

The partial derivative of the *x* parameter.

#### Type Description



| Name  | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                                                  | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md) | Size                           |
|-------|----------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|--------------------------------|
| *x*   | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md), **vector**, or **matrix** | [**float**](/windows/desktop/WinProg/windows-data-types)                        | any                            |
| *ret* | same as input *x*                                                                                              | [**float**](/windows/desktop/WinProg/windows-data-types)                        | same dimension(s) as input *x* |

### ddy\_coarse function

Computes a low precision partial derivative with respect to the screen-space y-coordinate.

#### Syntax

``` syntax
float ddy_coarse(
  in float value
);
```

#### Parameters

<dl> <dt>

*value* \[in\]
</dt> <dd>

Type: **float**

The input value.

</dd> </dl>

#### Return value

Type: **float**

The low precision partial derivative of *value*.

#### Remarks

The following overloaded versions are also available:

``` syntax
float2 ddy_coarse(float2 value);
float3 ddy_coarse(float3 value);
float4 ddy_coarse(float4 value);
```

### ddy\_fine function

Computes a high precision partial derivative with respect to the screen-space x-coordinate.

#### Syntax

``` syntax
float ddy_fine(
  in float value
);
```

#### Parameters

<dl> <dt>

*value* \[in\]
</dt> <dd>

Type: **float**

The input value.

</dd> </dl>

#### Return value

Type: **float**

The high precision partial derivative of *value*.

#### Remarks

The following overloaded versions are also available:

``` syntax
float2 ddy_fine(float2 value);
float3 ddy_fine(float3 value);
float4 ddy_fine(float4 value);  
```

### degrees

Converts the specified value from radians to degrees.



| *ret* degrees(*x*) |
|--------------------|



 

#### Parameters



| Item                                                   | Description                            |
|--------------------------------------------------------|----------------------------------------|
| <span id="x"></span><span id="X"></span>*x*<br/> | \[in\] The specified value.<br/> |



 

#### Return Value

The result of converting the *x* parameter from radians to degrees.

#### Type Description



| Name  | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                                                  | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md) | Size                           |
|-------|----------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|--------------------------------|
| *x*   | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md), **vector**, or **matrix** | [**float**](/windows/desktop/WinProg/windows-data-types)                        | any                            |
| *ret* | same as input *x*                                                                                              | [**float**](/windows/desktop/WinProg/windows-data-types)                        | same dimension(s) as input *x* |

### determinant

Returns the determinant of the specified floating-point, square matrix.



| *ret* determinant(*m*) |
|------------------------|



 

#### Parameters



| Item                                                   | Description                            |
|--------------------------------------------------------|----------------------------------------|
| <span id="m"></span><span id="M"></span>*m*<br/> | \[in\] The specified value.<br/> |



 

#### Return Value

The floating-point, scalar value that represents the determinant of the *m* parameter.

#### Type Description



| Name  | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                       | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md) | Size                                     |
|-------|-------------------------------------------------------------------------------------|----------------------------------------------------------------|------------------------------------------|
| *m*   | [**matrix**](dx-graphics-hlsl-intrinsic-functions.md) | [**float**](/windows/desktop/WinProg/windows-data-types)                        | any (number of rows = number of columns) |
| *ret* | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md) | [**float**](/windows/desktop/WinProg/windows-data-types)                        | 1                                        |

### distance

Returns a distance scalar between two vectors.



| *ret* distance(*x*, *y*) |
|--------------------------|



 

#### Parameters



| Item                                                   | Description                                                    |
|--------------------------------------------------------|----------------------------------------------------------------|
| <span id="x"></span><span id="X"></span>*x*<br/> | \[in\] The first floating-point vector to compare.<br/>  |
| <span id="y"></span><span id="Y"></span>*y*<br/> | \[in\] The second floating-point vector to compare.<br/> |



 

#### Return Value

A floating-point, scalar value that represents the distance between the *x* parameter and the *y* parameter.

#### Type Description



| Name  | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                       | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md) | Size                           |
|-------|-------------------------------------------------------------------------------------|----------------------------------------------------------------|--------------------------------|
| *x*   | [**vector**](dx-graphics-hlsl-intrinsic-functions.md) | [**float**](/windows/desktop/WinProg/windows-data-types)                        | any                            |
| *y*   | [**vector**](dx-graphics-hlsl-intrinsic-functions.md) | [**float**](/windows/desktop/WinProg/windows-data-types)                        | same dimension(s) as input *x* |
| *ret* | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md) | [**float**](/windows/desktop/WinProg/windows-data-types)                        | 1                              |

### dot

Returns the dot product of two vectors.



| *ret* dot(*x*, *y*) |
|---------------------|



 

#### Parameters



| Item                                                   | Description                          |
|--------------------------------------------------------|--------------------------------------|
| <span id="x"></span><span id="X"></span>*x*<br/> | \[in\] The first vector.<br/>  |
| <span id="y"></span><span id="Y"></span>*y*<br/> | \[in\] The second vector.<br/> |



 

#### Return Value

The dot product of the *x* parameter and the *y* parameter.

#### Type Description



| Name  | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                       | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md)                 | Size                            |
|-------|-------------------------------------------------------------------------------------|--------------------------------------------------------------------------------|---------------------------------|
| *x*   | [**vector**](dx-graphics-hlsl-intrinsic-functions.md) | [**float**](/windows/desktop/WinProg/windows-data-types), [**int**](/windows/desktop/WinProg/windows-data-types) | any                             |
| *y*   | [**vector**](dx-graphics-hlsl-intrinsic-functions.md) | [**float**](/windows/desktop/WinProg/windows-data-types), [**int**](/windows/desktop/WinProg/windows-data-types) | same dimensions(s) as input *x* |
| *ret* | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md) | [**float**](/windows/desktop/WinProg/windows-data-types), [**int**](/windows/desktop/WinProg/windows-data-types) | 1                               |

### dst function

Calculates a distance vector.

#### Syntax

``` syntax
fVector dst(
  in fVector src0,
  in fVector src1
);
```

#### Parameters

<dl> <dt>

*src0* \[in\]
</dt> <dd>

Type: **[fVector](dx-graphics-hlsl-vector.md)**

The first vector.

</dd> <dt>

*src1* \[in\]
</dt> <dd>

Type: **[fVector](dx-graphics-hlsl-vector.md)**

The second vector.

</dd> </dl>

#### Return value

Type: **[fVector](dx-graphics-hlsl-vector.md)**

The computed distance vector.

#### Remarks

This intrinsic function provides the same functionality as the Vertex Shader instruction [dst](dst---vs.md).

### exp

Returns the base-e exponential, or e<sup>x</sup>, of the specified value.



| *ret* exp(*x*) |
|----------------|



 

#### Parameters



| Item                                                   | Description                            |
|--------------------------------------------------------|----------------------------------------|
| <span id="x"></span><span id="X"></span>*x*<br/> | \[in\] The specified value.<br/> |



 

#### Return Value

The base-e exponential of the *x* parameter.

#### Type Description



| Name  | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                                                  | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md) | Size                           |
|-------|----------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|--------------------------------|
| *x*   | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md), **vector**, or **matrix** | [**float**](/windows/desktop/WinProg/windows-data-types)                        | any                            |
| *ret* | same as input *x*                                                                                              | [**float**](/windows/desktop/WinProg/windows-data-types)                        | same dimension(s) as input *x* |

### exp2

Returns the base 2 exponential, or 2<sup>x</sup>, of the specified value.



| *ret* exp2(*x*) |
|-----------------|



 

#### Parameters



| Item                                                   | Description                                           |
|--------------------------------------------------------|-------------------------------------------------------|
| <span id="x"></span><span id="X"></span>*x*<br/> | \[in\] The specified floating-point value.<br/> |



 

#### Return Value

The base 2 exponential of the *x* parameter.

#### Type Description



| Name  | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                                                  | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md) | Size                           |
|-------|----------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|--------------------------------|
| *x*   | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md), **vector**, or **matrix** | [**float**](/windows/desktop/WinProg/windows-data-types)                        | any                            |
| *ret* | same as input *x*                                                                                              | [**float**](/windows/desktop/WinProg/windows-data-types)                        | same dimension(s) as input *x* |

### f16tof32 function

Converts the float16 stored in the low-half of the uint to a float.

#### Syntax

``` syntax
float f16tof32(
  in uint value
);
```

#### Parameters

<dl> <dt>

*value* \[in\]
</dt> <dd>

Type: **uint**

The input value.

</dd> </dl>

#### Return value

Type: **float**

The converted value.

#### Remarks

The following overloaded versions are also available:

``` syntax
float2 f16tof32(uint2 value);
float3 f16tof32(uint3 value);
float4 f16tof32(uint4 value);
```

### f32tof16 function

Converts an input into a float16 type.

#### Syntax

``` syntax
uint f32tof16(
  in float value
);
```

#### Parameters

<dl> <dt>

*value* \[in\]
</dt> <dd>

Type: **float**

The input value.

</dd> </dl>

#### Return value

Type: **uint**

The converted value, stored in the low-half of the uint.

#### Remarks

The following overloaded versions are also available:

``` syntax
uint2 f32tof16(float2 value);
uint3 f32tof16(float3 value);
uint4 f32tof16(float4 value);
```

### faceforward

Flips the surface-normal (if needed) to face in a direction opposite to i; returns the result in n.



| *ret* faceforward(*n*, *i*, *ng*) |
|-----------------------------------|



 

This function uses the following formula: -*n*  sign(dot(*i*, *ng*)).

#### Parameters



| Item                                                      | Description                                                                                                     |
|-----------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------|
| <span id="n"></span><span id="N"></span>*n*<br/>    | \[in\] The resulting floating-point surface-normal vector.<br/>                                           |
| <span id="i"></span><span id="I"></span>*i*<br/>    | \[in\] A floating-point, incident vector that points from the view position to the shading position.<br/> |
| <span id="ng"></span><span id="NG"></span>*ng*<br/> | \[in\] A floating-point surface-normal vector.<br/>                                                       |



 

#### Return Value

A floating-point, surface normal vector that is facing the view direction.

#### Type Description



| Name  | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                       | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md) | Size                           |
|-------|-------------------------------------------------------------------------------------|----------------------------------------------------------------|--------------------------------|
| *n*   | [**vector**](dx-graphics-hlsl-intrinsic-functions.md) | [**float**](/windows/desktop/WinProg/windows-data-types)                        | any                            |
| *i*   | [**vector**](dx-graphics-hlsl-intrinsic-functions.md) | [**float**](/windows/desktop/WinProg/windows-data-types)                        | same dimension(s) as input *n* |
| *ng*  | [**vector**](dx-graphics-hlsl-intrinsic-functions.md) | [**float**](/windows/desktop/WinProg/windows-data-types)                        | same dimensions as input *n*   |
| *ret* | [**vector**](dx-graphics-hlsl-intrinsic-functions.md) | [**float**](/windows/desktop/WinProg/windows-data-types)                        | same dimensions as input *n*   |

### firstbithigh function

Gets the location of the first set bit starting from the highest order bit and working downward, per component.

#### Syntax

``` syntax
int firstbithigh(
  in int value
);
```

#### Parameters

<dl> <dt>

*value* \[in\]
</dt> <dd>

Type: **[**int**](/windows/desktop/WinProg/windows-data-types)**

The input value.

</dd> </dl>

#### Return value

Type: **[**int**](/windows/desktop/WinProg/windows-data-types)**

The location of the first set bit.

#### Remarks

For a signed integer, the first significant bit is zero for a negative number.

The following overloaded versions are also available:

``` syntax
int2 firstbithigh(int2 value);
int3 firstbithigh(int3 value);
int4 firstbithigh(int4 value);
uint firstbithigh(uint value);
uint2 firstbithigh(uint2 value);
uint3 firstbithigh(uint3 value);
uint4 firstbithigh(uint4 value);
```

### firstbitlow function

Returns the location of the first set bit starting from the lowest order bit and working upward, per component.

#### Syntax

``` syntax
int firstbitlow(
  in int value
);
```

#### Parameters

<dl> <dt>

*value* \[in\]
</dt> <dd>

Type: **[**int**](/windows/desktop/WinProg/windows-data-types)**

The input value.

</dd> </dl>

#### Return value

Type: **[**int**](/windows/desktop/WinProg/windows-data-types)**

The location of the first set bit.

#### Remarks

The following overloaded versions are also available:

``` syntax
uint2 firstbitlow(uint2 value);
uint3 firstbitlow(uint3 value);
uint4 firstbitlow(uint4 value);
```

### floor

Returns the largest integer that is less than or equal to the specified value.



| *ret* floor(*x*) |
|------------------|



 

#### Parameters



| Item                                                   | Description                            |
|--------------------------------------------------------|----------------------------------------|
| <span id="x"></span><span id="X"></span>*x*<br/> | \[in\] The specified value.<br/> |



 

#### Return Value

The largest integer value (returned as a floating-point type) that is less than or equal to the *x* parameter.

#### Type Description



| Name  | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                                                  | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md) | Size                           |
|-------|----------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|--------------------------------|
| *x*   | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md), **vector**, or **matrix** | [**float**](/windows/desktop/WinProg/windows-data-types)                        | any                            |
| *ret* | same as input *x*                                                                                              | [**float**](/windows/desktop/WinProg/windows-data-types)                        | same dimension(s) as input *x* |

### fma

Returns the double-precision fused multiply-addition of a \* b + c.



| *ret* fma(double *a*, *b*, *c*); |
|----------------------------------|



 

#### Parameters

<dl> <dt>

<span id="a"></span><span id="A"></span>*a*
</dt> <dd>

\[in\] The first value in the fused multiply-addition.

</dd> <dt>

<span id="b"></span><span id="B"></span>*b*
</dt> <dd>

\[in\] The second value in the fused multiply-addition.

</dd> <dt>

<span id="c"></span><span id="C"></span>*c*
</dt> <dd>

\[in\] The third value in the fused multiply-addition.

</dd> </dl>

#### Return Value

The double-precision fused multiply-addition of parameters *a* \* *b* + *c*. The returned value must be accurate to 0.5 units of least precision (ULP).

#### Remarks

The **fma** intrinsic must support NaNs, INFs, and Denorms.

To use the **fma** intrinsic in your shader code, call the [**ID3D11Device::CheckFeatureSupport**](/windows/desktop/api/d3d11/nf-d3d11-id3d11device-checkfeaturesupport) method with [**D3D11\_FEATURE\_D3D11\_OPTIONS**](/windows/desktop/api/d3d11/ne-d3d11-d3d11_feature) to verify that the Direct3D device supports the [**ExtendedDoublesShaderInstructions**](/windows/desktop/api/d3d11/ns-d3d11-d3d11_feature_data_d3d11_options) feature option. The **fma** intrinsic requires a WDDM 1.2 display driver, and all WDDM 1.2 display drivers must support **fma**. If your app creates a rendering device with [feature level](/windows/desktop/direct3d11/overviews-direct3d-11-devices-downlevel-intro) 11.0 or 11.1 and the compilation target is shader model 5 or later, the HLSL source code can use the **fma** intrinsic.

#### Type Description



| Name  | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                                                  | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md) | Size                         |
|-------|----------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|------------------------------|
| *a*   | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md), **vector**, or **matrix** | [**double**](/windows/desktop/WinProg/windows-data-types)                       | any                          |
| *b*   | same as input *a*                                                                                              | [**double**](/windows/desktop/WinProg/windows-data-types)                       | same dimensions as input *a* |
| *c*   | same as input *a*                                                                                              | [**double**](/windows/desktop/WinProg/windows-data-types)                       | same dimensions as input *a* |
| *ret* | same as input *a*                                                                                              | [**double**](/windows/desktop/WinProg/windows-data-types)                       | same dimensions as input *a* |

### fmod

Returns the floating-point remainder of x/y.



| *ret* fmod(*x*, *y*) |
|----------------------|



 

#### Parameters



| Item                                                   | Description                                    |
|--------------------------------------------------------|------------------------------------------------|
| <span id="x"></span><span id="X"></span>*x*<br/> | \[in\] The floating-point dividend.<br/> |
| <span id="y"></span><span id="Y"></span>*y*<br/> | \[in\] The floating-point divisor.<br/>  |



 

#### Return Value

The floating-point remainder of the *x* parameter divided by the *y* parameter.

#### Remarks

The floating-point remainder is calculated such that x = i \* y + f, where i is an integer, f has the same sign as x, and the absolute value of f is less than the absolute value of y.

#### Type Description



| Name  | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                                                  | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md) | Size                           |
|-------|----------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|--------------------------------|
| *x*   | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md), **vector**, or **matrix** | [**float**](/windows/desktop/WinProg/windows-data-types)                        | any                            |
| *y*   | same as input *x*                                                                                              | [**float**](/windows/desktop/WinProg/windows-data-types)                        | same dimension(s) as input *x* |
| *ret* | same as input *x*                                                                                              | [**float**](/windows/desktop/WinProg/windows-data-types)                        | same dimension(s) as input *x* |

### frac

Returns the fractional (or decimal) part of x; which is greater than or equal to 0 and less than 1.

Also see [trunc](./dx-graphics-hlsl-trunc.md).

| *ret* frac(*x*) |
|-----------------|



 

#### Parameters



| Item                                                   | Description                            |
|--------------------------------------------------------|----------------------------------------|
| <span id="x"></span><span id="X"></span>*x*<br/> | \[in\] The specified value.<br/> |



 

#### Return Value

The fractional part of the *x* parameter.

#### Type Description



| Name  | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                                                  | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md) | Size                           |
|-------|----------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|--------------------------------|
| *x*   | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md), **vector**, or **matrix** | [**float**](/windows/desktop/WinProg/windows-data-types)                        | any                            |
| *ret* | same as input *x*                                                                                              | [**float**](/windows/desktop/WinProg/windows-data-types)                        | same dimension(s) as input *x* |

### frexp

Returns the mantissa and exponent of the specified floating-point value.



| *ret* frexp(*x*, *exp*) |
|-------------------------|



 

The return value is the mantissa, and the value returned by *exp* parameter is the exponent.

#### Parameters



| Item                                                         | Description                                                                                                                                      |
|--------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|
| <span id="x"></span><span id="X"></span>*x*<br/>       | \[in\] The specified floating-point value. If the *x* parameter is 0, this function returns 0 for both the mantissa and the exponent.<br/> |
| <span id="exp"></span><span id="EXP"></span>*exp*<br/> | \[out\] The returned exponent of the *x* parameter.<br/>                                                                                   |



 

#### Return Value

The mantissa of the *x* parameter.

#### Type Description



| Name  | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                                                  | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md) | Size                           |
|-------|----------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|--------------------------------|
| *x*   | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md), **vector**, or **matrix** | [**float**](/windows/desktop/WinProg/windows-data-types)                        | any                            |
| *exp* | same as input *x*                                                                                              | [**float**](/windows/desktop/WinProg/windows-data-types)                        | same dimension(s) as input *x* |
| *ret* | same as input *x*                                                                                              | [**float**](/windows/desktop/WinProg/windows-data-types)                        | same dimension(s) as input *x* |

### fwidth

Returns the absolute value of the partial derivatives of the specified value.



| *ret* fwidth(*x*) |
|-------------------|



 

This function computes the following: [**abs**](dx-graphics-hlsl-abs.md)([**ddx**](dx-graphics-hlsl-ddx.md)(*x*)) + [**abs**](dx-graphics-hlsl-abs.md)([**ddy**](dx-graphics-hlsl-ddy.md)(*x*)).

This function is only supported in pixel shaders.

#### Parameters



| Item                                                   | Description                            |
|--------------------------------------------------------|----------------------------------------|
| <span id="x"></span><span id="X"></span>*x*<br/> | \[in\] The specified value.<br/> |



 

#### Return Value

The absolute value of the partial derivatives of the *x* parameter.

#### Type Description



| Name  | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                                                  | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md) | Size                           |
|-------|----------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|--------------------------------|
| *x*   | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md), **vector**, or **matrix** | [**float**](/windows/desktop/WinProg/windows-data-types)                        | any                            |
| *ret* | same as input *x*                                                                                              | [**float**](/windows/desktop/WinProg/windows-data-types)                        | same dimension(s) as input *x* |

### isfinite

Determines if the specified floating-point value is finite.



| *ret* isfinite(*x*) |
|---------------------|



 

#### Parameters



| Item                                                   | Description                            |
|--------------------------------------------------------|----------------------------------------|
| <span id="x"></span><span id="X"></span>*x*<br/> | \[in\] The specified value.<br/> |



 

#### Return Value

Returns a value of the same size as the input, with a value set to **True** if the *x* parameter is finite; otherwise **False**.

#### Type Description



| Name  | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                                                  | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md) | Size     |
|-------|----------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|----------|
| *x*   | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md), **vector**, or **matrix** | [**float**](/windows/desktop/WinProg/windows-data-types)                        | any      |
| *ret* | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md), **vector**, or **matrix** | [**bool**](/windows/desktop/WinProg/windows-data-types)                         | as input |

### isinf

Determines if the specified value is infinite.



| *ret* isinf(*x*) |
|------------------|



 

#### Parameters



| Item                                                   | Description                            |
|--------------------------------------------------------|----------------------------------------|
| <span id="x"></span><span id="X"></span>*x*<br/> | \[in\] The specified value.<br/> |



 

#### Return Value

Returns a value of the same size as the input, with a value set to **True** if the *x* parameter is +INF or -INF. Otherwise, **False**.

#### Type Description



| Name  | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                                                  | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md) | Size     |
|-------|----------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|----------|
| *x*   | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md), **vector**, or **matrix** | [**float**](/windows/desktop/WinProg/windows-data-types)                        | any      |
| *ret* | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md), **vector**, or **matrix** | [**bool**](/windows/desktop/WinProg/windows-data-types)                         | as input |

### isnan

Determines if the specified value is NAN or QNAN.



| *ret* isnan(*x*) |
|------------------|



 

#### Parameters



| Item                                                   | Description                            |
|--------------------------------------------------------|----------------------------------------|
| <span id="x"></span><span id="X"></span>*x*<br/> | \[in\] The specified value.<br/> |



 

#### Return Value

Returns a value of the same size as the input, with a value set to **True** if the *x* parameter is NAN or QNAN. Otherwise, **False**.

#### Type Description



| Name  | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                                                  | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md) | Size     |
|-------|----------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|----------|
| *x*   | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md), **vector**, or **matrix** | [**float**](/windows/desktop/WinProg/windows-data-types)                        | any      |
| *ret* | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md), **vector**, or **matrix** | [**bool**](/windows/desktop/WinProg/windows-data-types)                         | as input |

### ldexp

Returns the result of multiplying the specified value by two, raised to the power of the specified exponent.



| *ret* ldexp(*x*, *exp*) |
|-------------------------|



 

This function uses the following formula: *x* \* 2<sup>exp</sup>

#### Parameters



| Item                                                         | Description                               |
|--------------------------------------------------------------|-------------------------------------------|
| <span id="x"></span><span id="X"></span>*x*<br/>       | \[in\] The specified value.<br/>    |
| <span id="exp"></span><span id="EXP"></span>*exp*<br/> | \[in\] The specified exponent.<br/> |



 

#### Return Value

The result of multiplying the *x* parameter by two, raised to the power of the *exp* parameter.

#### Type Description



| Name  | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                                                  | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md) | Size                           |
|-------|----------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|--------------------------------|
| *x*   | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md), **vector**, or **matrix** | [**float**](/windows/desktop/WinProg/windows-data-types)                        | any                            |
| *exp* | same as input *x*                                                                                              | [**float**](/windows/desktop/WinProg/windows-data-types)                        | same dimension(s) as input *x* |
| *ret* | same as input *x*                                                                                              | [**float**](/windows/desktop/WinProg/windows-data-types)                        | same dimension(s) as input *x* |

### length

Returns the length of the specified floating-point vector.



| *ret* length(*x*) |
|-------------------|



 

#### Parameters



| Item                                                   | Description                                     |
|--------------------------------------------------------|-------------------------------------------------|
| <span id="x"></span><span id="X"></span>*x*<br/> | The specified floating-point vector.<br/> |



 

#### Return Value

A floating-point scalar that represents the length of the *x* parameter.

#### Type Description



| Name  | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                       | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md) | Size |
|-------|-------------------------------------------------------------------------------------|----------------------------------------------------------------|------|
| *x*   | [**vector**](dx-graphics-hlsl-intrinsic-functions.md) | [**float**](/windows/desktop/WinProg/windows-data-types)                        | any  |
| *ret* | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md) | [**float**](/windows/desktop/WinProg/windows-data-types)                        | 1    |

### lerp

Performs a linear interpolation.



| *ret* lerp(*x*, *y*, *s*) |
|---------------------------|



 

#### Parameters



| Item                                                   | Description                                                                                           |
|--------------------------------------------------------|-------------------------------------------------------------------------------------------------------|
| <span id="x"></span><span id="X"></span>*x*<br/> | \[in\] The first-floating point value.<br/>                                                     |
| <span id="y"></span><span id="Y"></span>*y*<br/> | \[in\] The second-floating point value.<br/>                                                    |
| <span id="s"></span><span id="S"></span>*s*<br/> | \[in\] A value that linearly interpolates between the *x* parameter and the *y* parameter.<br/> |



 

#### Return Value

The result of the linear interpolation.

#### Type Description



| Name  | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                                                  | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md) | Size                           |
|-------|----------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|--------------------------------|
| *x*   | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md), **vector**, or **matrix** | [**float**](/windows/desktop/WinProg/windows-data-types)                        | any                            |
| *y*   | same as input *x*                                                                                              | [**float**](/windows/desktop/WinProg/windows-data-types)                        | same dimension(s) as input *x* |
| *s*   | same as input *x*                                                                                              | [**float**](/windows/desktop/WinProg/windows-data-types)                        | same dimension(s) as input *x* |
| *ret* | same as input *x*                                                                                              | [**float**](/windows/desktop/WinProg/windows-data-types)                        | same dimension(s) as input *x* |



 

#### Remarks

Linear interpolation is based on the following formula: x\*(1-s) + y\*s which can equivalently be written as x + s(y-x).

### lit

Returns a lighting coefficient vector.



| *ret* lit(*n\_dot\_l*, *n\_dot\_h*, *m*) |
|------------------------------------------|



 

This function returns a lighting coefficient vector (ambient, diffuse, specular, 1) where:

-   ambient = 1
-   diffuse = n · l < 0 ? 0 : n · l
-   specular = n · l < 0 \|\| n · h < 0 ? 0 : (n · h) ^ m

Where the vector n is the normal vector, l is the direction to light and h is the half vector.

#### Parameters



| Item                                                                       | Description                                                                              |
|----------------------------------------------------------------------------|------------------------------------------------------------------------------------------|
| <span id="n_dot_l"></span><span id="N_DOT_L"></span>*n\_dot\_l*<br/> | \[in\] The dot product of the normalized surface normal and the light vector.<br/> |
| <span id="n_dot_h"></span><span id="N_DOT_H"></span>*n\_dot\_h*<br/> | \[in\] The dot product of the half-angle vector and the surface normal.<br/>       |
| <span id="m"></span><span id="M"></span>*m*<br/>                     | \[in\] A specular exponent.<br/>                                                   |



 

#### Return Value

The lighting coefficient vector.

#### Type Description



| Name        | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                       | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md) | Size |
|-------------|-------------------------------------------------------------------------------------|----------------------------------------------------------------|------|
| *n\_dot\_l* | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md) | [**float**](/windows/desktop/WinProg/windows-data-types)                        | 1    |
| *n\_dot\_h* | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md) | [**float**](/windows/desktop/WinProg/windows-data-types)                        | 1    |
| *m*         | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md) | [**float**](/windows/desktop/WinProg/windows-data-types)                        | 1    |
| *ret*       | [**vector**](dx-graphics-hlsl-intrinsic-functions.md) | [**float**](/windows/desktop/WinProg/windows-data-types)                        | 4    |

### log

Returns the base-e logarithm of the specified value.



| *ret* log(*x*) |
|----------------|



 

#### Parameters



| Item                                                   | Description                            |
|--------------------------------------------------------|----------------------------------------|
| <span id="x"></span><span id="X"></span>*x*<br/> | \[in\] The specified value.<br/> |



 

#### Return Value

The base-e logarithm of the *x* parameter. If the *x* parameter is negative, this function returns indefinite. If the *x* parameter is 0, this function returns -INF.

#### Type Description



| Name  | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                                                  | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md) | Size                           |
|-------|----------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|--------------------------------|
| *x*   | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md), **vector**, or **matrix** | [**float**](/windows/desktop/WinProg/windows-data-types)                        | any                            |
| *ret* | same as input *x*                                                                                              | [**float**](/windows/desktop/WinProg/windows-data-types)                        | same dimension(s) as input *x* |

### log10

Returns the base-10 logarithm of the specified value.



| *ret* log10(*x*) |
|------------------|



 

#### Parameters



| Item                                                   | Description                            |
|--------------------------------------------------------|----------------------------------------|
| <span id="x"></span><span id="X"></span>*x*<br/> | \[in\] The specified value.<br/> |



 

#### Return Value

The base-10 logarithm of the *x* parameter. If the *x* parameter is negative, this function returns indefinite. If the *x* is 0, this function returns -INF.

#### Type Description



| Name  | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                                                  | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md) | Size                           |
|-------|----------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|--------------------------------|
| *x*   | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md), **vector**, or **matrix** | [**float**](/windows/desktop/WinProg/windows-data-types)                        | any                            |
| *ret* | same as input *x*                                                                                              | [**float**](/windows/desktop/WinProg/windows-data-types)                        | same dimension(s) as input *x* |

### log2

Returns the base-2 logarithm of the specified value.



| *ret* log2(*x*) |
|-----------------|



 

#### Parameters



| Item                                                   | Description                            |
|--------------------------------------------------------|----------------------------------------|
| <span id="x"></span><span id="X"></span>*x*<br/> | \[in\] The specified value.<br/> |



 

#### Return Value

The base-2 logarithm of the *x* parameter. If the *x* parameter is negative, this function returns indefinite. If the *x* parameter is 0, this function returns +INF.

#### Type Description



| Name  | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                                                  | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md) | Size                           |
|-------|----------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|--------------------------------|
| *x*   | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md), **vector**, or **matrix** | [**float**](/windows/desktop/WinProg/windows-data-types)                        | any                            |
| *ret* | same as input *x*                                                                                              | [**float**](/windows/desktop/WinProg/windows-data-types)                        | same dimension(s) as input *x* |

### mad function

Performs an arithmetic multiply/add operation on three values.

#### Syntax

``` syntax
numeric mad(
  in numeric mvalue,
  in numeric avalue,
  in numeric bvalue
);
```

#### Parameters

<dl> <dt>

*mvalue* \[in\]
</dt> <dd>

Type: **numeric**

The multiplication value.

</dd> <dt>

*avalue* \[in\]
</dt> <dd>

Type: **numeric**

The first addition value.

</dd> <dt>

*bvalue* \[in\]
</dt> <dd>

Type: **numeric**

The second addition value.

</dd> </dl>

#### Return value

Type: **numeric**

The result of *mvalue* \* *avalue* + *bvalue*.

### max

Selects the greater of x and y.



| ret max(x, y) |
|---------------|



 

#### Parameters



| Item                                                   | Description                          |
|--------------------------------------------------------|--------------------------------------|
| <span id="x"></span><span id="X"></span>*x*<br/> | \[in\] The x input value.<br/> |
| <span id="y"></span><span id="Y"></span>*y*<br/> | \[in\] The y input value.<br/> |



 

#### Return Value

The *x* or *y* parameter, whichever is the largest value.


#### Remarks

Denormals are handled as follows:

| src0 src1-> | -inf | F             | +inf | NAN  |
|-------------|------|---------------|------|------|
| -inf        | -inf | src1          | +inf | -inf |
| F           | src0 | src0 or src1  | +inf | src0 |
| +inf        | +inf | +inf          | +inf | +inf |
| NaN         | -inf | src1          | +inf | NaN  |

F means finite-real number.


#### Type Description

| Name | In/Out      | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                                                  | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md)                 | Size                         |
|------|-------------|----------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------|------------------------------|
| x    | in          | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md), **vector**, or **matrix** | [**float**](/windows/desktop/WinProg/windows-data-types), [**int**](/windows/desktop/WinProg/windows-data-types) | any                          |
| y    | in          | same as input x                                                                                                | [**float**](/windows/desktop/WinProg/windows-data-types), [**int**](/windows/desktop/WinProg/windows-data-types) | same dimension(s) as input x |
| ret  | return type | same as input x                                                                                                | [**float**](/windows/desktop/WinProg/windows-data-types), [**int**](/windows/desktop/WinProg/windows-data-types) | same dimension(s) as input x |

### min

Selects the lesser of x and y.



| ret min(x, y) |
|---------------|



 

#### Parameters



| Item                                                   | Description                          |
|--------------------------------------------------------|--------------------------------------|
| <span id="x"></span><span id="X"></span>*x*<br/> | \[in\] The x input value.<br/> |
| <span id="y"></span><span id="Y"></span>*y*<br/> | \[in\] The y input value.<br/> |



 

#### Return Value

The *x* or *y* parameter, whichever is the smallest value.


#### Remarks

Denormals are handled as follows:

| src0 src1-> | -inf | F             | +inf | NAN  |
|-------------|------|---------------|------|------|
| -inf        | -inf | -inf          | -inf | -inf |
| F           | -inf | src0 or src1  | src0 | src0 |
| +inf        | -inf | src1          | +inf | +inf |
| NaN         | -inf | src1          | +inf | NaN  |

F means finite-real number.


#### Type Description

| Name | In/Out      | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                                                  | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md)                 | Size                         |
|------|-------------|----------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------|------------------------------|
| x    | in          | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md), **vector**, or **matrix** | [**float**](/windows/desktop/WinProg/windows-data-types), [**int**](/windows/desktop/WinProg/windows-data-types) | any                          |
| y    | in          | same as input x                                                                                                | [**float**](/windows/desktop/WinProg/windows-data-types), [**int**](/windows/desktop/WinProg/windows-data-types) | same dimension(s) as input x |
| ret  | return type | same as input x                                                                                                | [**float**](/windows/desktop/WinProg/windows-data-types), [**int**](/windows/desktop/WinProg/windows-data-types) | same dimension(s) as input x |

### modf

Splits the value x into fractional and integer parts, each of which has the same sign as x.



| ret modf(x, out ip) |
|---------------------|



 

#### Parameters



| Item                                                      | Description                                    |
|-----------------------------------------------------------|------------------------------------------------|
| <span id="x"></span><span id="X"></span>*x*<br/>    | \[in\] The x input value.<br/>           |
| <span id="ip"></span><span id="IP"></span>*ip*<br/> | \[out\] The integer portion of *x*.<br/> |



 

#### Return Value

The signed-fractional portion of x.

#### Type Description



| Name | In/Out | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                                                  | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md)                 | Size                         |
|------|--------|----------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------|------------------------------|
| x    | in     | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md), **vector**, or **matrix** | [**float**](/windows/desktop/WinProg/windows-data-types), [**int**](/windows/desktop/WinProg/windows-data-types) | any                          |
| ip   | out    | same as input x                                                                                                | [**float**](/windows/desktop/WinProg/windows-data-types), [**int**](/windows/desktop/WinProg/windows-data-types) | same dimension(s) as input x |
| ret  | out    | same as input x                                                                                                | [**float**](/windows/desktop/WinProg/windows-data-types), [**int**](/windows/desktop/WinProg/windows-data-types) | same dimension(s) as input x |

### msad4

Compares a 4-byte reference value and an 8-byte source value and accumulates a vector of 4 sums. Each sum corresponds to the masked sum of absolute differences of a different byte alignment between the reference value and the source value.



| uint4 result = msad4(uint reference, uint2 source, uint4 accum); |
|------------------------------------------------------------------|



 

#### Parameters

<dl> <dt>

<span id="reference"></span><span id="REFERENCE"></span>*reference*
</dt> <dd>

\[in\] The reference array of 4 bytes in one **uint** value.

</dd> <dt>

<span id="source"></span><span id="SOURCE"></span>*source*
</dt> <dd>

\[in\] The source array of 8 bytes in two **uint2** values.

</dd> <dt>

<span id="accum"></span><span id="ACCUM"></span>*accum*
</dt> <dd>

\[in\] A vector of 4 values. **msad4** adds this vector to the masked sum of absolute differences of the different byte alignments between the reference value and the source value.

</dd> </dl>

#### Return Value

A vector of 4 sums. Each sum corresponds to the masked sum of absolute differences of different byte alignments between the reference value and the source value. **msad4** doesn't include a difference in the sum if that difference is masked (that is, the reference byte is 0).

#### Remarks

To use the **msad4** intrinsic in your shader code, call the [**ID3D11Device::CheckFeatureSupport**](/windows/desktop/api/d3d11/nf-d3d11-id3d11device-checkfeaturesupport) method with [**D3D11\_FEATURE\_D3D11\_OPTIONS**](/windows/desktop/api/d3d11/ne-d3d11-d3d11_feature) to verify that the Direct3D device supports the [**SAD4ShaderInstructions**](/windows/desktop/api/d3d11/ns-d3d11-d3d11_feature_data_d3d11_options) feature option. The **msad4** intrinsic requires a WDDM 1.2 display driver, and all WDDM 1.2 display drivers must support **msad4**. If your app creates a rendering device with [feature level](/windows/desktop/direct3d11/overviews-direct3d-11-devices-downlevel-intro) 11.0 or 11.1 and the compilation target is shader model 5 or later, the HLSL source code can use the **msad4** intrinsic.

Return values are only accurate up to 65535. If you call the **msad4** intrinsic with inputs that might result in return values greater than 65535, **msad4** produces undefined results.

### mul

Multiplies x and y using matrix math. The inner dimension x-columns and y-rows must be equal.



| ret mul(x, y) |
|---------------|



 

#### Parameters



| Item                                                   | Description                                                                           |
|--------------------------------------------------------|---------------------------------------------------------------------------------------|
| <span id="x"></span><span id="X"></span>*x*<br/> | \[in\] The x input value. If x is a vector, it treated as a row vector.<br/>    |
| <span id="y"></span><span id="Y"></span>*y*<br/> | \[in\] The y input value. If y is a vector, it treated as a column vector.<br/> |



 

#### Return Value

The result of x times y. The result has the dimension x-rows x y-columns.

#### Type Description

There are 9 overloaded versions of this function; the overloaded versions handle the different cases for the types and sizes of the input arguments.



| Version | Name | Purpose | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md) | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md) | Size                                                                     |
|---------|------|---------|---------------------------------------------------------------|----------------------------------------------------------------|--------------------------------------------------------------------------|
| 1       |      |         |                                                               |                                                                |                                                                          |
|         | x    | in      | scalar                                                        | float, int                                                     | 1                                                                        |
|         | y    | in      | scalar                                                        | same as input x                                                | 1                                                                        |
|         | ret  | out     | scalar                                                        | same as input x                                                | 1                                                                        |
| 2       |      |         |                                                               |                                                                |                                                                          |
|         | x    | in      | scalar                                                        | float, int                                                     | 1                                                                        |
|         | y    | in      | vector                                                        | float, int                                                     | any                                                                      |
|         | ret  | out     | vector                                                        | float, int                                                     | same dimension(s) as input y                                             |
| 3       |      |         |                                                               |                                                                |                                                                          |
|         | x    | in      | scalar                                                        | float, int                                                     | 1                                                                        |
|         | y    | in      | matrix                                                        | float, int                                                     | any                                                                      |
|         | ret  | out     | matrix                                                        | same as input y                                                | same dimension(s) as input y                                             |
| 4       |      |         |                                                               |                                                                |                                                                          |
|         | x    | in      | vector                                                        | float, int                                                     | any                                                                      |
|         | y    | in      | scalar                                                        | float, int                                                     | 1                                                                        |
|         | ret  | out     | vector                                                        | float, int                                                     | same dimension(s) as input x                                             |
| 5       |      |         |                                                               |                                                                |                                                                          |
|         | x    | in      | vector                                                        | float, int                                                     | any                                                                      |
|         | y    | in      | vector                                                        | float, int                                                     | same dimension(s) as input x                                             |
|         | ret  | out     | scalar                                                        | float, int                                                     | 1                                                                        |
| 6       |      |         |                                                               |                                                                |                                                                          |
|         | x    | in      | vector                                                        | float, int                                                     | any                                                                      |
|         | y    | in      | matrix                                                        | float, int                                                     | rows = same dimension(s) as input x, columns = any                       |
|         | ret  | out     | vector                                                        | float, int                                                     | same dimension(s) as input y columns                                     |
| 7       |      |         |                                                               |                                                                |                                                                          |
|         | x    | in      | matrix                                                        | float, int                                                     | any                                                                      |
|         | y    | in      | scalar                                                        | float, int                                                     | 1                                                                        |
|         | ret  | out     | matrix                                                        | float, int                                                     | same dimension(s) as input x                                             |
| 8       |      |         |                                                               |                                                                |                                                                          |
|         | x    | in      | matrix                                                        | float, int                                                     | any                                                                      |
|         | y    | in      | vector                                                        | float, int                                                     | number of columns in input x                                             |
|         | ret  | out     | vector                                                        | float, int                                                     | number of rows in input x                                                |
| 9       |      |         |                                                               |                                                                |                                                                          |
|         | x    | in      | matrix                                                        | float, int                                                     | any                                                                      |
|         | y    | in      | matrix                                                        | float, int                                                     | rows = number of columns in input x                                      |
|         | ret  | out     | matrix                                                        | float, int                                                     | rows = number of rows in input x, columns = number of columns in input y |

### normalize

Normalizes the specified floating-point vector according to x / length(x).



| *ret* normalize(*x*) |
|----------------------|



 

#### Parameters



| Item                                                   | Description                                            |
|--------------------------------------------------------|--------------------------------------------------------|
| <span id="x"></span><span id="X"></span>*x*<br/> | \[in\] The specified floating-point vector.<br/> |



 

#### Return Value

The normalized *x* parameter. If the length of the *x* parameter is 0, the result is indefinite.

#### Remarks

The **normalize** HLSL intrinsic function uses the following formula: *x* / [**length**](dx-graphics-hlsl-length.md)(*x*).

#### Type Description



| Name  | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                       | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md) | Size                           |
|-------|-------------------------------------------------------------------------------------|----------------------------------------------------------------|--------------------------------|
| *x*   | [**vector**](dx-graphics-hlsl-intrinsic-functions.md) | [**float**](/windows/desktop/WinProg/windows-data-types)                        | any                            |
| *ret* | same as input *x*                                                                   | [**float**](/windows/desktop/WinProg/windows-data-types)                        | same dimension(s) as input *x* |

### pow

Returns the specified value raised to the specified power.



| *ret* pow(*x*, *y*) |
|---------------------|


By default, DXC always uses *log-mul-exp pattern* (explained as follows) to implement the **pow** function. In contrast, FXC also uses the *mul-only* pattern instead to implement the **pow** function in some scenarios. For example, for smaller constant values of *y* (such as *pow(x, 3)*), FXC uses the *mul-only* pattern. This could lead to the **pow** function producing different results when compiled by using FXC and DXC in some cases. For example, for a runtime value of *x=0*, *pow(x,3)* evaluates to *NaN* and *0* on DXC and FXC, respectively. To achieve the FXC behavior with respect to the **pow** function on DXC, set the language version to 2016 (by using the flag `-HV 2016`) during compilation.

#### Example of pow implementation by using the log-mul-exp pattern

```C++
pow(x,y) = e^(log(x) * y)
```

#### Example of pow implementation by using the mul-only pattern

```C++
pow(x,3) = (x * x) * x 
```
 

#### Parameters



| Item                                                   | Description                            |
|--------------------------------------------------------|----------------------------------------|
| <span id="x"></span><span id="X"></span>*x*<br/> | \[in\] The specified value.<br/> |
| <span id="y"></span><span id="Y"></span>*y*<br/> | \[in\] The specified power.<br/> |



 

#### Return Value

The *x* parameter raised to the power of the *y* parameter.

#### Remarks

The **pow** HLSL intrinsic function calculates *x*<sup>y</sup>.



| X      | Y      | Result                                                                      |
|--------|--------|-----------------------------------------------------------------------------|
| < 0 | any    | NAN                                                                         |
| > 0 | == 0   | 1                                                                           |
| == 0   | > 0 | 0                                                                           |
| == 0   | < 0 | inf                                                                         |
| > 0 | < 0 | 1/X<sup>-Y</sup>                                                            |
| == 0   | == 0   | Depends on the particular graphics processor<br/> 0, or 1, or NAN<br/> |



 

#### Type Description



| Name  | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                                                  | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md) | Size                           |
|-------|----------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|--------------------------------|
| *x*   | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md), **vector**, or **matrix** | [**float**](/windows/desktop/WinProg/windows-data-types)                        | any                            |
| *y*   | same as input *x*                                                                                              | [**float**](/windows/desktop/WinProg/windows-data-types)                        | same dimension(s) as input *x* |
| *ret* | same as input *x*                                                                                              | [**float**](/windows/desktop/WinProg/windows-data-types)                        | same dimension(s) as input *x* |

### radians

Converts the specified value from degrees to radians.



| *ret* radians(*x*) |
|--------------------|



 

#### Parameters



| Item                                                   | Description                            |
|--------------------------------------------------------|----------------------------------------|
| <span id="x"></span><span id="X"></span>*x*<br/> | \[in\] The specified value.<br/> |



 

#### Return Value

The *x* parameter converted from degrees to radians.

#### Type Description



| Name  | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                                                  | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md) | Size                           |
|-------|----------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|--------------------------------|
| *x*   | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md), **vector**, or **matrix** | [**float**](/windows/desktop/WinProg/windows-data-types)                        | any                            |
| *ret* | same as input *x*                                                                                              | [**float**](/windows/desktop/WinProg/windows-data-types)                        | same dimension(s) as input *x* |

### rcp

Calculates a fast, approximate, per-component reciprocal.



| *ret* rcp(*x*) |
|----------------|



 

#### Parameters

<dl> <dt>

<span id="x"></span><span id="X"></span>*x*
</dt> <dd>

\[in\] The input value.

</dd> </dl>

#### Return Value

The reciprocal of the *x* parameter.

#### Type Description



| Name  | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                                                  | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md)                      | Size                           |
|-------|----------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|--------------------------------|
| *x*   | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md), **vector**, or **matrix** | [**float**](/windows/desktop/WinProg/windows-data-types) or [**double**](/windows/desktop/WinProg/windows-data-types) | any                            |
| *ret* | same as input *x*                                                                                              | [**float**](/windows/desktop/WinProg/windows-data-types) or [**double**](/windows/desktop/WinProg/windows-data-types) | same dimension(s) as input *x* |

### reflect

Returns a reflection vector using an incident ray and a surface normal.



| *ret* reflect(*i*, *n*) |
|-------------------------|



 

#### Parameters



| Item                                                   | Description                                          |
|--------------------------------------------------------|------------------------------------------------------|
| <span id="i"></span><span id="I"></span>*i*<br/> | \[in\] A floating-point, incident vector.<br/> |
| <span id="n"></span><span id="N"></span>*n*<br/> | \[in\] A floating-point, normal vector.<br/>   |



 

#### Return Value

A floating-point, reflection vector.

#### Remarks

This function calculates the reflection vector using the following formula: v = i - 2 \* n \* dot(i n) .

#### Type Description



| Name  | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                       | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md) | Size                           |
|-------|-------------------------------------------------------------------------------------|----------------------------------------------------------------|--------------------------------|
| *i*   | [**vector**](dx-graphics-hlsl-intrinsic-functions.md) | [**float**](/windows/desktop/WinProg/windows-data-types)                        | any                            |
| *n*   | [**vector**](dx-graphics-hlsl-intrinsic-functions.md) | [**float**](/windows/desktop/WinProg/windows-data-types)                        | same dimension(s) as input *i* |
| *ret* | [**vector**](dx-graphics-hlsl-intrinsic-functions.md) | [**float**](/windows/desktop/WinProg/windows-data-types)                        | same dimension(s) as input *i* |

### refract

Returns a refraction vector using an entering ray, a surface normal, and a refraction index.



| *ret* refract(*i*, *n*, ?) |
|----------------------------|



 

#### Parameters



| Item                                                   | Description                                                  |
|--------------------------------------------------------|--------------------------------------------------------------|
| <span id="i"></span><span id="I"></span>*i*<br/> | \[in\] A floating-point, ray direction vector.<br/>    |
| <span id="n"></span><span id="N"></span>*n*<br/> | \[in\] A floating-point, surface normal vector.<br/>   |
| *?*<br/>                                         | \[in\] A floating-point, refraction index scalar.<br/> |



 

#### Return Value

A floating-point, refraction vector. If the angle between the entering ray i and the surface normal n is too great for a given refraction index ?, the return value is (0,0,0).

#### Type Description



| Name              | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                       | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md) | Size                           |
|-------------------|-------------------------------------------------------------------------------------|----------------------------------------------------------------|--------------------------------|
| *i*               | [**vector**](dx-graphics-hlsl-intrinsic-functions.md) | [**float**](/windows/desktop/WinProg/windows-data-types)                        | any                            |
| *n*               | [**vector**](dx-graphics-hlsl-intrinsic-functions.md) | [**float**](/windows/desktop/WinProg/windows-data-types)                        | same dimension(s) as input *i* |
| ?                 | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md) | [**float**](/windows/desktop/WinProg/windows-data-types)                        | 1                              |
| refraction vector | [**vector**](dx-graphics-hlsl-intrinsic-functions.md) | [**float**](/windows/desktop/WinProg/windows-data-types)                        | same dimension(s) as input *i* |

### reversebits function

Reverses the order of the bits, per component.

#### Syntax

``` syntax
uint reversebits(
  in uint value
);
```

#### Parameters

<dl> <dt>

*value* \[in\]
</dt> <dd>

Type: **uint**

The input value.

</dd> </dl>

#### Return value

Type: **uint**

The input value, with the bit order reversed.

#### Remarks

The following overloaded versions are also available:

``` syntax
uint2 reversebits(uint2 value);
uint3 reversebits(uint3 value);
uint4 reversebits(uint4 value);
```

### round

Rounds the specified value to the nearest integer. Halfway cases are rounded to the nearest even.



| *ret* round(*x*) |
|------------------|



 

#### Parameters



| Item                                                   | Description                            |
|--------------------------------------------------------|----------------------------------------|
| <span id="x"></span><span id="X"></span>*x*<br/> | \[in\] The specified value.<br/> |



 

#### Return Value

The *x* parameter, rounded to the nearest integer within a floating-point type.

#### Type Description



| Name  | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                                                  | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md) | Size                           |
|-------|----------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|--------------------------------|
| *x*   | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md), **vector**, or **matrix** | [**float**](/windows/desktop/WinProg/windows-data-types)                        | any                            |
| *ret* | same as input *x*                                                                                              | [**float**](/windows/desktop/WinProg/windows-data-types)                        | same dimension(s) as input *x* |

### rsqrt

Returns the reciprocal of the square root of the specified value.



| *ret* rsqrt(*x*) |
|------------------|



 

#### Parameters



| Item                                                   | Description                            |
|--------------------------------------------------------|----------------------------------------|
| <span id="x"></span><span id="X"></span>*x*<br/> | \[in\] The specified value.<br/> |



 

#### Return Value

The reciprocal of the square root of the *x* parameter.

#### Remarks

This function uses the following formula: 1 / **sqrt**(*x*).

#### Type Description



| Name  | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                                                  | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md) | Size                           |
|-------|----------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|--------------------------------|
| *x*   | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md), **vector**, or **matrix** | [**float**](/windows/desktop/WinProg/windows-data-types)                        | any                            |
| *ret* | same as input *x*                                                                                              | [**float**](/windows/desktop/WinProg/windows-data-types)                        | same dimension(s) as input *x* |

### saturate (HLSL reference)

Clamps the specified value within the range of 0 to 1.



| *ret* saturate(*x*) |
|---------------------|



 

#### Parameters



| Item                                                   | Description                            |
|--------------------------------------------------------|----------------------------------------|
| <span id="x"></span><span id="X"></span>*x*<br/> | \[in\] The specified value.<br/> |



 

#### Return Value

The *x* parameter, clamped within the range of 0 to 1.

#### Type Description



| Name  | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                                                  | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md) | Size                           |
|-------|----------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|--------------------------------|
| *x*   | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md), **vector**, or **matrix** | [**float**](/windows/desktop/WinProg/windows-data-types)                        | any                            |
| *ret* | same as input *x*                                                                                              | [**float**](/windows/desktop/WinProg/windows-data-types)                        | same dimension(s) as input *x* |

### sign

Returns the sign of *x*.



| *ret* sign(*x*) |
|-----------------|



 

#### Parameters



| Item                                                   | Description                        |
|--------------------------------------------------------|------------------------------------|
| <span id="x"></span><span id="X"></span>*x*<br/> | \[in\] The input value.<br/> |



 

#### Return Value

Returns -1 if *x* is less than zero; 0 if *x* equals zero; and 1 if *x* is greater than zero.

#### Type Description



| Name  | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                                                  | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md)                 | Size                           |
|-------|----------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------|--------------------------------|
| *x*   | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md), **vector**, or **matrix** | [**float**](/windows/desktop/WinProg/windows-data-types), [**int**](/windows/desktop/WinProg/windows-data-types) | any                            |
| *ret* | same as input *x*                                                                                              | [**int**](/windows/desktop/WinProg/windows-data-types)                                          | same dimension(s) as input *x* |

### sin

Returns the sine of the specified value.



| *ret* sin(*x*) |
|----------------|



 

#### Parameters



| Item                                                   | Description                                        |
|--------------------------------------------------------|----------------------------------------------------|
| <span id="x"></span><span id="X"></span>*x*<br/> | \[in\] The specified value, in radians.<br/> |



 

#### Return Value

The sine of the *x* parameter.

#### Type Description



| Name  | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                                                  | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md) | Size                           |
|-------|----------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|--------------------------------|
| *x*   | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md), **vector**, or **matrix** | [**float**](/windows/desktop/WinProg/windows-data-types)                        | any                            |
| *ret* | same as input *x*                                                                                              | [**float**](/windows/desktop/WinProg/windows-data-types)                        | same dimension(s) as input *x* |

### sinh

Returns the hyperbolic sine of the specified value.



| *ret* sinh(*x*) |
|-----------------|



 

#### Parameters



| Item                                                   | Description                                        |
|--------------------------------------------------------|----------------------------------------------------|
| <span id="x"></span><span id="X"></span>*x*<br/> | \[in\] The specified value, in radians.<br/> |



 

#### Return Value

The hyperbolic sine of the *x* parameter.

#### Type Description



| Name  | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                                                  | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md) | Size                           |
|-------|----------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|--------------------------------|
| *x*   | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md), **vector**, or **matrix** | [**float**](/windows/desktop/WinProg/windows-data-types)                        | any                            |
| *ret* | same as input *x*                                                                                              | [**float**](/windows/desktop/WinProg/windows-data-types)                        | same dimension(s) as input *x* |

### smoothstep

Returns a smooth Hermite interpolation between 0 and 1, if *x* is in the range \[*min*, *max*\].



| *ret* smoothstep(*min*, *max*, *x*) |
|-------------------------------------|



 

#### Parameters



| Item                                                         | Description                                               |
|--------------------------------------------------------------|-----------------------------------------------------------|
| <span id="min"></span><span id="MIN"></span>*min*<br/> | \[in\] The minimum range of the *x* parameter.<br/> |
| <span id="max"></span><span id="MAX"></span>*max*<br/> | \[in\] The maximum range of the *x* parameter.<br/> |
| <span id="x"></span><span id="X"></span>*x*<br/>       | \[in\] The specified value to be interpolated.<br/> |



 

#### Return Value

Returns 0 if *x* is less than *min*; 1 if *x* is greater than *max*; otherwise, a value between 0 and 1 if *x* is in the range \[*min*, *max*\].

#### Remarks

Use the **smoothstep** HLSL intrinsic function to create a smooth transition between two values. For example, you can use this function to blend two colors smoothly.

#### Type Description



| Name  | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                                                  | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md) | Size                           |
|-------|----------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|--------------------------------|
| *x*   | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md), **vector**, or **matrix** | [**float**](/windows/desktop/WinProg/windows-data-types)                        | any                            |
| *min* | same as input *x*                                                                                              | [**float**](/windows/desktop/WinProg/windows-data-types)                        | same dimension(s) as input *x* |
| *max* | same as input *x*                                                                                              | [**float**](/windows/desktop/WinProg/windows-data-types)                        | same dimension(s) as input *x* |
| *ret* | same as input *x*                                                                                              | [**float**](/windows/desktop/WinProg/windows-data-types)                        | same dimension(s) as input *x* |

### sqrt

Returns the square root of the specified floating-point value, per component.



| *ret* sqrt(*x*) |
|-----------------|



 

#### Parameters



| Item                                                   | Description                                           |
|--------------------------------------------------------|-------------------------------------------------------|
| <span id="x"></span><span id="X"></span>*x*<br/> | \[in\] The specified floating-point value.<br/> |



 

#### Return Value

The square root of the *x* parameter, per component.

#### Type Description



| Name  | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                                                  | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md) | Size                           |
|-------|----------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|--------------------------------|
| *x*   | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md), **vector**, or **matrix** | [**float**](/windows/desktop/WinProg/windows-data-types)                        | any                            |
| *ret* | same as input *x*                                                                                              | [**float**](/windows/desktop/WinProg/windows-data-types)                        | same dimension(s) as input *x* |

### step

Compares two values, returning 0 or 1 based on which value is greater.



| *ret* step(*y*, *x*) |
|----------------------|



 

#### Parameters



| Item                                                   | Description                                                   |
|--------------------------------------------------------|---------------------------------------------------------------|
| <span id="y"></span><span id="Y"></span>*y*<br/> | \[in\] The first floating-point value to compare.<br/>  |
| <span id="x"></span><span id="X"></span>*x*<br/> | \[in\] The second floating-point value to compare.<br/> |



 

#### Return Value

1 if the *x* parameter is greater than or equal to the *y* parameter; otherwise, 0.

#### Remarks

This function uses the following formula: (*x* >= *y*) ? 1 : 0. The function returns either 0 or 1 depending on whether the *x* parameter is greater than the *y* parameter. To compute a smooth interpolation between 0 and 1, use the [**smoothstep**](dx-graphics-hlsl-smoothstep.md) HLSL intrinsic function.

#### Type Description



| Name  | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                                                  | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md) | Size                           |
|-------|----------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|--------------------------------|
| *y*   | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md), **vector**, or **matrix** | [**float**](/windows/desktop/WinProg/windows-data-types)                        | any                            |
| *x*   | same as input *y*                                                                                              | [**float**](/windows/desktop/WinProg/windows-data-types)                        | same dimension(s) as input *y* |
| *ret* | same as input *y*                                                                                              | [**float**](/windows/desktop/WinProg/windows-data-types)                        | same dimension(s) as input *y* |

### tan

Returns the tangent of the specified value.



| *ret* tan(*x*) |
|----------------|



 

#### Parameters



| Item                                                   | Description                                        |
|--------------------------------------------------------|----------------------------------------------------|
| <span id="x"></span><span id="X"></span>*x*<br/> | \[in\] The specified value, in radians.<br/> |



 

#### Return Value

The tangent of the *x* parameter.

#### Type Description



| Name  | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                                                  | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md) | Size                           |
|-------|----------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|--------------------------------|
| *x*   | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md), **vector**, or **matrix** | [**float**](/windows/desktop/WinProg/windows-data-types)                        | any                            |
| *ret* | same as input *x*                                                                                              | [**float**](/windows/desktop/WinProg/windows-data-types)                        | same dimension(s) as input *x* |

### tanh

Returns the hyperbolic tangent of the specified value.



| *ret* tanh(*x*) |
|-----------------|



 

#### Parameters



| Item                                                   | Description                                        |
|--------------------------------------------------------|----------------------------------------------------|
| <span id="x"></span><span id="X"></span>*x*<br/> | \[in\] The specified value, in radians.<br/> |



 

#### Return Value

The hyperbolic tangent of the *x* parameter.

#### Type Description



| Name  | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                                                  | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md) | Size                           |
|-------|----------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|--------------------------------|
| *x*   | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md), **vector**, or **matrix** | [**float**](/windows/desktop/WinProg/windows-data-types)                        | any                            |
| *ret* | same as input *x*                                                                                              | [**float**](/windows/desktop/WinProg/windows-data-types)                        | same dimension(s) as input *x* |

### transpose

Transposes the specified input matrix.



| ret transpose(*x*) |
|--------------------|



 

#### Parameters



| Item                                                   | Description                             |
|--------------------------------------------------------|-----------------------------------------|
| <span id="x"></span><span id="X"></span>*x*<br/> | \[in\] The specified matrix.<br/> |



 

#### Return Value

The transposed value of the *x* parameter.

#### Remarks

If the dimensions of the source matrix are *rows* *columns*, the resulting matrix is *columns* *rows*.

#### Type Description



| Name | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                       | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md)                                                         | Size                                                                                   |
|------|-------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------|
| *x*  | [**matrix**](dx-graphics-hlsl-intrinsic-functions.md) | [**float**](/windows/desktop/WinProg/windows-data-types), [**int**](/windows/desktop/WinProg/windows-data-types), [**bool**](/windows/desktop/WinProg/windows-data-types) | any                                                                                    |
| ret  | [**matrix**](dx-graphics-hlsl-intrinsic-functions.md) | [**float**](/windows/desktop/WinProg/windows-data-types), [**int**](/windows/desktop/WinProg/windows-data-types), [**bool**](/windows/desktop/WinProg/windows-data-types) | rows = same number of columns as input *x*, columns = same number of rows as input *x* |

### trunc

Truncates a floating-point value to the integer component.



| ret trunc(*x*) |
|----------------|



 

#### Parameters



| Item                                                   | Description                            |
|--------------------------------------------------------|----------------------------------------|
| <span id="x"></span><span id="X"></span>*x*<br/> | \[in\] The specified input.<br/> |



 

#### Return Value

The input value truncated to an integer component.

#### Remarks

This function truncates a floating-point value to the integer component. Given a floating-point value of 1.6, the trunc function would return 1.0, where as the [**round (DirectX HLSL)**](dx-graphics-hlsl-round.md) function would return 2.0.

#### Type Description



| Name | [**Template Type**](dx-graphics-hlsl-intrinsic-functions.md)                                                  | [**Component Type**](dx-graphics-hlsl-intrinsic-functions.md) | Size                         |
|------|----------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|------------------------------|
| *x*  | [**scalar**](dx-graphics-hlsl-intrinsic-functions.md), **vector**, or **matrix** | [**float**](/windows/desktop/WinProg/windows-data-types)                        | any                          |
| ret  | Same type as input x                                                                                           | [**float**](/windows/desktop/WinProg/windows-data-types)                        | Same dimension(s) as input x |
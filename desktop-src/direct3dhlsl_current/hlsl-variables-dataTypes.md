# Data Types

## Writing to Globals

Global variables are treated as constants in HLSL, but just like FXC, DXC also enables support for writing to globals with the `-Gec` flag as shown in the following example.

```C++
float gvar; // Write enabled with "-Gec"

float4 main(uint a : A) : SV_Target
{
  gvar = a * 2.0f;  
  return (float4) gvar;
} 
```

## Alignment

Basic Type Alignment rules - additional alignment and layout rules must be applied on top of these for legacy constant buffers:

1. [`Scalars`](#scalar-types) are naturally aligned to their storage size.
1. [`Vector`](#vector-types) and [`Matrix`](#matrix-type) types are aligned by their component type alignment.
1. [`Structs`](hlsl-language-type-struct.md) are aligned by the max of it's member alignments.
1. Arrays are aligned by the alignment of the array element type.

### Legacy Constant Buffer Alignment

Legacy Constant buffer still contains legacy 4 DWORD (128 bit) row alignment for indexing. For 16-bit types, we can fit up to 8 scalars for a single row.

### Structure Alignment

HLSL Structure will follow natural alignment for scalar types. This is equivalent to the layout that C++ compiler would produce under `#pragma pack (8)`.

## Scalar Types

### bool

<b>bool</b>

`true` or `false`

| <b>Minimum Shader Model</b> | 6.0 |
| --- | --- |
| <b>Minimum Language Set</b> | 2016 |

### int

<b>int</b>

32-bit signed integer.

| <b>Minimum Shader Model</b> | 6.0 |
| --- | --- |
| <b>Minimum Language Set</b> | 2016 |

<b>min12int</b>

Minimum precision 12-bit signed integer value.  Used for arithmetic and logical operations but not memory addressing.

>**Note:** Converted implicitly to `int16_t` when using `DXC` command line argument `-enable-16bit-types` in combination with <i>HLSL 2018</i> and <i>Shader Model 6.2</i>.

| <b>Minimum Shader Model</b> | 6.0 |
| --- | --- |
| <b>Minimum Language Set</b> | 2016 |

<b>min16int</b>

Minimum precision 16-bit signed integer value.  Used for arithmetic and logical operations but not memory addressing.

>**Note:** Converted implicitly to `int16_t` when using `DXC` command line argument `-enable-16bit-types` in combination with <i>HLSL 2018</i> and <i>Shader Model 6.2</i>.

| <b>Minimum Shader Model</b> | 6.0 |
| --- | --- |
| <b>Minimum Language Set</b> | 2016 |

<b>int16_t</b>

16-bit signed integer.

| <b>Minimum Shader Model</b> | 6.2 |
| --- | --- |
| <b>Minimum Language Set</b> | 2018 |

<b>int32_t</b>

32-bit signed integer.

| <b>Minimum Shader Model</b> | 6.0 |
| --- | --- |
| <b>Minimum Language Set</b> | 2018 |

<b>int64_t</b>

64-bit signed integer.

| <b>Minimum Shader Model</b> | 6.0 |
| --- | --- |
| <b>Minimum Language Set</b> | 2016 |

<b>int8_t4_packed</b>

4 packed and sign extended int8_t values in a uint32_t

| <b>Minimum Shader Model</b> | 6.6 |
| --- | --- |
| <b>Minimum Language Set</b> | 2016 |

### uint

<b>uint</b>

32-bit unsigned integer.

| <b>Minimum Shader Model</b> | 6.0 |
| --- | --- |
| <b>Minimum Language Set</b> | 2016 |

<b>min12uint</b>

minimum precision 12-bit unsigned integer value.  Used for arithmetic and logical operations but not memory addressing.

>**Note:** Converted implicitly to `int16_t` when using `DXC` command line argument `-enable-16bit-types` in combination with <i>HLSL 2018</i> and <i>Shader Model 6.2</i>.

| <b>Minimum Shader Model</b> | 6.0 |
| --- | --- |
| <b>Minimum Language Set</b> | 2016 |

<b>min16uint</b>

minimum precision 16-bit unsigned integer value.  Used for arithmetic and logical operations but not memory addressing.

>**Note:** Converted implicitly to `int16_t` when using `DXC` command line argument `-enable-16bit-types` in combination with <i>HLSL 2018</i> and <i>Shader Model 6.2</i>.

| <b>Minimum Shader Model</b> | 6.0 |
| --- | --- |
| <b>Minimum Language Set</b> | 2016 |

<b>uint16_t</b>

16-bit unsigned integer.

| <b>Minimum Shader Model</b> | 6.2 |
| --- | --- |
| <b>Minimum Language Set</b> | 2018 |

<b>uint32_t</b>

32-bit unsigned integer.

| <b>Minimum Shader Model</b> | 6.0 |
| --- | --- |
| <b>Minimum Language Set</b> | 2018 |

<b>uint64_t</b>

64-bit unsigned integer.

| <b>Minimum Shader Model</b> | 6.0 |
| --- | --- |
| <b>Minimum Language Set</b> | 2016 |

<b>uint8_t4_packed</b>

4 packed and zero extended int8_t values in a uint32_t

| <b>Minimum Shader Model</b> | 6.6 |
| --- | --- |
| <b>Minimum Language Set</b> | 2016 |

### dword

<b>dword</b>

32-bit unsigned integer.

| <b>Minimum Shader Model</b> | 6.0 |
| --- | --- |
| <b>Minimum Language Set</b> | 2016 |

### half

<b>half</b>

32-bit floating point value. This data type is provided only for language compatibility. A half data type cannot be used on a uniform global variable (use the /Gec flag if this functionality is desired).

>**Note:** Converted implicitly to `float16_t` when using `DXC` command line argument `-enable-16bit-types` in combination with <i>HLSL 2018</i> and <i>Shader Model 6.2</i>. Without <i>Shader Model 6.2</i>, converted implicitly to `float32_t`.

| <b>Minimum Shader Model</b> | 6.0 |
| --- | --- |
| <b>Minimum Language Set</b> | 2016 |

### float

<b>float</b>

32-bit floating point value.

>**Note:** Can use modifiers `snorm` 

| <b>Minimum Shader Model</b> | 6.0 |
| --- | --- |
| <b>Minimum Language Set</b> | 2016 |

<b>min10float</b>

Minimum precision 10-bit floating point value.  Used for arithmetic and logical operations but not memory addressing.

>**Note:** Converted implicitly to `float16_t` when using `DXC` command line argument `-enable-16bit-types` in combination with <i>HLSL 2018</i> and <i>Shader Model 6.2</i>.

| <b>Minimum Shader Model</b> | 6.0 |
| --- | --- |
| <b>Minimum Language Set</b> | 2016 |

<b>min16float</b>

Minimum precision 16-bit signed integer value.  Used for arithmetic and logical operations but not memory addressing.

>**Note:** Converted implicitly to `float16_t` when using `DXC` command line argument `-enable-16bit-types` in combination with <i>HLSL 2018</i> and <i>Shader Model 6.2</i>.

| <b>Minimum Shader Model</b> | 6.0 |
| --- | --- |
| <b>Minimum Language Set</b> | 2016 |

<b>float16_t</b>

16-bit floating point value.

| <b>Minimum Shader Model</b> | 6.2 |
| --- | --- |
| <b>Minimum Language Set</b> | 2018 |

<b>float32_t</b>

32-bit floating point value.

| <b>Minimum Shader Model</b> | 6.0 |
| --- | --- |
| <b>Minimum Language Set</b> | 2018 |

<b>float64_t</b>

64-bit floating point value.

| <b>Minimum Shader Model</b> | 6.0 |
| --- | --- |
| <b>Minimum Language Set</b> | 2018 |

### double

<b>double</b>

64-bit floating point value. You cannot use double precision values as inputs and outputs for a stream. To pass double precision values between shaders, declare each double as a pair of uint data types. Then, use the [`asuint`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/asuint) function to pack each double into the pair of uints and the [`asdouble`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/asdouble) function to unpack the pair of uints back into the double.

>**Note:** Converted implicitly to `float64_t`.

| <b>Minimum Shader Model</b> | 6.0 |
| --- | --- |
| <b>Minimum Language Set</b> | 2016 |

## Vector Types

A vector contains between one and four scalar components; every component of a vector must be of the same type.

```
TypeComponents Name
```

### Components

| Item | Description |
| - | - |
| TypeComponents | A single name that contains two parts. The first part is one of the [`scalar`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/dx-graphics-hlsl-data-types) types. The second part is the number of components, which must be between 1 and 4 inclusive. |
| Name | An ASCII string that uniquely identifies the variable name. |

<b>Examples</b>

Here are some examples:

```
bool    bVector;   // scalar containing 1 Boolean
int1    iVector = 1;
float3  fVector = { 0.2f, 0.3f, 0.4f };
```

A vector can be declared using this syntax also:

```
vector <Type, Number> VariableName
```

Here are some examples:

```
vector <int,    1> iVector = 1;
vector <double, 4> dVector = { 0.2, 0.3, 0.4, 0.5 };
```

| <b>Minimum Shader Model</b> | 6.0 |
| --- | --- |
| <b>Minimum Language Set</b> | 2016 |

## Matrix Type

A matrix is a special data type that contains between one and sixteen components. Every component of a matrix must be of the same type.

Matrix types may be layed out in either row-major or column-major orientation. This impacts not only component ordering in memory, but padding for row (or column) alignment in legacy constant buffers. For storage, the column major matrix can be considered equivalent to a row major matrix with the dimensions transposed. In other words, `row_major matrix<float, R, C>` is equivalent to `column_major matrix<float, C, R>` in storage layout and alignment constraints. Therefore the alignment constraints will be described here in terms of the row_major equivalent storage layout.

### Components

| Item | Description |
| - | - |
| TypeComponents | A single name that contains three parts. The first part is one of the [`scalar`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/dx-graphics-hlsl-data-types) types. The second part is the number of rows. The third part is the number of columns. The number of rows and columns is a positive integer between 1 and 4 inclusive. |
| Name | An ASCII string that uniquely identifies the variable name. |

<b>Examples</b>

```
int1x1    iMatrix;   // integer matrix with 1 row,  1 column
int4x1    iMatrix;   // integer matrix with 4 rows, 1 column
int1x4    iMatrix;   // integer matrix with 1 row, 4 columns
double3x3 dMatrix;   // double matrix with 3 rows, 3 columns

float2x2 fMatrix = { 0.0f, 0.1, // row 1
                     2.1f, 2.2f // row 2
                   };
```

A matrix can be declared using this syntax also:

```
matrix <Type, Number> VariableName;
```

The matrix type uses the angle brackets to specify the type, the number of rows, and the number of columns. This example creates a floating-point matrix, with two rows and two columns. Any of the scalar data types can be used.

Here is an example:

```
matrix <float, 2, 2> fMatrix = { 0.0f, 0.1, // row 1
                                 2.1f, 2.2f // row 2
                               };
```

| <b>Minimum Shader Model</b> | 6.0 |
| --- | --- |
| <b>Minimum Language Set</b> | 2016 |

## Arrays

An array is a sequence of objects of the same type that occupy a contiguous area of memory.  The objects contained in the array include [`scalar types`](#scalar-types), [`vector types`](#vector-types), and [`matrix types`](#matrix-type).  Compiler rules require empty arrays to be initialized upon instantiation.

```hlsl
// allocated unitialized array 
int sampleArray[2];

// allocate initialized array
int sampleArray[2] = {0, 1};

// empty initialized array
// allocated based on size of initialized elements
int sampleArray[] = {0, 1};
```

### Multi-dimensional arrays

HLSL supports declaration and usage of multi-dimensional arrays.

```hlsl
int multiDimArray[2][3] = {
  { 0, 1, 2 },
  { 3, 4, 5 }
};
```

>**Note** The compiler stores data linearly in a multi-dimensional array.  In the above example, the laid out data is as follows: {`0`, `1`, `2`, `3`, `4`, `5`}

### Out-of-bound array accesses
By default, DXC errors out when finding constant index references to an array, which is out of bound. For example, the following HLSL shader fails to compile with an error message: `error: array index 3 is out of bounds`. You could turn this error into a warning by setting the language version to 2016 (that is, by using the `-HV 2016` flag) only when the out-of-bound access happens in the unused or dead code.

```C++
void main()
{
  uint x[2];
  x[3]=1.f; // Out-of-bound access.
} 
```

### Length property on constant arrays

The `Length` property on constant arrays is supported on DXC under the `-Gec` flag as shown in the following example.

```C++
uint main() : OUT
{
    int x[5];
    return x.Length;
}
```
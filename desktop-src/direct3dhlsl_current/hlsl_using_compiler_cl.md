# Using the Command Line

## DXC command-line interface

A complete list of command-line flags is obtained by running `dxc.exe -?`. If you're familiar with FXC, many of the command-line arguments are the same. Following are some common flags.

```
-D <value>              Define macro.
-E <value>              Entry point name.
-Fd <file>              Write debug information to the specified file or directory; trail \ to autogenerate.
-Fo <file>              Output object file.
-Gec                    Enable backward compatibility mode.
-HV <value>             HLSL version (2016, 2017, 2018, 2021). Default is 2018.
-Od                     Disable optimizations.
-T <profile>            Set target profile.
    <profile>: ps_6_0, ps_6_1, ps_6_2, ps_6_3, ps_6_4, ps_6_5, ps_6_6,
                vs_6_0, vs_6_1, vs_6_2, vs_6_3, vs_6_4, vs_6_5, vs_6_6,
                cs_6_0, cs_6_1, cs_6_2, cs_6_3, cs_6_4, cs_6_5, cs_6_6,
                gs_6_0, gs_6_1, gs_6_2, gs_6_3, gs_6_4, gs_6_5, gs_6_6,
                ds_6_0, ds_6_1, ds_6_2, ds_6_3, ds_6_4, ds_6_5, ds_6_6,
                hs_6_0, hs_6_1, hs_6_2, hs_6_3, hs_6_4, hs_6_5, hs_6_6,
                lib_6_3, lib_6_4, lib_6_5, lib_6_6,
-Vd                     Disable validation.
-Zi                     Enable debug information.
-Zpc                    Pack matrices in column-major order.
-Zpr                    Pack matrices in row-major order.
  ```

>**NOTE:** DXC has been updated to no longer embed .pdb (program database/debug information) by default in the shader. By default, .pdbs are external.

`dxc.exe --version` will also report which variant of the compiler it is. 

Following is an example of using the command-line interface.

```
dxc -E main -T ps_6_0 -Fo myshader.bin -Zi -Fd myshader.pdb -D MYDEFINE=1 myshader.hlsl
```

In this example, myshader.hlsl is compiled to a shader model 6.0 pixel shader. The compiled shader is written to myshader.bin as specified by the `-Fo` flag. Debug information is enabled with the `-Zi` flag, and the .pdb is written out to myshader.pdb with the `-Fd` flag. If you would prefer that the compiler automatically generate a .pdb name, you can supply `.\` as the `-Fd` argument. Again, the debug information in the PDB isn't embedded in the shader.

## "Legacy" Layout in native 16-bit types mode (-enable-16bit-types)

Native 16-bit types may be packed into the same rows as other fixed precision types. Alignment and other rules stated above all apply still. For instance, a 32-bit value following a single 16-bit value starting a row will be 32-bit aligned, leaving 16-bits of padding between the values.

## "Non-Legacy" packing (-no-legacy-cbuf-layout)

Follows Structured Buffer Packing.

## Denorm Mode

Starting from Shader Model 6.2, you can provide -denorm command line option to specify behaviors for 32-bit floating point denormal number.

Available values for this option are "preserve", "ftz", and "any". These options will be represented as function attributes in DXIL.

Affected instructions for this mode are basic arithmetic operations (add, subtract, multiply, and divide).

Note that fp16/fp64 need to preserve denorms regardless of this option.

| -denorm \<value\>    | function attribute          | behavior                                      |
| :------------------: |:---------------------------:| :-------------------------------------------: |
| preserve             |"fp32-denorm-mode"="preserve"| denorm input/output should be preserved       |
| ftz                  |"fp32-denorm-mode"="ftz"     | denorm input/output should be flushed to zero |
| any                  |"fp32-denorm-mode"="any"     | any behavior is allowed         

| <b>Minimum Shader Model</b> | 6.2 |
| --- | --- |
| <b>Minimum Language Set</b> | 2016 |

## Shader hash

The hash for the shader can be saved to file by using the `-Fsh` command-line flag. Through the .dll interface, it's always available by using `IDxcResult::GetOutput`.  

On Windows, the shader DXIL is hashed to determine the value.  

## Reflection

By default, reflection data is stored in the shader. The `-Qstrip_reflect` flag can be used to remove it.  
The flag `-Fre` can now be used to save your reflection data out to a separate file, and the file is saved even if `-Qstrip_reflect` is used. Similarly, `IDxcResult::GetOutput` can be used to get the separate reflection blob, even if `-Qstrip_reflect` is used. `IDxcUtils::CreateReflection` can create a reflection interface from these separate reflection blobs.

## PDBs

When your shader is compiled, the .pdb filename (supplied with the `-Fd` option) and a hash of the shader is stored in the shader. PIX uses this information to find the shader .pdb.  

### Slim PDBs
A new compilation flag, `-Zs` creates a new type of .pdb that is far smaller than traditional .pdbs and decreases compilation time when .pdbs are generated.  These “slim” .pdbs contain
only the source code and compilation arguments used to generate the shader.  PIX will generate the additional debug information required “on demand” when the shader is debugged.
 
Note that full .pdbs (which contain everything a slim .pdb does plus the full debug information used by the debugger) are still supported with the `-Zi` flag.
 
### A note on compiler versioning.
When a .pdb is generated, the version of the compiler is stored in the .pdb so that PIX can know which compiler was use to originally compiler the shader.  PIX will report if the current compiler associated with PIX does not match the one used to generate the shader and the matching compiler can be supplied if desired.
 
### New pdb interface.
A new interface call IDxcPdbUtils has been introduced in dxcapi.h.  This interface allows you to inspect the source, compilation arguments, compiler version, and hash as well as allows you to recompile the shader from the pdb if desired.

## Porting Shaders from FXC to DXC

1. Enable some of the old FXC compilation behaviors that are disabled by default on DXC. This is supported on DXC through the following compiler flags:

    - `-Gec`: Enable Direct3D 9 backward compatibility (for example, enable support for `COLOR` semantic that's supported only until Direct3D 9).

    - `-HV`: Enable FXC backward compatibility by setting the language version to 2016 (that is, `-HV 2016`). This enables a certain legacy language semantic that's available on FXC.

    - `-flegacy-macro-expansion`: Expand the operands before performing token-pasting operation (FXC behavior).

    - `-flegacy-resource-reservation`: Reserve unused explicit register assignments for compatibility with shader model 5.0 and earlier.

2. Provide information about the old deprecated HLSL syntaxes that were supported on FXC but are no longer supported on DXC.

## Legacy resource reservation by using the `-flegacy-resource-reservation` flag

For shader model 5.0 or earlier, FXC would factor in the register allocation of unused resources when doing register allocation for used ones. For example, when compiling the following shader on FXC with SM5.0 and 5.1, `Tex1[1]` is bound to `t4` and `t0`, respectively.
When using DXC, to achieve the FXC resource allocation behavior with SM5.0 or earlier, use the `-flegacy-resource-reservation` flag.

```C++
Texture2D Tex0[2] : register(t1);
Texture2D Tex1[2];

float4 main() : SV_Target
{
    return Tex1[1].Load((uint3)0);
} 
```

### Legacy macro expansion by using the `-flegacy-macro-expansion` flag
The following HLSL shader compiles successfully on FXC, but errors out on DXC as `b##slot` is replaced with `bSLOT_VAL` instead of `b3`, thus causing compilation failure. To achieve the FXC token replacement behavior on DXC, compile with the additional flag "`-flegacy-macro-expansion`".

```C++
#define SLOT_VAL 3
#define CBUFFER_ALIGNED( name, slot ) cbuffer name : register( b##slot )
 
CBUFFER_ALIGNED( MyCBuffer, SLOT_VAL )
{
       float4        val;
};
```

You can avoid the usage of the -flegacy-macro-expansion flag in this case by following standard preprocessor rules.

```C++
#define SLOT_VAL 3
#define PASTE1(a, b) a##b
#define PASTE(a, b) PASTE1(a, b)
#define CBUFFER_ALIGNED( name, slot ) cbuffer name : register( PASTE(b, slot) )
CBUFFER_ALIGNED( MyCBuffer, SLOT_VAL )
{
       float4        val;
};
```


-flegacy-macro-expansion doesn't help for cases where the tokens are not macro arguments, though fxc still expands these.  The following will result in an error even if -flegacy-macro-expansion is used.

```C++
#define C 4
#define A4 float4
#define TYPE A##C

#define FUNC(ty) ty main() : OUT { return 0; }
FUNC(TYPE)
```

 The following change will bring the HLSL into compatibility with standard preprocessor rules, no longer requiring the -flegacy-macro-expansion option.

```C++
#define C 4
#define A4 float4
#define PASTE1(a, b) a##b
#define PASTE(a, b) PASTE1(a, b)
#define TYPE PASTE(A, C)

#define FUNC(ty) ty main() : OUT { return 0; }
FUNC(TYPE)
```
# Built-in Constants

Built-in constants are predefined enumeration values and flags.  These values are pre-defined as opposed to the user-defined language feature [`enumeration`](dx-graphics-hlsl.md).

## Predefined Version Macros

Starting with the March 2020 release, a collection of predefined macros indicating version and compile target information are available from within the shader code. These allow preprocessor conditionals to depend on target shader model version, target shader stage, language version, or compiler release version. Using these macros, a single shader can adapt to multiple versions or invocation parameters accordingly.

### Shader Target Defines

The shader target indicated by the `-T <stage>_<major>_<minor>` option is reflected in the compiler through shader stage and shader model version defines.

#### Shader Stage Defines

A series of defines with constant values represent the possible shader stages:
* `__SHADER_STAGE_VERTEX`
* `__SHADER_STAGE_PIXEL`
* `__SHADER_STAGE_GEOMETRY`
* `__SHADER_STAGE_HULL`
* `__SHADER_STAGE_DOMAIN`
* `__SHADER_STAGE_COMPUTE`
* `__SHADER_STAGE_AMPLIFICATION`
* `__SHADER_STAGE_MESH`
* `__SHADER_STAGE_LIBRARY`

The predefined macro, `__SHADER_TARGET_STAGE`, is set at compilation time depending on the option provided to the `-T` flag to one of the above values. To use this value to conditionally include code, `__SHADER_TARGET_STAGE` should be compared with one of the above predefined constants. For example:

```hlsl
#if __SHADER_TARGET_STAGE == __SHADER_STAGE_AMPLIFICATION
  DispatchMesh(8, 8, 1, pld);
#endif
```

#### Shader Model Version Defines

The shader model version targeted by the compile is available in the shader code by the `__SHADER_TARGET_MAJOR` and `__SHADER_TARGET_MINOR` defined integers. These contain the <major> and <minor> versions respectively as specified at compile time.

They can be used to enable features where the targeted shader model allows.

```hlsl
#if __SHADER_TARGET_MINOR < 6
RWTexture2D<int64_t> myTexture : register (u0);
#endif
...
#if __SHADER_TARGET_MINOR >= 6
    RWTexture2D<int64_t> myTexture = ResourceDescriptorHeap[0];
#endif


```

Note that these reflect the shader model specified at compile time and not the maximum shader model supported.

### HLSL Language Version Define

The `__HLSL_VERSION` macro contains an integer representing the HLSL language version specified by the `-HV <version>` flag or the default the compiler uses. Current options are:

* 2016 - compatibility version useful for compatibility with FXC
* 2017 - Added enums to the language
* 2018 - Current default version
* 2021 - Latest version with C++ style features that can be enabled, but is not yet the default

### Compiler Release Version Defines

The `__hlsl_dx_compiler` define has been available for all versions of DXC. It is defined by DXC, but not by the FXC compiler and can be used to differentiate between the two.

Predefined integers representing the four components of the version information of the current compiler.
* __DXC_VERSION_MAJOR
* __DXC_VERSION_MINOR
* __DXC_VERSION_RELEASE
* __DXC_VERSION_COMMITS

As reported by `dxc -?` or `dxc --version` (where available). A release compiler has a form similar to: "1.6.2106.0" is major version of 1, minor of 6, release 2106, and the commits number is 0. Builds from the main branch outside a release will be of the form "1.6.0.2955" where the final number represents the number of commits with a release number of 0. If the shader is to be compiled with non-release compilers, this will have to be accounted for.

This can be useful to work around bugs in a given version. For example, to work around a bug present in 1.6.2106 and earlier releases:

```hlsl
#if __DXC_VERSION_MAJOR == 1 && (__DXC_VERSION_MINOR < 6 || \
                                 (__DXC_VERSION_MINOR == 6 && __DXC_VERSION_RELEASE <= 2106 \
                                                                 && __DXC_VERSION_RELEASE > 0))
  return WARBug12345(Outputs);
#else
  return Outputs;
#endif
```

## Raytracing

### RAY\_FLAG enumeration

Flags passed to the [**TraceRay**](traceray-function.md) function to override transparency, culling, and early-out behavior.

#### Syntax


```
enum RAY_FLAG : uint
{
    RAY_FLAG_NONE                            = 0x00,
    RAY_FLAG_FORCE_OPAQUE                    = 0x01,
    RAY_FLAG_FORCE_NON_OPAQUE                = 0x02,
    RAY_FLAG_ACCEPT_FIRST_HIT_AND_END_SEARCH = 0x04,
    RAY_FLAG_SKIP_CLOSEST_HIT_SHADER         = 0x08,
    RAY_FLAG_CULL_BACK_FACING_TRIANGLES      = 0x10,
    RAY_FLAG_CULL_FRONT_FACING_TRIANGLES     = 0x20,
    RAY_FLAG_CULL_OPAQUE                     = 0x40,
    RAY_FLAG_CULL_NON_OPAQUE                 = 0x80,
    RAY_FLAG_SKIP_TRIANGLES                  = 0x100,
    RAY_FLAG_SKIP_PROCEDURAL_PRIMITIVES      = 0x200,
}; 
```

<dl> <dt>

<span id="RAY_FLAG_NONE"></span><span id="ray_flag_none"></span>**RAY\_FLAG\_NONE**
</dt> <dd>

No options selected.

</dd> <dt>

<span id="RAY_FLAG_FORCE_OPAQUE"></span><span id="ray_flag_force_opaque"></span>**RAY\_FLAG\_FORCE\_OPAQUE**
</dt> <dd>

All ray-primitive intersections encountered in a raytrace are treated as opaque.  So no any hit shaders will be executed regardless of whether or not the hit geometry specifies D3D12\_RAYTRACING\_GEOMETRY\_FLAG\_OPAQUE, and regardless of the instance flags on the instance that was hit.

This flag is mutually exclusive with RAY\_FLAG\_FORCE\_NON\_OPAQUE, RAY\_FLAG\_CULL\_OPAQUE and RAY\_FLAG\_CULL\_NON\_OPAQUE.


</dd> <dt>

<span id="RAY_FLAG_FORCE_NON_OPAQUE"></span><span id="ray_flag_force_non_opaque"></span>**RAY\_FLAG\_FORCE\_NON\_OPAQUE**
</dt> <dd>

All ray-primitive intersections encountered in a raytrace are treated as non-opaque.  So any hit shaders, if present, will be executed regardless of whether or not the hit geometry specifies D3D12\_RAYTRACING\_GEOMETRY\_FLAG\_OPAQUE, and regardless of the instance flags on the instance that was hit.
This flag is mutually exclusive with RAY\_FLAG\_FORCE_\OPAQUE, RAY\_FLAG\_CULL\_OPAQUE and RAY\_FLAG\_CULL\_NON\_OPAQUE.


</dd> <dt>

<span id="RAY_FLAG_ACCEPT_FIRST_HIT_AND_END_SEARCH"></span><span id="ray_flag_accept_first_hit_and_end_search"></span>**RAY\_FLAG\_ACCEPT\_FIRST\_HIT\_AND\_END\_SEARCH**
</dt> <dd>

The first ray-primitive intersection encountered in a raytrace automatically causes **AcceptHitAndEndSearch** to be called immediately after the any hit shader, including if there is no any hit shader. 
 
The only exception is when the preceding any hit shader calls **IgnoreHit**, in which case the ray continues unaffected such that the next hit becomes another candidate to be the first hit.  For this exception to apply, the any hit shader has to actually be executed.  So if the any hit shader is skipped because the hit is treated as opaque (e.g. due to RAY\_FLAG\_FORCE\_OPAQUE or D3D12\_RAYTRACING\_GEOMETRY\_FLAG\_OPAQUE or D3D12\_RAYTRACING\_INSTANCE\_FLAG\_OPAQUE being set), then **AcceptHitAndEndSearch** is called.

If a closest hit shader is present at the first hit, it gets invoked unless RAY\_FLAG\_SKIP\_CLOSEST\_HIT\_SHADER is also present.  The one hit that was found is considered “closest”, even though other potential hits that might be closer on the ray may not have been visited.

A typical use for this flag is for shadows, where only a single hit needs to be found.


</dd> <dt>

<span id="RAY_FLAG_SKIP_CLOSEST_HIT_SHADER"></span><span id="ray_flag_skip_closest_hit_shader"></span>**RAY\_FLAG\_SKIP\_CLOSEST\_HIT\_SHADER**
</dt> <dd>

Even if at least one hit has been committed, and the hit group for the closest hit contains a closest hit shader, skip execution of that shader. 

</dd> <dt>

<span id="RAY_FLAG_CULL_BACK_FACING_TRIANGLES"></span><span id="ray_flag_cull_back_facing_triangles"></span>**RAY\_FLAG\_CULL\_BACK\_FACING\_TRIANGLES**
</dt> <dd>

Enables culling of back facing triangles. See **D3D12\_RAYTRACING\_INSTANCE\_FLAGS** for selecting which triangles are back facing, per-instance.

On instances that specify D3D12\_RAYTRACING\_INSTANCE\_FLAG\_TRIANGLE\_CULL\_DISABLE, this flag has no effect.

On geometry types other than D3D12\_RAYTRACING\_GEOMETRY\_TYPE\_TRIANGLES, this flag has no effect.

This flag is mutually exclusive with RAY\_FLAG\_CULL\_FRONT\_FACING\_TRIANGLES.


</dd> <dt>

<span id="RAY_FLAG_CULL_FRONT_FACING_TRIANGLES"></span><span id="ray_flag_cull_front_facing_trianglesag_none"></span>**RAY\_FLAG\_CULL\_FRONT\_FACING\_TRIANGLES**
</dt> <dd>

Enables culling of front facing triangles. See **D3D12\_RAYTRACING\_INSTANCE\_FLAGS** for selecting which triangles are back facing, per-instance.

On instances that specify D3D12\_RAYTRACING\_INSTANCE\_FLAG\_TRIANGLE\_CULL\_DISABLE, this flag has no effect.

On geometry types other than D3D12\_RAYTRACING\_GEOMETRY\_TYPE\_TRIANGLES, this flag has no effect.

This flag is mutually exclusive with RAY\_FLAG\_CULL\_BACK\_FACING\_TRIANGLES.


</dd> <dt>

<span id="RAY_FLAG_CULL_OPAQUE"></span><span id="ray_flag_cull_opaque"></span>**RAY\_FLAG\_CULL\_OPAQUE**
</dt> <dd>

Culls all primitives that are considered opaque based on their geometry and instance flags.

This flag is mutually exclusive with RAY\_FLAG\_FORCE\_OPAQUE, RAY\_FLAG\_FORCE\_NON\_OPAQUE, and RAY\_FLAG\_CULL\_NON\_OPAQUE.


</dd> <dt>

<span id="RAY_FLAG_CULL_NON_OPAQUE"></span><span id="ray_flag_cull_non_opaque"></span>**RAY\_FLAG\_CULL\_NON\_OPAQUE**
</dt> <dd>

Culls all primitives that are considered non-opaque based on their geometry and instance flags.

This flag is mutually exclusive with RAY\_FLAG\_FORCE\_OPAQUE, RAY\_FLAG\_FORCE\_NON\_OPAQUE, and RAY\_FLAG\_CULL\_OPAQUE.


</dd>
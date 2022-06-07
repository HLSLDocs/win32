# Register

Optional keyword for assigning a shader variable to a particular register, which uses the following syntax:

```
: register ( [shader_profile], Type#[subcomponent] )
```

### register

Required keyword.

### [shader_profile]

Optional [`shader profile`](https://docs.microsoft.com/en-us/windows/desktop/direct3dtools/dx-graphics-tools-fxc-syntax), which can be a shader target or pipeline stage symbol.

### Type#[subcomponent]

 and subcomponent declaration.

| Register Type | Register Description |
| - | - |
| b | Constant buffer |
| t | Texture and texture buffer |
| c | Buffer offset |
| s | Sampler |
| u | Unordered Access View |

<i>#</i> is the register number.

The <i>subcomponent</i> is an optional integer number.

## Remarks

You may add one or more register assignments to the same variable declaration, separated by spaces.

The <b>register</b> keyword acts the same as the [`packoffset (DirectX HLSL)`](https://docs.microsoft.com/en-us/windows/win32/direct3dhlsl/dx-graphics-hlsl-variable-packoffset) keyword.

## Examples

```
sampler myVar : register( ps_5_0, s ); 
```

```
sampler myVar : register( vs, s[8] );
```

```
sampler myVar : register( ps, s[2] ) 
              : register( ps_5_0, s[0] ) 
              : register( vs, s[8] );
```
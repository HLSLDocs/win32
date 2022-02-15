# HLSL Texture2DMSArray Object

Object for accessing a read-only 2D multi-sample texture shader resource view.  See [SRV Textures](hlsl-resource-objects.md#srv-textures).
A template argument indicates the data type to use in HLSL for the texture element.
Textures are typed resources, so a data conversion step will translate between the DXGI_FORMAT and the element type declared in HLSL.

```HLSL
// prototype
template<typename ElementType = float4> class Texture2DMSArray;

// example declarations:
Texture2DMSArray MyMSTex;
Texture2DMSArray <float4, 128> MyMSTex;
```

## Methods

| Method | Description |
| - | - |
| [GetDimensions](hlsl-method-getDimensions.md) | Gets texture size information. |
| [Load](hlsl-method-load.md) | Reads texel data without any filtering or sampling. |
| [GetSamplePosition](hlsl-method-getSamplePosition.md) | Gets the position of the specified sample. |

## Operators

| Operator | Description |
| - | - |
| [operator\[\]](hlsl-operator) | Reads texel data without any filtering or sampling in the first mip level. |
| [sample operator\[\]\[\]](hlsl-operator-sample.md) | Reads texel data without any filtering or sampling. |
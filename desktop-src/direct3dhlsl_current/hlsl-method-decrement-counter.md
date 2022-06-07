# DecrementCounter

### Signatures

Decrements the object's hidden counter.

```syntax
uint RWStructuredBuffer<ElementType>::DecrementCounter();
```

## Return Value

`uint`

The pre-decremented counter value.

## Parameters

None.

## Remarks

The bound unordered access view must have `D3D11_BUFFER_UAV_FLAG_COUNTER` set during creation for this method to work.

A structured resource can be further indexed based on the component names of the structures.

## Example
```HLSL
// None.
```

## Supported Shader Models

| Shader Model | 6.0 | 6.1 | 6.2 | 6.3 | 6.4 | 6.5 | 6.6 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Vertex | - | - | - | - | - | - | - |
| Hull | - | - | - | - | - | - | - |
| Domain | - | - | - | - | - | - | - |
| Geometry | - | - | - | - | - | - | - |
| Amplification | - | - | - | - | - | - | 1* |
| Mesh | - | - | - | - | - | - | 1* |
| Pixel | x | x | x | x | x | x | x |
| Compute | - | - | - | - | - | - | x |

| Key | Description |
| - | - |
| x | Supported |
| 1* | Supported with optional feature: `SHADER_FEATURE_DERIVATIVES_IN_MESH_AND_AMPLIFICATION_SHADERS` |

>TBD: Make optional feature into a link

Library `export` function support depends on the entry point that calls the function.
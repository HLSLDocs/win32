# HLSL StructuredBuffer

A read-only buffer, which can take a templated type that is a structure.

```HLSL
StructuredBuffer<MyStruct> mySB;
```

## Methods

| Method | Description |
| - | - |
| [GetDimensions](hlsl-method-getDimensions.md) | Gets texture size information. |
| [Load](hlsl-method-load_buffer.md) | Reads `Buffer` data. |

## Operators

| Operator | Description |
| - | - |
| [operator\[\]](hlsl-operator_buffer.md) | Reads value from buffer. |
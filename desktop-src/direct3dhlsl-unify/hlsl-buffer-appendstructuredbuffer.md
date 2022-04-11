# HLSL AppendStructuredBuffer

Output templated buffer that appears as a stream the shader may append to.

The UAV format bound to this resource needs to be created with the `DXGI_FORMAT_UNKNOWN` format.

The UAV bound to this resource must have been created with `D3D11_BUFFER_UAV_FLAG_APPEND`.

For more information about an append structured buffer, see both sections: [`append and consume`](https://docs.microsoft.com/en-us/windows/desktop/direct3d11/direct3d-11-advanced-stages-cs-resources) buffer and [`structured buffer`](https://docs.microsoft.com/en-us/windows/desktop/direct3d11/direct3d-11-advanced-stages-cs-resources).


```HLSL
// None.
```

## Methods

| Method | Description |
| - | - |
| [GetDimensions](hlsl-method-getDimensions.md) | Gets texture size information. |
| [Append](hlsl-method-append.md) | Appends a value to the end of the buffer. |
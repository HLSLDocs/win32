# RWTexture2D

Object for accessing a read-write 2D texture unordered access view.

You can prefix `RWTexture2D` objects with the storage class `globallycoherent`. This storage class causes memory barriers and syncs to flush data across the entire GPU such that other groups can see writes. Without this specifier, a memory barrier or sync will flush a UAV only within the current group.

A template argument indicates the data type to use in HLSL for the texture element.

Because a `RWTexture2D` object is a UAV-type object, its properties differ from a shader resource view (SRV)-type object, such as a [`Texture2D`](hlsl-obj-texture2D.md) object. For example, you can read from and write to a `RWTexture2D` object, but you can only read from a [`Texture2D`](hlsl-obj-texture2D.md) object.

A `RWTexture2D` object cannot use methods from a [`Texture2D`](hlsl-obj-texture2D.md) object, such as [`Sample`](hlsl-method-sample.md). However, because you can create multiple view types to the same resource, you can declare multiple texture types as a single texture in multiple shaders. For example, you can declare and use a `RWTexture2D` object as tex in a compute shader and then declare and use a [`Texture2D`](hlsl-obj-texture2D.md) object as tex in a pixel shader.

>**Note:** The runtime enforces certain usage patterns when you create multiple view types to the same resource. For example, the runtime does not allow you to have both a UAV mapping for a resource and SRV mapping for the same resource active at the same time.

```HLSL
struct PixelShaderInput
{
    float4 pos : SV_POSITION;
    float2 tex : TEXTURE;
};

Texture2D<float> tex;
float4 main(PixelShaderInput input) : SV_TARGET
{
    return tex.Sample(TextureSampler, input.tex);
}
```

## Methods

| Method | Description |
| - | - |
| [GetDimensions](hlsl-method-getDimensions.md) | Gets texture size information. |
| [Load](hlsl-method-load.md) | Reads texture data. |

## Operators

| Operator | Description |
| - | - |
| [operator\[\]](hlsl-operator.md) | Reads value from texture. |
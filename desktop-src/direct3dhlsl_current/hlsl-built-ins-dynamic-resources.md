# Built-in Dynamic Resources

Shader Model 6.6 introduces the ability to create resources from descriptors by directly indexing into the CBV_SRV_UAV heap or the Sampler heap. No root signature descriptor table mapping is required for this resource creation method, but new global root signature flags are used to indicate the use of each heap from the shader.

In HLSL, the feature is exposed as two new builtin global indexable objects: ResourceDescriptorHeap and SamplerDescriptorHeap. Indexing each results in an internal handle object that can be assigned to temporary resource or sampler objects, without requiring resource binding locations or mapping through root signature descriptor tables.

In HLSL, the CBV/SRV/UAV Descriptor Heap is referred to as the Resource Descriptor Heap.

Additional changes to existing handle patterns are introduced in this shader model to unify code paths and remove unnecessary metadata.

## ResourceDescriptorHeap and SamplerDescriptorHeap

In HLSL, two new builtin global indexable objects allow you to set local resource and sampler objects by directly indexing into the CBV_SRV_UAV (Resource) descriptor heap or the Sampler descriptor heap.

```HLSL
<resource variable> = ResourceDescriptorHeap[uint index];
<sampler variable> = SamplerDescriptorHeap[uint index];
```

`ResourceDescriptorHeap[index]` must be used to assign a local or global CBV, SRV, or UAV resource variable or function call argument.

`SamplerDescriptorHeap[index]` must be used to assign a local or global SamplerState or SamplerComparisonState variable or function call argument.

Here’s an example usage:

```hlsl
Texture2D<float4> myTexture = ResourceDescriptorHeap[texIdx];
SamplerState mySampler = SamplerDescriptorHeap[sampIdx];
float4 result = myTexture.Sample(SamplerDescriptorHeap[sampIdx], coord);
```

The object type returned by these indexing operations cannot be declared, stored, or used directly in HLSL, other than to assign a resource or sampler variable.

By default, indexing into the resource or sampler heap is considered uniform. If the index is not uniform, you must use the NonUniformResourceIndex intrinsic on the index. If the index is not uniform and NonUniformResourceIndex is not used, The result may be undefined.

Example:

```HLSL
RWByteAddressBuffer buf = ResourceDescriptorHeap[NonUniformResourceIndex(index)];
SamplerState samp = SamplerDescriptorHeap[NonUniformResourceIndex(index)];
```

Descriptors and their data looked up using ResourceDescriptorHeap and SamplerDescriptorHeap must be considered volatile. See [`Descriptor and Data Volatility`](https://microsoft.github.io/DirectX-Specs/d3d/HLSL_SM_6_6_DynamicResources.html#descriptor-and-data-volatility).
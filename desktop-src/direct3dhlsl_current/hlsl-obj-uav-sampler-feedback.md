# UAV (Unordered Access View) Sampler Feedback

An unordered access view provides similar functionality, but enables the reading and writing to the texture (or other resource) in any order.

Unordered access views are slightly more costly in terms of performance, but allow, for example, a texture to be written to at the same time that it is being read from. This enables the updated texture to be re-used by the graphics pipeline for some other purpose.

## FeedbackTexture2D

Please refer to the [`DirectX Spec`](https://microsoft.github.io/DirectX-Specs/d3d/SamplerFeedback.html)

## FeedbackTexture2DArray

Please refer to the [`DirectX Spec`](https://microsoft.github.io/DirectX-Specs/d3d/SamplerFeedback.html)
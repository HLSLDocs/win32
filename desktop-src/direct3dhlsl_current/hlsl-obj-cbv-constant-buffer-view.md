# CBV (Constant Buffer View)

Constant buffers contain shader constant data. The value of them is that the data persists, and can be accessed by any GPU shader, until it is necessary to change the data.

Typical data for a constant buffer would be world, projection and view matrices, which remain constant throughout the drawing of one frame.

Constant buffer layout should match the HLSL layout (refer to [`Packing Rules for Constant Variables`](hlsl-language-global-blocks.md#packing-rules-for-constant-variables)).

## ConstantBuffer

`ConstantBuffer` is an object representation of [`cbuffer`](hlsl-language-global-blocks.md)
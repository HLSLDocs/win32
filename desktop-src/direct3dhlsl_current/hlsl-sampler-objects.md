# SamplerObjects

Sampler objects access shader resource views for texel data.  In HLSL for DirectX 12, the application provides three objects related to texture sampler; the `Sampler`, the `SamplerState`, and the `SamplerComparisonState`.

# Sampler

The `Sampler` accesses texel data based on `u, v, w` coordinates.

The samplers indicating texture dimensionality such as `tex1d` and `tex2d` have been deprecated for DirectX 12.

# SamplerState

The `SamplerState` is an opaque object that contains `Sampler` settings.

The following constant values describe data in the `SamplerState` object.

## UVW texel addresssing

- `AddressU`
- `AddressV`
- `AddressW`

## Border Color

- `BorderColor`

## Texture Filtering

- `Filter`
- `MaxAnisotropy`

## Level of Detail

- `MaxLOD`
- `MinLOD`
- `MipLODBias`

# SamplerComparisonState

The `SamplerComparisonState` contains comparison values against the `Sampler`.  This is represented by a constant value labeled `ComparisonFunc`.
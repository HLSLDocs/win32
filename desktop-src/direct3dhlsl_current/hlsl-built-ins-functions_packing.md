# Packing

### Unpack

A set of unpack intrinsics are being added to unpack 4 signed or unsigned 8-bit values into a vector of 16 bit values or a 32 bit values. The 32 bit vector will not require the 16 bit native support.

```HLSL
int16_t4 unpack_s8s16(int8_t4_packed packedVal);        // Sign Extended
uint16_t4 unpack_u8u16(uint8_t4_packed packedVal);      // Non-Sign Extended

int32_t4 unpack_s8s32(int8_t4_packed packedVal);        // Sign Extended
uint32_t4 unpack_u8u32(uint8_t4_packed packedVal);      // Non-Sign Extended
```

### Pack Intrinsics

Pack intrinsics will pack a vector of 4 signed or unsigned values into a packed 32 bit uint32_t represented by one of the new packed datatypes. Two versions of the pack intrinsics are defined. A version which performs a datatype clamp and a version which simply drops the unused bits.

```HLSL
uint8_t4_packed pack_u8(uint32_t4 unpackedVal);         // Pack lower 8 bits, drop unused bits
int8_t4_packed pack_s8(int32_t4  unpackedVal);          // Pack lower 8 bits, drop unused bits

uint8_t4_packed pack_u8(uint16_t4 unpackedVal);         // Pack lower 8 bits, drop unused bits
int8_t4_packed pack_s8(int16_t4  unpackedVal);          // Pack lower 8 bits, drop unused bits

uint8_t4_packed pack_clamp_u8(int32_t4  unpackedVal);   // Pack and Clamp [0, 255]
int8_t4_packed pack_clamp_s8(int32_t4  unpackedVal);    // Pack and Clamp [-128, 127]

uint8_t4_packed pack_clamp_u8(int16_t4  unpackedVal);   // Pack and Clamp [0, 255]
int8_t4_packed pack_clamp_s8(int16_t4  unpackedVal);    // Pack and Clamp [-128, 127]
```

#### Example

Dequantize linear equation is defined dequantizeValue = (X - Z_p) * S

```HLSL
int16_t4 x0 = unpack_u8s16(Read())
int16_t4 x1 = unpack_u8s16(Read())

int16_t z0 = unpack_u8s16(Read()).x
int16_t z1 = unpack_u8s16(Read()).x
int32_t z_output = unpack_u8s32(Read()).x

float s0 = Read()
float s1 = Read()
float s2 = Read()

float s_output = (s0 * s1)/s2;

int16_t4 x2 = x0 - z0.xxxx;
int16_t4 x3 = x1 - z1.xxxx;

int32_t4 x_mul = (int32_t4)x2 * (int32_t4)x3;

float4 x_float = x_mul * s_output.xxxx;
int32_t4 x_output = round(x_float);

x_output = x_output + z_output.xxxx;

uint8_t4_packed y = pack_clamp_u8(x_output);

write(y);
```
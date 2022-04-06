# Operator[] (Buffer)

Reads value from buffer.

RW objects can write values to the buffer object.

Operator signatures vary per supported Buffer Object type.

```syntax
uint Buffer::Operator[](
    in uint pos );

ElementType StructuredBuffer<ElementType>::Operator[](
    in uint pos );

uint RWBuffer::Operator[](
    in uint pos );

ElementType RWStructuredBuffer<ElementType>::Operator[](
    in uint pos );
```

<b>Example</b>

```HLSL
// None.
```

## Return Value

The `Buffer` and `RWBuffer` objects returns `uint` values.  The dimensionality of the return value depends on the method signature.

The buffer objects `StructuredBuffer` and `RWStructuredBuffer` returns a mandatory templated value.
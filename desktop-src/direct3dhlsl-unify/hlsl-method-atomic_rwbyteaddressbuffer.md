# Atomic Methods (RWByteAddressBuffer) 

## InterlockedAdd

Adds the value, atomically.

```syntax
void InterlockedAdd(
    in  uint    dest,
    in  uint    value,
    out uint    original_value );
```

## InterlockedAnd

Ands the value, atomically.

```syntax
void InterlockedAnd(
    in  uint    dest,
    in  uint    value,
    out uint    original_value );
```

## InterlockedCompareExchange

Compares the input to the comparison value and exchanges the result, atomically.

Atomically compares the value in dest to compare_value, stores value in dest if the values match, returns the original value of dest in original_value.

```syntax
void InterlockedCompareExchange(
    in  uint    dest,
    in  uint    compare_value,
    in  uint    value,
    out uint    original_value );
```

## InterlockedCompareStore

Compares the input to the comparison value, atomically.

```syntax
void InterlockedCompareStore(
    in  uint    dest,
    in  uint    compare_value,
    in  uint    value );
```

## InterlockedExchange

Exchanges a value, atomically.

```syntax
void InterlockedExchange(
    in  uint    dest,
    in  uint    value,
    out uint    original_value );
```

## InterlockedMax

Finds the maximum value, atomically.

```syntax
void InterlockedMax(
    in  uint    dest,
    in  uint    value,
    out uint    original_value );
```

## InterlockedMin

Finds the minimum value, atomically.

```syntax
void InterlockedMin(
    in  uint    dest,
    in  uint    value,
    out uint    original_value );
```

## InterlockedOr

Performs an atmoic `OR` on the value.

```syntax
void InterlockedOr(
    in  uint    dest,
    in  uint    value,
    out uint    original_value );
```

## InterlockedXor

Performs an atomic `XOR` on the value.

```syntax
void InterlockedXor(
    in  uint    dest,
    in  uint    value,
    out uint    original_value );
```

| Parameter | Description |
| - | - |
| in [`uint dest`](#uint-dest) | The destination address. |
| in [`uint compare_value`](#uint-compare_value) | The comparison value. |
| in [`uint value`](#uint-value) | The input value. |
| out [`uint original_value`](#uint-original_value) | The original value. |

<b>Example</b>

```HLSL
// None.
```

## Return Value

None.

## Parameters

### `uint dest`

The destination address.

### `uint compare_value`

The comparison value.

### `uint value`

The input value.

### `uint original_value`

The original value.

## Remarks

These operation can be performed only on `int` or `uint` typed resources and shared memory variables. There are three possible uses for these functions. The first is when R is a shared memory variable type. In this case, these functions perform atomic operations of value to the shared memory register referenced by dest. The second scenario is when R is a resource variable type. In this scenario, the functions perform an atomic operation of the value to the resource location referenced by dest. Finally, the third scenario is when R is a local variable type. In this scenario, the function reduces to the operation of the value of dest and value, stored in dest. The overloaded function has an additional output variable which will be set to the original value of dest. This overloaded operation is only available when R is readable and writable.

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
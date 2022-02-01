# Texture2DMSArray.GetSamplePosition Method

Reference

## Definition

Returns the sample position for the sample index provided.

#### In this article

*  [Definition](#definition)
*  [Overloads](#overloads)

## Overloads

| Method | Description |
| ------ | ----------- |
| [GetSamplePosition(int)](#GetSamplePosition-int) | Returns the sample position for the sample index provided. |

## GetSamplePosition(int) {#GetSamplePosition-int}

Returns the sample position for the sample index provided.

```HLSL
float2 GetSamplePosition(
  in int sampleindex
);
```

### Parameters
<i>sampleIndex</i> [in] int
The zero-based index of a sample location.

### Returns
Type: float2

A sample location.
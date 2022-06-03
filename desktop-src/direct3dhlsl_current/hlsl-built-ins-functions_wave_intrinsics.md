# Wave Intrinsics

### QuadReadAcrossDiagonal function

Returns the specified local value which is read from the diagonally opposite lane in this quad.

#### Syntax


``` syntax
<type> QuadReadAcrossDiagonal(
   <type> localValue
);
```



#### Parameters

<dl> <dt>

*localValue* 
</dt> <dd>

The requested type.

</dd> </dl>

#### Return value

The specified local value which is read from the diagonally opposite lane in this quad.

#### Remarks

For more information on quads, refer to [Overview of Shader Model 6](hlsl-shader-model-6-0-features-for-direct3d-12.md).

This function is supported from shader model 6.0 only in pixel and compute shaders.

### QuadReadLaneAt function

Returns the specified source value from the lane identified by the lane ID within the current quad.

#### Syntax


``` syntax
<type> QuadReadLaneAt(
   <type> sourceValue,
   uint   quadLaneID  
);
```



#### Parameters

<dl> <dt>

*sourceValue* 
</dt> <dd>

The requested type.

</dd> <dt>

*quadLaneID* 
</dt> <dd>

The lane ID; this will be a value from 0 to 3.

</dd> </dl>

#### Return value

The specified source value. The result of this function is uniform across the quad. If the source lane is inactive, the results are undefined.

#### Remarks

For more information on quads, refer to [Overview of Shader Model 6](hlsl-shader-model-6-0-features-for-direct3d-12.md).

This function is supported from shader model 6.0 only in pixel and compute shaders.

### QuadReadAcrossX function

Returns the specified local value read from the other lane in this quad in the X direction.

#### Syntax

``` syntax
<type> QuadReadAcrossX(
   <type> localValue
);
```

#### Parameters

<dl> <dt>

*localValue* 
</dt> <dd>

The requested type.

</dd> </dl>

#### Return value

The specified local value. If the source lane is inactive, the results are undefined.

#### Remarks

For more information on quads, refer to [Overview of Shader Model 6](hlsl-shader-model-6-0-features-for-direct3d-12.md).

This function is supported from shader model 6.0 only in pixel and compute shaders.

### QuadReadAcrossY function

Returns the specified source value read from the other lane in this quad in the Y direction.

#### Syntax

``` syntax
<type> QuadReadAcrossY(
   <type> localValue
);
```

#### Parameters

<dl> <dt>

*localValue* 
</dt> <dd>

The requested type.

</dd> </dl>

#### Return value

The specified source value. If the source lane is inactive, the results are undefined.

#### Remarks

For more information on quads, refer to [Overview of Shader Model 6](hlsl-shader-model-6-0-features-for-direct3d-12.md).

This function is supported from shader model 6.0 only in pixel and compute shaders.

### WaveActiveAllEqual function

Returns true if the expression is the same for every active lane in the current wave (and thus uniform across it).

#### Syntax


``` syntax
bool WaveActiveAllEqual(
   <type> expr
);
```



#### Parameters

<dl> <dt>

*expr* 
</dt> <dd>

The expression to evaluate.

</dd> </dl>

#### Return value

True if the expression is the same for every active lane in the current wave.

#### Remarks

This function is supported from shader model 6.0 in all shader stages. 

### WaveActiveBitAnd function

Returns the bitwise AND of all the values of the expression across all active lanes in the current wave and replicates it back to all active lanes.

#### Syntax


``` syntax
<int_type> WaveActiveBitAnd(
   <int_type> expr
);
```



#### Parameters

<dl> <dt>

*expr* 
</dt> <dd>

The expression to evaluate.

</dd> </dl>

#### Return value

The bitwise AND value.

#### Remarks

This function is supported from shader model 6.0 in all shader stages. 

### WaveActiveBitOr function

Returns the bitwise OR of all the values of the expression across all active lanes in the current wave and replicates it back to all active lanes.

#### Syntax

``` syntax
<int_type> WaveActiveBitOr(
   <int_type> expr
);
```

#### Parameters

<dl> <dt>

*expr* 
</dt> <dd>

The expression to evaluate.

</dd> </dl>

#### Return value

The bitwise OR value.

#### Remarks

This function is supported from shader model 6.0 in all shader stages. 

### WaveActiveBitXor function

Returns the bitwise XOR of all the values of the expression across all active lanes in the current wave and replicates it back to all active lanes.

#### Syntax

``` syntax
<int_type> WaveActiveBitXor(
   <int_type> expr
);
```

#### Parameters

<dl> <dt>

*expr* 
</dt> <dd>

The expression to evaluate.

</dd> </dl>

#### Return value

The bitwise XOR value.

#### Remarks

This function is supported from shader model 6.0 in all shader stages. 

### WaveActiveCountBits function

Counts the number of boolean variables which evaluate to true across all active lanes in the current wave, and replicates the result to all lanes in the wave.

#### Syntax


``` syntax
uint WaveActiveCountBits(
   bool bBit
);
```



#### Parameters

<dl> <dt>

*bBit* 
</dt> <dd>

The boolean variables to evaluate. Providing an explicit true Boolean value returns the number of active lanes.

</dd> </dl>

#### Return value

The number of lanes for which the boolean variable evaluates to true, across all active lanes in the current wave.

#### Remarks

This function is supported from shader model 6.0 in all shader stages. 



 

#### Examples

This can be implemented more efficiently than a full WaveActiveSum, as described in the following example:

``` syntax
result = WaveActiveCountBits( WaveActiveBallot( bBit ) );
```

### WaveActiveMax function

Returns the maximum value of the expression across all active lanes in the current wave and replicates it back to all active lanes.

#### Syntax

``` syntax
<type> WaveActiveMax(
   <type> expr
);
```

#### Parameters

<dl> <dt>

*expr* 
</dt> <dd>

The expression to evaluate.

</dd> </dl>

#### Return value

The maximum value.

#### Remarks

The order of operations is undefined.

This function is supported from shader model 6.0 in all shader stages. 



 

#### Examples

``` syntax
 float3 maxPos = WaveActiveMax( myPoint.position );
    BoundingBox.max = max( maxPos, BoundingBox.max );
```

### WaveActiveMin function

Returns the minimum value of the expression across all active lanes in the current wave replicates it back to all active lanes.

#### Syntax

``` syntax
<type> WaveActiveMin(
   <type> expr
);
```

#### Parameters

<dl> <dt>

*expr* 
</dt> <dd>

The expression to evaluate.

</dd> </dl>

#### Return value

The minimum value.

#### Remarks

The order of operations is undefined.

This function is supported from shader model 6.0 in all shader stages. 



 

#### Examples

``` syntax
 float3 minPos = WaveActiveMin( myPoint.position );
    BoundingBox.min = min( minPos, BoundingBox.min );
```

### WaveActiveProduct function

Multiplies the values of the expression together across all active lanes in the current wave and replicates it back to all active lanes.

#### Syntax

``` syntax
<type> WaveActiveProduct(
   <type> expr
);
```

#### Parameters

<dl> <dt>

*expr* 
</dt> <dd>

The expression to evaluate.

</dd> </dl>

#### Return value

The product value.

#### Remarks

The order of operations is undefined.

This function is supported from shader model 6.0 in all shader stages.

### WaveActiveSum function

Sums up the value of the expression across all active lanes in the current wave and replicates it to all lanes in the current wave.

#### Syntax

``` syntax
<type> WaveActiveSum(
   <type> expr
);
```

#### Parameters

<dl> <dt>

*expr* 
</dt> <dd>

The expression to evaluate.

</dd> </dl>

#### Return value

The sum value.

#### Remarks

The order of operations is undefined.

This function is supported from shader model 6.0 in all shader stages. 



 

#### Examples

``` syntax
float3 total = WaveActiveSum( position ); // sum positions in wave
float3 center = total/count;           // compute average of these positions
```

### WaveActiveAllTrue function

Returns true if the expression is true in all active lanes in the current wave.

#### Syntax

``` syntax
bool WaveActiveAllTrue(
   bool expr
);
```

#### Parameters

<dl> <dt>

*expr* 
</dt> <dd>

The boolean expression to evaluate.

</dd> </dl>

#### Return value

True if the expression is true in all lanes.

#### Remarks

This function is supported from shader model 6.0 in all shader stages. 

### WaveActiveAnyTrue function

Returns true if the expression is true in any of the active lanes in the current wave.

#### Syntax

``` syntax
bool WaveActiveAnyTrue(
   bool expr
);
```

#### Parameters

<dl> <dt>

*expr* 
</dt> <dd>

The boolean expression to evaluate.

</dd> </dl>

#### Return value

True if the expression is true in any lane.

#### Remarks

This function is supported from shader model 6.0 in all shader stages. 

### WaveActiveBallot function

Returns a uint4 containing a bitmask of the evaluation of the Boolean expression for all active lanes in the current wave. 

#### Syntax

``` syntax
uint4 WaveBallot(
   bool expr
);
```

#### Parameters

<dl> <dt>

*expr* 
</dt> <dd>

The boolean expression to evaluate.

</dd> </dl>

#### Return value

A uint4 containing a bitmask of the evaluation of the Boolean expression for all active lanes in the current wave. The least-significant bit corresponds to the lane with index zero. The bits corresponding to inactive lanes will be zero. The bits that are greater than or equal to [**WaveGetLaneCount**](wavegetlanecount.md) will be zero.

#### Remarks

Different GPUs have different SIMD processor widths (lane counts). Most of these **WaveXXX** functions are able to operate at level of abstraction where SIMD machine width is concealed. To maximize portability of code across GPUs, use the intrinsics that don’t rely on machine width. For example, use:

``` syntax
uint result = WaveActiveCountBits( bBit );
```

Instead of:

``` syntax
uint result = countbits( WaveActiveBallot( bBit ) );
```

This function is supported from shader model 6.0 in all shader stages. 


### WaveGetLaneCount function

Returns the number of lanes in a wave on this architecture.

#### Syntax

``` syntax
uint WaveGetLaneCount(void);
```

#### Parameters

This function has no parameters.

#### Return value

The result will be between 4 and 128, and includes all waves: active, inactive, and/or helper lanes. The result returned from this function may vary significantly depending on the driver implementation.

#### Remarks

This function is supported from shader model 6.0 in all shader stages. 



 

#### Examples

``` syntax
 uint laneCount = WaveGetLaneCount();    // number of lanes in wave
```
 

#### Examples

``` syntax
// get a bitwise representation of the number of currently active lanes:
uint4 waveBits = WaveActiveBallot( true ); // convert to bits 
```

### WaveGetLaneIndex function

Returns the index of the current lane within the current wave.

#### Syntax

``` syntax
uint WaveGetLaneIndex(void);
```

#### Parameters

This function has no parameters.

#### Return value

The current lane index. The result will be between 0 and the result returned from [**WaveGetLaneCount**](wavegetlanecount.md).

#### Remarks

This function is supported from shader model 6.0 in all shader stages. 

### WaveIsFirstLane function

Returns true only for the active lane in the current wave with the smallest index.

#### Syntax


``` syntax
bool WaveIsFirstLane(void);
```



#### Parameters

This function has no parameters.

#### Return value

True only for the active lane in the current wave with the smallest index.

#### Remarks

This function can be used to identify operations that are to be executed only once per wave.

This function is supported from shader model 6.0 in all shader stages. 



 

#### Examples

``` syntax
 if ( WaveIsFirstLane() )
{
    . . . // once per-wave code
}
```

### WavePrefixCountBits function

Returns the sum of all the specified boolean variables set to true across all active lanes with indices smaller than the current lane.

#### Syntax


``` syntax
uint WavePrefixCountBits(
   bool bBit
);
```



#### Parameters

<dl> <dt>

*bBit* 
</dt> <dd>

The specified boolean variables.

</dd> </dl>

#### Return value

The sum of all the specified Boolean variables set to true across all active lanes with indices smaller than the current lane.

#### Remarks

This function is supported from shader model 6.0 in all shader stages. 



 

#### Examples

The following code describes how to implement a compacted write to an ordered stream where the number of elements written per lane is either 1 or 0.

``` syntax
bool bDoesThisLaneHaveAnAppendItem = <expr>;
// compute number of items to append for the whole wave
uint laneAppendOffset = WavePrefixCountBits( bDoesThisLaneHaveAnAppendItem );
uint appendCount = WaveActiveCountBits( bDoesThisLaneHaveAnAppendItem);
// update the output location for this whole wave
uint appendOffset;
if ( WaveIsFirstLane () )
{
    // this way, we only issue one atomic for the entire wave, which reduces contention
    // and keeps the output data for each lane in this wave together in the output buffer
    InterlockedAdd(bufferSize, appendCount, appendOffset);
}
appendOffset = WaveReadLaneFirst( appendOffset ); // broadcast value
appendOffset += laneAppendOffset; // and add in the offset for this lane
buffer[appendOffset] = myData; // write to the offset location for this lane
```

### WavePrefixProduct function

Returns the product of all of the values in the active lanes in this wave with indices less than this lane.

#### Syntax

``` syntax
<type> WavePrefixProduct(
   <type> value
);
```

#### Parameters

*value* 

The value to multiply.

#### Return value

The product of all the values.

#### Remarks

The order of operations on this routine cannot be guaranteed. So, effectively, the \[precise\] flag is ignored within it.

A postfix product can be computed by multiplying the prefix product by the current lane's value.

Note that the active lane with the lowest index will always receive a 1 for its prefix product.

This function is supported from shader model 6.0 in all shader stages. 

#### Examples

```hlsl
uint numToMultiply = 2;
uint prefixProduct = WavePrefixProduct( numToMultiply );
```

On a machine with a wave size of 8, and all lanes active except lanes 0 and 4, the following values would be returned from WavePrefixProduct.

| lane index | status   | prefixProduct | 
|------------|----------|---------------|
| 0          | inactive | n/a           |
| 1          | active   | = 1           |
| 2          | active   | = 1\*2        |
| 3          | active   | = 1\*2\*2     |
| 4          | inactive | n/a           |
| 5          | active   | = 1\*2\*2\*2       |
| 6          | active   | = 1\*2\*2\*2\*2    |
| 7          | active   | = 1\*2\*2\*2\*2\*2 |

### WavePrefixSum function

Returns the sum of all of the values in the active lanes with smaller indices than this one.

#### Syntax

``` syntax
<type> WavePrefixSum(
   <type> value
);
```

#### Parameters

*value* 

The value to sum up.

#### Return value

The sum of the values.

#### Remarks

The order of operations on this routine cannot be guaranteed. So, effectively, the \[precise\] flag is ignored within it.

A postfix sum can be computed by adding the prefix sum to the current lane's value.

Note that the active lane with the lowest index will always receive a 0 for its prefix sum.

This function is supported from shader model 6.0 in all shader stages. 

#### Examples

```hlsl
uint numToSum = 2;
uint prefixSum = WavePrefixSum( numToSum );
```

On a machine with a wave size of 8, and all lanes active except lanes 0 and 4, the following values would be returned from WavePrefixSum.

| lane index | status   | prefixSum     | 
|------------|----------|---------------|
| 0          | inactive | n/a           |
| 1          | active   | = 0           |
| 2          | active   | = 0+2         |
| 3          | active   | = 0+2+2       |
| 4          | inactive | n/a           |
| 5          | active   | = 0+2+2+2     |
| 6          | active   | = 0+2+2+2+2   |
| 7          | active   | = 0+2+2+2+2+2 |

### WaveReadLaneFirst function

Returns the value of the expression for the active lane of the current wave with the smallest index.

#### Syntax

``` syntax
<type> WaveReadLaneFirst(
   <type> expr
);
```

#### Parameters

<dl> <dt>

*expr* 
</dt> <dd>

The expression to evaluate.

</dd> </dl>

#### Return value

The resulting value is uniform across the wave.

#### Remarks

This function is supported from shader model 6.0 in all shader stages. 

### WaveReadLaneAt function

Returns the value of the expression for the given lane index within the specified wave.

#### Syntax

``` syntax
<type> WaveReadLaneAt(
   <type> expr,
   uint laneIndex
);
```

#### Parameters

<dl> <dt>

*expr* 
</dt> <dd>

The expression to evaluate.

</dd> <dt>

*laneIndex* 
</dt> <dd>

The index of the lane for which the *expr* result will be returned.

</dd> </dl>

#### Return value

The resulting value is the result of *expr*. It will be uniform if *laneIndex* is uniform.

#### Remarks

This function is effectively a broadcast of the value in the *laneIndex*'th lane.

This function is supported from shader model 6.0 in all shader stages.
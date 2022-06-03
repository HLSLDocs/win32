# Memory Barriers and Thread Synchronization

### GroupMemoryBarrier function

Blocks execution of all threads in a group until all group shared accesses have been completed.

#### Syntax

``` syntax
void GroupMemoryBarrier(void);
```

#### Parameters

This function has no parameters.

#### Return value

This function does not return a value.

### GroupMemoryBarrierWithGroupSync function

Blocks execution of all threads in a group until all group shared accesses have been completed and all threads in the group have reached this call.

#### Syntax

``` syntax
void GroupMemoryBarrierWithGroupSync(void);
```

#### Parameters

This function has no parameters.

#### Return value

This function does not return a value.

### AllMemoryBarrier function

Blocks execution of all threads in a group until all memory accesses have been completed.

#### Syntax

``` syntax
void AllMemoryBarrier(void);
```

#### Parameters

This function has no parameters.

#### Return value

This function does not return a value.

#### Remarks

A memory barrier guarantees that outstanding memory operations have completed. Threads are synchronized at GroupSync barriers. This may stall a thread or threads if memory operations are in progress.

### AllMemoryBarrierWithGroupSync function

Blocks execution of all threads in a group until all memory accesses have been completed and all threads in the group have reached this call.

#### Syntax

``` syntax
void AllMemoryBarrierWithGroupSync(void);
```

#### Parameters

This function has no parameters.

#### Return value

This function does not return a value.

#### Remarks

A memory barrier guarantees that outstanding memory operations have completed. Threads are synchronized at GroupSync barriers. This may stall a thread or threads if memory operations are in progress.

### DeviceMemoryBarrier function

Blocks execution of all threads in a group until all device memory accesses have been completed.

#### Syntax

``` syntax
void DeviceMemoryBarrier(void);
```

#### Parameters

This function has no parameters.

#### Return value

This function does not return a value.

### DeviceMemoryBarrierWithGroupSync function

Blocks execution of all threads in a group until all device memory accesses have been completed and all threads in the group have reached this call.

#### Syntax

``` syntax
void DeviceMemoryBarrierWithGroupSync(void);
```

#### Parameters

This function has no parameters.

#### Return value

This function does not return a value.
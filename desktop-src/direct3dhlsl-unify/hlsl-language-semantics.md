# Semantics

A semantic is a string attached to a shader input or output that conveys information about the intended use of a parameter. Semantics are required on all variables passed between shader stages. The syntax for adding a semantic to a shader variable is shown here (`Variable Syntax (DirectX HLSL)`).

In general, data passed between pipeline stages is completely generic and is not uniquely interpreted by the system; arbitrary semantics are allowed which have no special meaning. Parameters (in Direct3D 10 and later) which contain these special semantics are referred to as `System-Value Semantics`.
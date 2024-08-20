---
title: Enums
layout: default
nav_order: 5
---
# Enums

Any enums exposed to Unreal Engine via UProperty/UEnum/UFunction-parameter must have a underlying type of byte. It's a restriction set by the engine with enums used in Blueprint. 

If you don't need to expose them, you can have any valid underlying type.

```c#
[UEnum]
public enum EMyEnum : byte
{
    Value1 = 0,
    Value2 = 1,
}
```
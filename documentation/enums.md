---
description: >-
  Any enums exposed to Unreal Engine via UProperty/UEnum/UFunction-parameter
  must have a underlying type of byte. It’s a restriction set by the engine with
  enums used in Blueprint.
---

# Enums

```csharp
[UEnum]
public enum EMyEnum : byte
{
    Value1 = 0,
    Value2 = 1,
}
```

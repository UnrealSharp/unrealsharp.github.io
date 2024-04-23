---
title: Enums
layout: default
---

```c#
[UEnum]
public enum MyEnum : byte
{
    Value1 = 0,
    Value2 = 1,
}
```

The enum must have a underlying type of byte. It's a Unreal Engine restriction with reflection enums.
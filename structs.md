---
title: Structs
layout: default
nav_order: 3
---
# Structs 

```c#
using UnrealSharp.Attributes;

namespace MyNameSpace;

[UStruct]
public struct MyStruct
{
    [UProperty(PropertyFlags.BlueprintReadOnly)]
    public int MyInt;
    
    [UProperty(PropertyFlags.BlueprintReadOnly)]
    public float MyFloat;
    
    [UProperty(PropertyFlags.BlueprintReadOnly)]
    public string MyString;
    
    [UProperty(PropertyFlags.BlueprintReadOnly)]
    public bool MyBool;
    
    [UProperty(PropertyFlags.BlueprintReadOnly)]
    public Object MyObject;
}
```

Members in a Unreal Engine exposed struct through UStruct, needs to be a field. If not exposed, none of that applies.
---
title: Structs
layout: default
nav_order: 3
---


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

Members in a struct needs to be field.
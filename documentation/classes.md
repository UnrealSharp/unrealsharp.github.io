---
description: >-
  To expose C# classes to Unreal Engine, they must be marked with the [UClass]
  attribute and inherit from a UObject, such as AActor, UActorComponent, or any
  other subclass.
layout:
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# Classes

```csharp
[UClass]
public class AMyShowcaseClass : AActor
{
    protected override void BeginPlay()
    {
        base.BeginPlay();
    }
}

```

---
description: >-
  To make a C# class visible to Unreal Engine’s reflection system (and therefore
  Blueprint and the gameplay framework), the class must:
---

# Classes

* Be marked with the `[UClass]` attribute.
* **Inherit from a valid** `UObject`**-based type**, such as `AActor`, `UActorComponent`, `USceneComponent`, or any other Unreal class exposed through UnrealSharp.
* Be declared as a `partial` **class**, so UnrealSharp can generate interop code from the source generator.

```csharp
[UClass]
public partial class AMyShowcaseClass : AActor
{
    public override void BeginPlay()
    {
        base.BeginPlay();
    }
}

```

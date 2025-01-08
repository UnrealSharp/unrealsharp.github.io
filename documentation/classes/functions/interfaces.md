---
description: Exposing C# Interfaces to Unreal
---

# Interfaces

To create an interface in UnrealSharp, the interface must be prefixed with I, and use the UInterface attribute.

```csharp
[UInterface]
public interface IInteractable
{
    [UFunction(FunctionFlags.BlueprintEvent)]
    public bool OnInteract();

    [UFunction(FunctionFlags.BlueprintEvent)]
    public bool StopInteract();
}
```

The UFunction for interface methods can only be defined in their interface. You can’t UFunction an implementation of the interface method.

---
description: Exposing C# Interfaces to Unreal
---

# Interfaces

To create an interface in UnrealSharp, the interface must be prefixed with I, and use the UInterface attribute.

```csharp
[UInterface]
public partial interface IInteractable
{
    [UFunction(FunctionFlags.BlueprintEvent)]
    public bool OnInteract();

    [UFunction(FunctionFlags.BlueprintEvent)]
    public bool StopInteract();
}
```

The UFunction for interface methods can only be defined in their interface. You can’t UFunction an implementation of the interface method.

### C++/C# Implemented Interfaces&#x20;

Calling interfaces that are implemented in C++/C#, you can just cast to the interface and call the function.

```csharp
void ExecuteNativeImplementedInterface(AActor managedImplementedInterface)
{
    if (managedImplementedInterface is IMyShowcaseInterface showcase)
    {
        showcase.OnInterfaceTriggered();
    }
}
```

### Blueprint Implemented Interfaces

If you have a C++/C# interface implemented only in Blueprints. C# won't recognize it when you try to cast it. Instead U# has `AsInterface<>()` which will create a wrapper object that you can use to call BP-implemented interfaces as seen below.

```csharp
[UClass]
public partial class AShowcaseActor : AActor
{
    [UFunction(FunctionFlags.BlueprintCallable)]
    public void ExecuteBlueprintInterface(AActor targetObject)
    {
        IMyShowcase? showcase = targetObject.AsInterface<IMyShowcase>();
        
        if (showcase != null)
        {
            showcase.OnInterfaceTriggered();
        }
    }
}
```

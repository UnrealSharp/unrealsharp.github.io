---
description: >-
  To expose C# class members to Unreal Engine so they can participate in
  reflection, serialization, Blueprint access, and editor details panels they
  must:
---

# Properties

* Be marked with the **`[UProperty]`** attribute.
* Be defined as C# properties with getters and/or setters.
* Be declared as **`partial`**, allowing UnrealSharp to generate the required interop and reflection code.<br>

Getters and setters are fully usable and behave like normal C# properties, while still being visible to Unreal.<br>

Below is an example demonstrating common property types

{% code fullWidth="false" %}
```csharp
[UClass]
public partial class AMyShowcaseClass : AActor
{
    // Declares a default component which is automatically created and assigned
    // when the actor is constructed. Marking it as RootComponent makes it the root.
    [UProperty(DefaultComponent = true, RootComponent = true)]
    public partial UStaticMeshComponent MyMesh { get; set; }
 
    // Exposes a map to the editor and Blueprint.
    // Note: TMap itself cannot currently be constructed with 'new' in C#.
    [UProperty(PropertyFlags.EditAnywhere | PropertyFlags.BlueprintReadWrite)]
    public partial TMap<int, string> MyMap { get; set; }

    [UProperty(PropertyFlags.EditAnywhere | PropertyFlags.BlueprintReadWrite)]
    public partial TWeakObjectPtr<AMyShowcaseClass> MyWeakObject { get; set; }

    public override void BeginPlay()
    {
        base.BeginPlay();

        PrintString("BeginPlay called!");

        // Assuming the enginehas initialized MyMap for you,
        // you can use it like a normal map:
        MyMap.Add(1, "First Value");
        MyMap.Add(2, "Second Value");

        MyWeakObject = this;

        UpdateMapWithKey(2, "Updated Second Value");
    }    
}
```
{% endcode %}

At the moment:

* **You cannot directly construct certain Unreal container types** like `TArray<>` and `TMap<>` in managed code using `new TArray<>()` or `new TMap<>()`.
* For Unreal-exposed properties using `TArray` / `TMap`, the underlying instance is created by the engine / interop layer. You can read/write to them (e.g., `MyMap.Add(...)`), but not manually allocate them yourself.
* If you need **purely managed collections** that you control entirely from C#, prefer:
  * `IList<T>` for array-like data
  * `IDictionary<TKey, TValue>` for maps

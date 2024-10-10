---
description: >-
  Exposing C# members to Unreal Engine, they must be marked with the [UProperty]
  attribute and be defined as properties.
---

# Properties

{% hint style="warning" %}
Getters and Setters currently cannot be used as the weaver injects into them.
{% endhint %}

{% code fullWidth="false" %}
```csharp
[UClass]
public class AMyShowcaseClass : AActor
{
    [UProperty(DefaultComponent = true, RootComponent = true)]
    public UStaticMeshComponent MyMesh { get; set; }
 
    [UProperty(PropertyFlags.EditAnywhere | PropertyFlags.BlueprintReadWrite)]
    public TMap<int, string> MyMap { get; set; }

    [UProperty(PropertyFlags.EditAnywhere | PropertyFlags.BlueprintReadWrite)]
    public TWeakObjectPtr<AMyShowcaseClass> MyWeakObject { get; set; }

    protected override void BeginPlay()
    {
        base.BeginPlay();

        PrintString("BeginPlay called!");

        MyMap.Add(1, "First Value");
        MyMap.Add(2, "Second Value");

        MyWeakObject = this;

        UpdateMapWithKey(2, "Updated Second Value");
    }    
}
```
{% endcode %}


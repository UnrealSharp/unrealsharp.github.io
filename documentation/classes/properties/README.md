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
public partial class AMyShowcaseClass : AActor
{
    [UProperty(DefaultComponent = true, RootComponent = true)]
    public partial UStaticMeshComponent MyMesh { get; set; }
 
    [UProperty(PropertyFlags.EditAnywhere | PropertyFlags.BlueprintReadWrite)]
    public partial  TMap<int, string> MyMap { get; set; }

    [UProperty(PropertyFlags.EditAnywhere | PropertyFlags.BlueprintReadWrite)]
    public partial TWeakObjectPtr<AMyShowcaseClass> MyWeakObject { get; set; }

    public override void BeginPlay()
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

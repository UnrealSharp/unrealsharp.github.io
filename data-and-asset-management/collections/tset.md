---
description: >-
  Sets are collections that have unique elements and specific operations such as
  union, intersections and differences.
---

# TSet

Example of using a TSet as a UProperty

```csharp
[UClass]
public partial class AMyShowcaseClass : AActor
{
    [UProperty(PropertyFlags.EditAnywhere | PropertyFlags.BlueprintReadWrite)]
    public partial TSet<int> MySet { get; set; }

    public override void BeginPlay()
    {
        base.BeginPlay();

        MySet.Add(1);
        MySet.Add(2);
    }    
}
```

TMap can also be represented as an ISet inside of a UFunction

```csharp
[UFunction(FunctionFlags.BlueprintCallable)]
public void TestSet(ISet<int> MySet)
{
    PrintString($"Set Count: {MySet.Count}");
}
```

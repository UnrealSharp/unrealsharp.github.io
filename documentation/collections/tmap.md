---
description: >-
  TMaps are defined by two types, a key type and a value type, which are stored
  as associated pairs in the map.
---

# TMap

Example of using a TMap as a UProperty

```csharp
[UClass]
public class AMyShowcaseClass : AActor
{
    [UProperty(PropertyFlags.EditAnywhere | PropertyFlags.BlueprintReadWrite)]
    public TMap<int, string> MyMap { get; set; }

    [UProperty(PropertyFlags.EditAnywhere | PropertyFlags.BlueprintReadWrite)]
    protected override void BeginPlay()
    {
        base.BeginPlay();

        MyMap.Add(1, "First Value");
        MyMap.Add(2, "Second Value");

        UpdateMapWithKey(2, "Updated Second Value");
    }    
}
```

TMap can also be represented as an IDictionary inside of a UFunction

```csharp
[UFunction(FunctionFlags.BlueprintCallable)]
public void TestList(IDictionary<string, string> MyDict)
{
    PrintString($"Dictionary Key Count: {MyDict.Keys.Count}");
}
```

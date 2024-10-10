---
description: Basic Array that is used in Unreal
---

# TArray

Example of setting up an array and adding to it.

```csharp
[UClass]
public class AMyShowcaseClass : AActor
{ 
    [UProperty(PropertyFlags.EditAnywhere | PropertyFlags.BlueprintReadWrite)]
    public TArray<int> Array { get; set; }

    protected override void BeginPlay()
    {
        base.BeginPlay();

        Array.Add(1);
    }    
}
```

TArray can also be represented as an IList inside of a UFunction

```csharp
[UFunction(FunctionFlags.BlueprintCallable)]
public void TestList(IList<string> myList)
{
    PrintString($"List Count: {myList.Count}");
}
```


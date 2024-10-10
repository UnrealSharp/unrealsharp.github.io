---
description: Exposing your C# methods to Unreal functions
---

# Functions

You can expose your C# methods to unreal using the \[UFunction] Attribute

```csharp
[UFunction(FunctionFlags.BlueprintCallable)]
public void TestFunction()
{
    PrintString($"List Count: {myList.Count}");
}
```

---
description: Exposing your C# methods to Unreal functions
---

# Functions

You can expose your C# methods to unreal using the `UFunction` Attribute

```csharp
// Can be called from BP
[UFunction(FunctionFlags.BlueprintCallable)]
public void MyBPCallableFunction(IList<int> myList)
{
    
}

[UFunction(FunctionFlags.BlueprintEvent)]
public partial void MyBPOverridableFunction(IList<int> myList);

public partial void MyBPOverridableFunction_Implementation(IList<int> myList)
{

}
```

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

// Can be overridden by Blueprint, but has a default implementation
// Virtual specifier is optional.
[UFunction(FunctionFlags.BlueprintEvent)]
public virtual void MyOverridableFunction(IList<int> myList)
{
    
}

// Can be overridden by Blueprint, but has no default implementation
[UFunction(FunctionFlags.BlueprintEvent)]
public void MyBPOverridableFunction(IList<int> myList);
```

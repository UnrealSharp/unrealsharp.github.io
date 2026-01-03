---
description: >-
  To expose C# methods to Unreal Engine, whether for Blueprint calls or
  Blueprint overrides. You must apply the [UFunction] attribute.
---

# Functions

### **Blueprint-Callable Functions**

Use `BlueprintCallable` (or other call-related flags like `BlueprintPure`, etc.) to allow Blueprint graphs to invoke your C# method.

```csharp
// Can be called from BP
[UFunction(FunctionFlags.BlueprintCallable)]
public void MyBPCallableFunction(IList<int> myList)
{
    
}
```

Notes:

* Accepts normal managed types (`int`, `float`, `IList<T>`, etc.) as long as they can be marshalled.

***

### Blueprint-Overridable Functions (Events)

To allow Blueprint subclasses to override a C# function, UnrealSharp uses a **partial method pair**:

* A _declaration_ marked with `BlueprintEvent`.
* An automatically-generated `*_Implementation` method stub you can override on the C# side.

```csharp
// Declares a function that Blueprint subclasses may override.
[UFunction(FunctionFlags.BlueprintEvent)]
public partial void MyBPOverridableFunction(IList<int> myList);

// The default implementation on the C# side.
public partial void MyBPOverridableFunction_Implementation(IList<int> myList)
{
    // Default behavior
}

```

# C++ Extension Methods for C#

Extension methods are static methods that can be invoked on an existing class as if they were instance methods of that class. This is particularly useful when you want to add methods to existing classes (such as `Actor`) without modifying their original source code.

## Usage Requirements

To generate extension methods from C++ to C#, a C++ function needs to follow these:

- **Static and Public:** Extension methods must be declared as `static` and `public` in your C++ class.
- **Meta Attribute:** Use the `meta=(ExtensionMethod)`
- **Parameter Requirements:** The first parameter must be a reference to the type you are extending (`AActor*` in the case of extending `AActor`).
- **BlueprintCallable or ScriptMethod:** Ensure the method is marked with `BlueprintCallable` or `ScriptMethod` depending on your use case.
- **BlueprintFunctionLibrary** Needs to be in a BlueprintFunctionLibrary.

## Example

```cpp
UCLASS()
class UCSTestExtensions : public UBlueprintFunctionLibrary
{
    GENERATED_BODY()

public:

    // Example of an extension method that takes an int parameter
    // public static void ExtensionMethod1(this Actor actor, int value)
    UFUNCTION(meta=(ExtensionMethod, ScriptMethod))
    static void ExtensionMethod1(AActor* Actor, int32 Value) {};

    // Example of an extension method that takes a float parameter
    // public static void ExtensionMethod2(this Actor actor, float value)
    UFUNCTION(meta=(ExtensionMethod, ScriptMethod))
    static void ExtensionMethod2(AActor* Actor, float Value) {};
};
```

And it'll generate the following:

```c#
public static class CSharpForUEExtensions
{
    
    /// <summary>
    /// Example of an extension method that takes a float parameter
    /// public static void ExtensionMethod2(this Actor actor, float value)
    /// </summary>
    public static void ExtensionMethod2(this UnrealSharp.Engine.Actor actor, float value)
    {
        UnrealSharp.CSharpForUE.CSTestExtensions.ExtensionMethod2(actor, value);
    }
    
    /// <summary>
    /// Example of an extension method that takes an int parameter
    /// public static void ExtensionMethod1(this Actor actor, int value)
    /// </summary>
    public static void ExtensionMethod1(this UnrealSharp.Engine.Actor actor, int value)
    {
        UnrealSharp.CSharpForUE.CSTestExtensions.ExtensionMethod1(actor, value);
    }
}
```

And can be used like this:

```c#
protected override void ReceiveBeginPlay()
{
    MyActorReference.ExtensionMethod1(20);
    base.ReceiveBeginPlay();
}
```

# FWorldStaticVar\<T>

`FWorldStaticVar<T>` is a class designed to manage static variables that are tied to the lifetime of a `UWorld`. This means the value is automatically cleaned up when the associated `UWorld` is destroyed, such as during level transitions.

**Declaration and Usage**

You can declare a world-static variable like this:

```csharp
public static readonly FWorldStaticVar<float> MyStaticFloat = new();
```

To use it within your C# code:

```csharp
public partial class AMyActor : AActor
{
    public static readonly FWorldStaticVar<float> MyStaticFloat = new();
    
    public AMyActor()
    {
        // Set the value to 70 in the current World
        MyStaticFloat.Value = 70;
    }
}
```

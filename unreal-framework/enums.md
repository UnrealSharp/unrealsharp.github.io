# Enums

To expose a C# enum to Unreal Engine, it must:

* Use `byte` as its underlying type
* Have with the `[UEnum]` attribute

This is a hard limitation by Unreal Engine for enums used in properties and function parameters.

```csharp
[UEnum]
public enum EMyEnum : byte
{
    Value1 = 0,
    Value2 = 1,
}
```

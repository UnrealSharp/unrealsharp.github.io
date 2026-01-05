# Structs

To expose a C# struct to Unreal Engine, it must:

* Be declared as `partial`
* Have the `[UStruct]` attribute

```csharp
[UStruct]
public partial struct FMyStruct
{
    [UProperty(PropertyFlags.BlueprintReadOnly)]
    public int MyInt { get; private set; }
    
    [UProperty(PropertyFlags.BlueprintReadOnly)]
    public float MyFloat;
    
    [UProperty(PropertyFlags.BlueprintReadOnly)]
    public string MyString;
    
    [UProperty(PropertyFlags.BlueprintReadOnly)]
    public bool MyBool;
    
    [UProperty(PropertyFlags.BlueprintReadOnly)]
    public UObject MyObject;

    [UProperty(PropertyFlags.BlueprintReadOnly)]
    public IList<bool> MyArray;

    [UProperty(PropertyFlags.BlueprintReadOnly)]
    public IDictionary<string, string> MyMap;
}
```

Records also works:

```csharp
[UStruct]
public partial record struct FMyDemoStruct([field: UProperty(PropertyFlags.EditAnywhere)] int MyInt, 
                                   [field: UProperty(PropertyFlags.EditAnywhere)] string MyString)
```

# Structs

Structs need to be partial and have the `UStruct` attribute to expose the struct to the engine.

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
}
```

Records also works:

```csharp
[UStruct]
public partial record struct FMyDemoStruct([field: UProperty(PropertyFlags.EditAnywhere)] int MyInt, 
                                   [field: UProperty(PropertyFlags.EditAnywhere)] string MyString)
```

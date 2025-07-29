# Structs / Records

Only need UStruct to expose the struct to Unreal Engine

```csharp
[UStruct]
public struct FMyStruct
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
public record struct FMyDemoStruct([field: UProperty(PropertyFlags.EditAnywhere)] int MyInt, 
                                   [field: UProperty(PropertyFlags.EditAnywhere)] string MyString)
```


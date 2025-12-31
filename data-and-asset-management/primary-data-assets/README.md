# Primary Data Assets

You can create a `UPrimaryDataAsset` in C# using `UCSPrimaryDataAsset`.

```csharp
[UClass]
public partial class UItemPrimaryDataAsset : UCSPrimaryDataAsset
{
    public UItemPrimaryDataAsset()
    {
        AssetName = "Item";
    }
    
    [UProperty(PropertyFlags.EditDefaultsOnly)]
    public partial FText ItemName { get; set; }
}
```

`AssetName` needs to match up with the type assigned in `AssetManager`settings in your project settings.

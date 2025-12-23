# Developer Settings

Developer Settings is a class that shows up in **Project Settings** to configure values without needing to create a Blueprint.

**Requirements:**

* Create a class that derives from `UDeveloperSettings`.
* Assign a config category to the class, for example:`[UClass(config: "Game")]`.
* Any property you want to edit must be marked with `PropertyFlags.Config`.
* Object references can't be saved to config. They need to be soft referenced through TSoftObjectPtr<> or TSoftClassPtr<>.

```csharp
[UClass(config: "Game")]
public partial class UMyDeveloperSettings : UDeveloperSettings
{
    [UProperty(PropertyFlags.EditAnywhere | PropertyFlags.Config)]
    public partial float MyConfigFloat { get; set; }
    
    [UProperty(PropertyFlags.EditAnywhere | PropertyFlags.Config)]
    public partial TSoftObjectPtr<UMaterialInterface> MyConfigMaterial { get; set; }
}
```

If you now open the project settings, you can find your custom developer settings there.<br>

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

How to get the values in C#:

```csharp
public override void BeginPlay()
{
    UMyDeveloperSettings settings = GetDefault<UMyDeveloperSettings>();
    if (settings.MyConfigMaterial.IsValid)
    {
        // Do something with the material
    }
}
```

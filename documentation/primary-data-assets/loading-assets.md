# Loading Assets

All types registered in `AssetManager` settings are accessible in C# through the static `AssetTypes` class. These bindings make it easy to locate and load all assets of a specific type:

```csharp
UAssetManager assetManager = UAssetManager.Get();

// Optional list of asset bundles to load
List<FName> bundles = new List<FName>();

// Load all primary assets of type ItemRecipe
assetManager.LoadPrimaryAssets(AssetTypes.ItemRecipe.PrimaryAssetList, bundles, (loadedAssets) =>
{
    // Callback for when assets are loaded
});
```

To load specific assets, use the static `AssetIds` class or expose a `UProperty`of type `FPrimaryAssetId`and assign it in editor.

```csharp
UAssetManager assetManager = UAssetManager.Get();

// Optional list of asset bundles to load
List<FName> bundles = new List<FName>();

// Loads Item_Axe primary asset.
assetManager.LoadPrimaryAsset(AssetIds.Item_Item_Axe, bundles, [UFunction](asset) =>
{
    // Callback for when assets are loaded
});

// Loads Item_Axe primary asset through assigned property.
assetManager.LoadPrimaryAsset(AxeRecipeId, bundles, [UFunction](asset) =>
{
    // Callback for when assets are loaded
});
```

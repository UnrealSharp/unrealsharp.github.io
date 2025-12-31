# Loading Primary Data Assets

All types registered in `AssetManager` settings are accessible in C# through the static `AssetTypes` class. These bindings make it easy to locate and load all assets of a specific type:

```csharp
UAssetManager assetManager = UAssetManager.Get();

// Optional list of asset bundles to load
List<FName> bundles = new List<FName>();

// Load all primary assets of type ItemRecipe
IList<UItemRecipe> loadedItems = await assetManager.LoadPrimaryAssets<UItemRecipe>(AssetTypes.ItemRecipe.PrimaryAssetList, bundles);
```

To load specific assets, use the static `AssetIds` class or expose a `UProperty`of type `FPrimaryAssetId`and assign it in editor.

```csharp
UAssetManager assetManager = UAssetManager.Get();

// Optional list of asset bundles to load
List<FName> bundles = new List<FName>();

// Loads Item_Axe primary asset.
UItem loadedItem = await assetManager.LoadPrimaryAsset<UItem>(AssetIds.Item_Item_Axe, bundles);

// Loads Item_Axe primary asset through assigned property.
UItem loadedItem = await assetManager.LoadPrimaryAsset<UItem>(AxeRecipeId, bundles);
```

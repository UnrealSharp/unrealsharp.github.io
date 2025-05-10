# Loading Soft References

Unreal has two ways to reference assets so they're not a hard reference. Both through `TSoftObjectPtr<T>` and `TSoftClassPtr<T>`, these must be loaded in order to use them.

### Async Loading

This API allows you to load soft references asynchronously.

* If the reference is `null`, an exception is thrown.
* If the asset is already loaded, it's returned immediately.
* Otherwise, the asset is loaded in the background and returned once ready.

**Load a single soft reference:**

`var loadedReferences = await softReference.LoadAsync();`

**Load a list of soft references:**

`var loadedReferences = await softReferences.LoadAsync();`

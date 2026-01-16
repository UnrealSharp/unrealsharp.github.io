---
icon: heart-crack
---

# Known Issues

#### JSON Serialization

Using **Newtonsoft.Json** together with UnrealSharp’s AssemblyLoadContext based hot reload system can cause reloads to fail.

More info and workaround [here](https://github.com/UnrealSharp/UnrealSharp/issues/544).

#### Glue re-generating on engine upgrade or enabling a plugin

When upgrading to a new engine version or enabling an engine plugin, UnrealBuildTool doesn't trigger because it doesn't detect any source code changes, and no new glue will be generated.&#x20;

To fix this you need to force a glue re-generation by manually deleting the `Intermediate` and `Saved` folders in the UnrealSharp plugin folder.

Now compile as usual, and the glue will be re-generated.

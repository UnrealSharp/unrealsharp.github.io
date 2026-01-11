---
icon: heart-crack
---

# Known Issues

#### JSON Serialization

Using **Newtonsoft.Json** together with UnrealSharp’s AssemblyLoadContext based hot reload system can cause reloads to fail.

More info and workaround [here](https://github.com/UnrealSharp/UnrealSharp/issues/544).

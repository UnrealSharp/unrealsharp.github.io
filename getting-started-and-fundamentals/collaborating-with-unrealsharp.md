---
icon: users
---

# Collaborating with UnrealSharp

When collaborating with designers/artists (content creators) they often do not have access to build tools to generate the necessary C# glue generated from C++ reflection data.&#x20;

You can distribute pre-compiled installed builds to your team. This removes the need to commit generated files to source control and allows creators to work locally without a full build environment.

### Generating an Installed Build

Run the following command to package the necessary binaries:

```
"[ENGINE_PATH]\Engine\Build\BatchFiles\RunUAT.bat" StageUnrealSharp -ScriptDir="[PROJECT_ROOT]\Plugins\UnrealSharp\Build\Scripts" -Project="[PROJECT_ROOT]\Ember.uproject"
```

The staged build is generated here: `[PROJECT_ROOT]\Binaries\Managed\DOT_NET_VERSION\`. You can now distribute it to your content creators according to your pipeline.


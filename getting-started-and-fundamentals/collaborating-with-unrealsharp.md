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

You can now distribute these specifically to your content creators according to your existing pipeline (via Unreal Game Sync or your preferred source control workflow).

> Note: Only the generated C# glue code should be distributed this way. Continue to distribute your C++ binaries (the compiled game modules) through your pipeline as you would with any standard Unreal Engine project.

### Debug Tools

If it's not working as expected, you can use these console variables to simulate different environments and verify your setup:

* `UnrealSharp.SimulateNoDotNetSDK 1` Simulates an environment where the .NET SDK is not installed.
* `UnrealSharp.SimulateInstalledBuild 1` Forces the plugin to treat the environment as an installed build. This confirms that the project correctly consumes the distributed binaries instead of attempting to trigger a local build. **This assumes the .NET SDK is installed unless `UnrealSharp.SimulateNoDotNetSDK` is also active.**


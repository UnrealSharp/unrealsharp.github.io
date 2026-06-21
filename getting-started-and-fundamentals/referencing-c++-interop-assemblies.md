---
icon: file
---

# Referencing C++ Modules

Since your C++ modules are compiled as binaries rather than included as source, you will need to point your project directly to the assembly.

You can find the assemblies in: `MyProjectRootFolder/Binaries/Managed/<TargetFramework>`

To add a module, insert a reference entry into your `.csproj` file pointing to the DLL:

```xml
<Reference Include="MyCppModule">
  <HintPath>..\..\Binaries\Managed\net10.0\MyCppModule.dll</HintPath>
</Reference>
```

Hot reloading changes to `.csproj` files isn't supported yet. If the engine is already running, you’ll need to restart it to pick up your new module references.


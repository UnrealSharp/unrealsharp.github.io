# Static Variables

Managing static variables in Unreal Engine can be tricky. Regular static variables have a global lifetime, meaning their values persist across the entire application runtime. While this may seem convenient, it can lead to issues.

For instance, if you use regular static variables to store world-specific data, you might encounter problems such as:

* **Memory Leaks:** Static variables won’t automatically release their references when a `UWorld` is destroyed, potentially causing garbage collection (GC) issues.
* **Global Scope Conflicts:** Since regular static variables are shared across all worlds, their values are prone to accidental overwrites or unintended usage.

### Static Variables in UnrealSharp

To enable these classes in your project you need to include this in your csproj:

```xml-doc
<Reference Include="UnrealSharp.StaticVars">
  <HintPath>..\..\Plugins\UnrealSharp\Binaries\Managed\UnrealSharp.StaticVars.dll</HintPath>
</Reference>
```

## Available classes that manages static data

{% content-ref url="fgamestaticvar-less-than-t-greater-than.md" %}
[fgamestaticvar-less-than-t-greater-than.md](fgamestaticvar-less-than-t-greater-than.md)
{% endcontent-ref %}

{% content-ref url="fworldstaticvar-less-than-t-greater-than.md" %}
[fworldstaticvar-less-than-t-greater-than.md](fworldstaticvar-less-than-t-greater-than.md)
{% endcontent-ref %}

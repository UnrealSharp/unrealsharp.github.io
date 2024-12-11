# Static Variables

Managing static variables in Unreal Engine can be tricky. Regular static variables have a global lifetime, meaning their values persist across the entire application runtime. While this may seem convenient, it can lead to issues.

For instance, if you use regular static variables to store world-specific data, you might encounter problems such as:

* **Memory Leaks:** Static variables won’t automatically release their references when a `UWorld` is destroyed, potentially causing garbage collection (GC) issues.
* **Global Scope Conflicts:** Since regular static variables are shared across all worlds, their values are prone to accidental overwrites or unintended usage.

### Static Variables in UnrealSharp

#### FWorldStaticVar\<T>

`FWorldStaticVar<T>` is a class designed to manage static variables that are tied to the lifetime of a `UWorld`. This means the value is automatically cleaned up when the associated `UWorld` is destroyed, such as during level transitions.

**Declaration and Usage**

You can declare a world-static variable like this:

```csharp
public static readonly FWorldStaticVar<float> MyStaticFloat = new();
```

To use it within your C# code:

<pre class="language-csharp"><code class="lang-csharp">public class AMyActor: AActor
{
<strong>    public static readonly FWorldStaticVar&#x3C;float> MyStaticFloat = new();
</strong><strong>    
</strong>    public AMyActor()
    {
        // Set the value to 70 in the current World
        MyStaticFloat.Value = 70;
    }
}
</code></pre>

#### FGameStaticVar\<T>

Will be alive during the whole game session. Not yet implemented.

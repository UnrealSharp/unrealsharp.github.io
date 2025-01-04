# FGameStaticVar\<T>

#### FGameStaticVar\<T>

`FGameStaticVar<T>` is a class designed to manage static variables that will persist during the whole game.

In editor the value will reset on Play In Editor start/end and on hot reload.

**Declaration and Usage**

You can declare a game-static variable like this:

```csharp
public static readonly FGameStaticVar<float> MyStaticFloat = new();
```

To use it within your C# code:

<pre class="language-csharp"><code class="lang-csharp">public class AMyActor : AActor
{
<strong>    public static readonly FGameStaticVar&#x3C;float> MyStaticFloat = new();
</strong><strong>    
</strong>    public AMyActor()
    {
        // Set the value to 70 for this session
        MyStaticFloat.Value = 70;
    }
}
</code></pre>

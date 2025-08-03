---
description: >-
  To expose C# classes to Unreal Engine, they must be marked with the [UClass]
  attribute and inherit from a UObject, such as AActor, UActorComponent, or any
  other subclass.
---

# Classes

<pre class="language-csharp"><code class="lang-csharp"><strong>[UClass]
</strong>public class AMyShowcaseClass : AActor
{
    protected override void BeginPlay()
    {
        base.BeginPlay();
    }
}

</code></pre>

---
description: Making your first basic script in UnrealSharp
icon: scroll
---

# Your First Script

## First Script

Example setup of a basic UnrealSharp class

```csharp
using UnrealSharp.Attributes;
using UnrealSharp.Engine;

namespace ManagedTestCSharp;

[UClass]
public partial class AMyTestClass : AActor
{   
    [UProperty(PropertyFlags.BlueprintReadOnly)]
    public partial int MyInt { get; set; }

    public override void BeginPlay()
    {
        PrintString("Hello from C#!");
    
        base.BeginPlay();
    }

    [UFunction(FunctionFlags.BlueprintCallable)]
    public void MyFunction(int myInt)
    {
        MyInt = myInt;
        PrintString($"MyInt set to {MyInt}");
    }
}
```

Now go back to Unreal Engine and it should compile your code and your class should be able to be found in the editor.

<figure><img src="../.gitbook/assets/unreal_class_wizard.png" alt=""><figcaption></figcaption></figure>

## &#x20;<a href="#debugging" id="debugging"></a>

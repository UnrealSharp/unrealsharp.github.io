---
description: Making your first basic script in UnrealSharp
icon: scroll
layout:
  width: default
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
  tags:
    visible: true
  actions:
    visible: true
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
    // Automatically instantiated as a component, attached to the actors as the root, and editable in the defaults
    [UProperty(DefaultComponent = true, RootComponent = true)]
    public partial UStaticMeshComponent MyStaticMeshComponent { get; set; }
    
    // Can be read from Blueprints, but only set from C#
    [UProperty(PropertyFlags.BlueprintReadOnly)]
    public partial int MyInt { get; set; }
    
    // Can be read and set from Blueprints
    [UProperty(PropertyFlags.BlueprintReadWrite)]
    public partial IList<int> MyList { get; set; }
    
    // Can be read and set from Blueprints, but only editable in the defaults, not per instance
    [UProperty(PropertyFlags.BlueprintReadWrite | PropertyFlags.EditDefaultsOnly)]
    public partial bool MyBool { get; set; }

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

Now these members can be called from Blueprints!

<figure><img src="../.gitbook/assets/image (25).png" alt=""><figcaption></figcaption></figure>

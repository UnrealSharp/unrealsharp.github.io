# Show Widget On Screen

To spawn a widget, your class needs a reference to the Widget Blueprint class.&#x20;

Use `TSubclassOf<T>` to create a selectable dropdown in the Unreal Editor, to be able to choose your Widget Blueprint.

```csharp
[UClass]
public partial class AMyCharacter : ACharacter
{
    [UProperty(PropertyFlags.EditDefaultsOnly)]
    protected partial TSubclassOf<UMyWidget> MyWidgetClass { get; set; }
}
```

Which creates this in your child BP class, now assign it with a widget blueprint you want to spawn.

<figure><img src="../../.gitbook/assets/image (7) (1).png" alt=""><figcaption></figcaption></figure>

Now you can create the widget blueprint and show it:

```csharp
[UClass]
public partial class AMyCharacter : ACharacter
{
    [UProperty(PropertyFlags.EditDefaultsOnly)]
    protected partial TSubclassOf<UMyWidget> MyWidgetClass { get; set; }
    
    public override void BeginPlay()
    {
        // CreateWidget is available in any UObject class.
        UMyWidget myWidget = CreateWidget(MyWidgetClass);
        myWidget.AddToViewport();
        
        // Custom initialization function that I created
        myWidget.InitializeFrom(this);
    }
}
```

`AddToViewport` is the quickest way to get a widget on screen, it’s generally considered "quick and dirty".

Highly recommend using built-in plugins like [CommonUI](https://dev.epicgames.com/documentation/en-us/unreal-engine/overview-of-advanced-multiplatform-user-interfaces-with-common-ui-for-unreal-engine) to build more complex and scalable UI. It works with UnrealSharp right out of the box.

# Create/Compose Widgets

Make a class that inherits from `UUserWidget` (for layouts) or a specific widget like `UTextBlock` for extensions.

```csharp
[UClass]
public partial class UMyWidget : UUserWidget
{
}
```

Now add the child widgets to compose your widget.

The widgets you want to bind needs to have `UProperty` and `BindWidget` to work.

```csharp
[UClass]
public partial class UMyWidget : UUserWidget
{
    [UProperty, BindWidget]
    public partial UImage MyImage { get; set; }
    
    [UProperty, BindWidget]
    public partial UTextBlock MyTextBlock { get; set; }
}
```

In the Unreal Editor, create a new Widget Blueprint.

<figure><img src="../../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

When you have opened up the widget asset, you'll see compiler errors stating that the required widgets are missing.

<figure><img src="../../.gitbook/assets/image (2) (1) (1).png" alt=""><figcaption></figcaption></figure>

To resolve errors:

* Drag a widget element you want to bind from the **Palette** window into your **Hierarchy** (as shown in the image below)
* You must rename these spawned widgets to exactly match the property names in your C# code (in this case: `MyImage` and `MyTextBlock`).

<figure><img src="../../.gitbook/assets/image (4) (1).png" alt=""><figcaption></figcaption></figure>

Hit Compile in the editor. The errors will disappear as the C# properties successfully "bind" to the newly spawned widgets.

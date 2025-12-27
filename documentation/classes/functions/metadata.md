# Meta Data

Meta Data is a way to add additional data to any reflected type in Unreal Engine in editor. UnrealSharp has exposed the most common metadata in Unreal Engine through attributes.

```cpp
UPROPERTY(EditDefaultsOnly, meta = (Category = "MyCategory"))
TObjectPtr<UMyObject> MyObject;
```

Becomes this in C#:

```csharp
// Alternative 1
[UProperty(PropertyFlags.EditDefaultsOnly), Category("MyCategory")]
public partial UMyObject MyObject { get; set; }

// Alternative 2
[UProperty(PropertyFlags.EditDefaultsOnly), UMetaData("Category", "MyCategory")]
public partial UMyObject MyObject { get; set; }
```

So any meta data key you see in Unreal Engine documentation or C++ source code, there is likely an C# attribute with the same name.

If they don't exist, you can do `UMetaData("Key", "Value")`, as shown above in alternative 2.

#### Custom Meta Data Attributes

You can also define your own metadata attributes that the source generator will pick up and add to the type in engine.

To get started, add the `CustomMetaData` attribute to your custom attribute class. Here is the breakdown of how it works:

* Key: The attribute name becomes the metadata key (the source generator automatically removes the "Attribute" part).
* Value: The first argument in your constructor becomes the metadata value.

```csharp
[AttributeUsage(AttributeTargets.All), CustomMetaData]
public sealed class CategoryAttribute(string categoryName) : Attribute { }
```

In the example above, the source generator strips "Attribute" from the name, resulting in a metadata key of "Category" with the value you pass into the constructor.

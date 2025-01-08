---
description: MetaData for UFunctions and their purpose
---

# MetaData

Example of MetaData

```csharp
[UFunction(DisplayName = "TestFunction")] // Will show up in blueprint as this
public void MyTestFunction() { }
```



<table><thead><tr><th width="375">MetaData</th><th>Effect</th></tr></thead><tbody><tr><td>DisplayName</td><td>The name of this node in a Blueprint will be replaced with the value provided here, instead of the code-generated name.</td></tr><tr><td>CallInEditor</td><td>This function can be called in the editor on selected instances via a button in the Details panel.</td></tr><tr><td>Category = "TopCategory|SubCategory|Etc"</td><td>Specifies the category of the function when displayed in Blueprint editing tools. Define nested categories using the | operator.</td></tr><tr><td>ExpandEnumAsExecs="Parameter"</td><td>For <code>BlueprintCallable</code> functions, this indicates that one input execution pin should be created for each entry in the <code>enum</code> used by the parameter. The parameter must be of an enumerated type that has the <code>UEnum</code> Attribute.</td></tr></tbody></table>

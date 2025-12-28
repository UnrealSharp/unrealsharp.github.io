# Custom C# Getter / Setter

`UProperty` also supports custom getters / setters, aslong as the property type is supported by `UProperty`.

Custom getter / setter don't need any partial declaration.

```csharp
private int _score;

[UProperty(PropertyFlags.BlueprintReadOnly)]
public int Score
{
    get { return _score; }
    set 
    { 
        _score = value;
        
        if (_score == 10)
        {
            Win();
        }
    }
}
```

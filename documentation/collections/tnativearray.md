---
description: >-
  A more optimized approach to unreals arrays for doing fast copying as well as
  being able to share data between managed and native without marshalling costs.
---

# TNativeArray

```csharp
[UClass]
public class AActorTest : ACharacter
{
    [UProperty(PropertyFlags.EditAnywhere)]
    public TNativeArray<int> NativeArrayTest { get; set; }

    [UProperty(PropertyFlags.EditAnywhere)]
    public TNativeArray<int> NativeArrayTest2 { get; set; }

    protected override void BeginPlay()
    {
        base.BeginPlay();

        Span<int> test = [5, 6, 7, 8];
        NativeArrayTest.CopyFrom(test);

        Span<int> test2 = stackalloc int[NativeArrayTest.Length];
        NativeArrayTest.CopyTo(test2);

        NativeArrayTest2.CopyFrom(test2);
    }
}
```

You can also use NativeArray without any marshalling costs

```csharp
public override void Tick(float deltaSeconds)
{
    base.Tick(deltaSeconds);

    ref int MyNumber = ref NativeArrayTest.AsSpan()[0];
    MyNumber++;
}
```

TNativeArray can also be represented as an ReadOnlySpan inside of a UFunction

```csharp
[UFunction(FunctionFlags.BlueprintCallable)]
public void TestSpanCall(ReadOnlySpan<byte> span)
{
    PrintString($"Span Length: {span.Length}");
}
```

## Supported Types <a href="#features" id="features"></a>

Currently right now NativeArray only supports numerical primitive types

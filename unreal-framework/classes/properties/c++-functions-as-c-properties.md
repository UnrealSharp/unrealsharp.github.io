# C++ Functions As C# Properties

UnrealSharp automatically generates properties for any C++ function with a `Get` or `Set` prefix, provided the function either returns a value or accepts a single parameter.&#x20;

This includes `Get` functions that has an out parameter or just a `WorldContextObject`as parameter, like shown below.

```csharp
/** Returns the game instance object  */
UFUNCTION(BlueprintPure, Category="Game", meta=(WorldContext="WorldContextObject"))
static ENGINE_API class UGameInstance* GetGameInstance(const UObject* WorldContextObject);
```

The generator will attempt to pair corresponding getter and setter functions into a single C# property.

The following functions:

```cpp
UFUNCTION(BlueprintCallable)
void SetTestValue(int32 Value);

UFUNCTION(BlueprintCallable)
int32 GetTestValue();
```

turns into a property in C#:

```csharp
public int TestValue
{
    get
    {
        unsafe
        {
            byte* ParamsBufferAllocation = stackalloc byte[GetTestValue_ParamsSize];
            nint ParamsBuffer = (nint) ParamsBufferAllocation;
            UStructExporter.CallInitializeStruct(GetTestValue_NativeFunction, ParamsBuffer);
            
            UObjectExporter.CallInvokeNativeFunction(NativeObject, GetTestValue_NativeFunction, ParamsBuffer);
            
            int returnValue;
            returnValue = BlittableMarshaller<int>.FromNative(IntPtr.Add(ParamsBuffer, GetTestValue_ReturnValue_Offset), 0);
            
            return returnValue;
        }
    }
    set
    {
        unsafe
        {
            byte* ParamsBufferAllocation = stackalloc byte[SetTestValue_ParamsSize];
            nint ParamsBuffer = (nint) ParamsBufferAllocation;
            UStructExporter.CallInitializeStruct(SetTestValue_NativeFunction, ParamsBuffer);
            BlittableMarshaller<int>.ToNative(IntPtr.Add(ParamsBuffer, SetTestValue_Value_Offset), 0, value);
            
            UObjectExporter.CallInvokeNativeFunction(NativeObject, SetTestValue_NativeFunction, ParamsBuffer);
            
        }
    }
}
```

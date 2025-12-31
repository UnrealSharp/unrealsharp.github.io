# C++ Properties with Getters/Setters

UnrealSharp will attempt to pair up C++ member variables with their designated getters/setters and call these functions rather than setting the value directly in memory.&#x20;

It also supports the new native Getter/Setters workflow that was implemented in 5.1.

The following C++ member:

```csharp
UPROPERTY(BlueprintGetter=K2_GetRootComponent, Category="Transformation")
TObjectPtr<USceneComponent> RootComponent;
```

maps to this C# code, which calls `K2_GetRootComponent` to retrieve the value:

```csharp
public UnrealSharp.Engine.USceneComponent RootComponent
{
    get
    {
        unsafe
        {
            byte* ParamsBufferAllocation = stackalloc byte[K2_GetRootComponent_ParamsSize];
            nint ParamsBuffer = (nint) ParamsBufferAllocation;
            UStructExporter.CallInitializeStruct(K2_GetRootComponent_NativeFunction, ParamsBuffer);
            
            UObjectExporter.CallInvokeNativeFunction(NativeObject, K2_GetRootComponent_NativeFunction, ParamsBuffer);
            
            UnrealSharp.Engine.USceneComponent returnValue;
            returnValue = ObjectMarshaller<UnrealSharp.Engine.USceneComponent>.FromNative(IntPtr.Add(ParamsBuffer, K2_GetRootComponent_ReturnValue_Offset), 0);
            
            return (UnrealSharp.Engine.USceneComponent)returnValue;
        }
    }
}
```

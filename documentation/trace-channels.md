# Trace Channels

Working with collision channels in C# is not great, as the engine internally uses `ECollisionChannel` mapped to `ETraceTypeQuery` for BP-exposed tracing functions like `LineTraceByChannel` and others. By default, these mappings are not intuitive in C#, as they are just numeric IDs, with no info about the collision channel name.

To bridge this gap, the `ETraceChannel` provide a way to work with more readable and user-defined channel names in C#.

### ETraceChannel

The `ETraceChannel` enum defines a set of collision channels, each of which maps to a corresponding entry in the project's collision settings.

```
public enum ETraceChannel
{
    Visibility = 0,      // Default engine-provided channel
    Camera = 1,          // Default engine-provided channel
    MyOtherChannel = 2,  // User-defined collision channel
}
```

{% hint style="info" %}
**Note:** The entries in `ETraceChannel` will regenerate whenever new collision channels are added or existing ones are modified in the Unreal Editor. Removing entries requires an engine restart, as it's an engine bug that they keep the removed channel around.
{% endhint %}

### ETraceChannel to ETraceTypeQuery

Here's how to use the `ETraceChannel` enum and the `ToQuery` to use it with `ETraceTypeQuery`:

```
ETraceTypeQuery traceChannel = ETraceChannel.Camera.ToQuery();
SystemLibrary.LineTraceByChannel(this, start, end, traceChannel, false, actors, EDrawDebugTrace.None, out FHitResult hit, true);
```

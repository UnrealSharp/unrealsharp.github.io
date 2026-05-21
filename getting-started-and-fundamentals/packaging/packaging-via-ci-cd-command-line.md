# Packaging via CI/CD (Command Line)

You can trigger the packaging process from any CI/CD environment (such as TeamCity, Jenkins, or GitHub Actions) by invoking the `RunUAT` batch file directly from your build agent.

{% code overflow="wrap" %}
```bat
"<EnginePath>\Engine\Build\BatchFiles\RunUAT.bat" PackageProject -ScriptDir="<UnrealSharpRoot>\Build\Scripts" -Project="<YourProjectDirectory>/<YourProjectName>.uproject" -ArchiveDirectory="<YourArchiveDirectory>" -UETargetType="<TargetType>" -UEBuildConfig="<Config>"
```
{% endcode %}

### Available Parameters <a href="#example-usage" id="example-usage"></a>

* ArchiveDirectory: `[REQUIRED]` The base directory containing the packaged executable.
* UETargetType: `[REQUIRED]` The Unreal Engine target type (Editor, Game, Client, or Server).
* UEBuildConfig: `[REQUIRED]` The build configuration (Debug, Development, Shipping, or Test).
* TargetPlatform: `[Optional]` The target platform (Defaults to Win64).
* TargetArchitecture: `[Optional]` The target architecture (Defaults to X64).
* UserParams: `[Optional]` Additional parameters to forward to the user solution build. These should be specified in the format `-UserParams="-p:Property=Value" -UserParams="--argument"`.

### Example Usage: <a href="#example-usage" id="example-usage"></a>

If your engine is installed in `C:/Program Files/Epic Games/UE_5.5` and your project is located at `C:/BuildAgent/Work/MyGame`, a command would look like this:

{% code overflow="wrap" %}
```batch
"C:/Program Files/Epic Games/UE_5.5/Engine/Build/BatchFiles/RunUAT.bat" PackageProject -ScriptDir="C:/BuildAgent/Work/MyGame/Plugins/UnrealSharp/Build/Scripts" -Project="C:/BuildAgent/Work/MyGame/MyGame.uproject" -ArchiveDirectory="C:/BuildAgent/Output/Windows" -UETargetType="Game" -UEBuildConfig="Shipping"
```
{% endcode %}


---
title: FAQ
layout: default
---

# Frequently Asked Questions

## General
### 1. What is UnrealSharp?
UnrealSharp is a plugin for Unreal Engine that allows developers to use C# for game development and editor tooling. It is designed to offer the same functionalities as Blueprint, and even more, providing a familiar environment for C# developers. It is developed with fast iteration in mind, so you can develop your games in C# with the engine open, and it will compile the code for you on the fly.

### 2. Can I make a game with UnrealSharp?
The plugin is not production ready yet, but the plan is yes you will be able to!

### 3. How do I download UnrealSharp?
You can compile a source build from the [GitHub repository](https://github.com/UnrealSharp/UnrealSharp).

### 4. I'm coming from Unity with a C# background, is UnrealSharp a good fit for me?
It is recommended you have Unreal Engine experience and an engineer familiar with C++ to use UnrealSharp. Having an understanding of the [Blueprint / C++ architecture](https://youtu.be/VMZftEVDuCE?si=bxRZj6z9VDTC0Fkk) and how they're used side by side is extremely important to have knowledge on.

Additionally, UnrealSharp can only access what is exposed to [reflection](#1-what-is-reflection), so similar to Blueprints you will still need to use C++ to expose certain systems or features. The plugin has an ongoing effort to help expose things to C# out of the box, such as subsystems, but you won't be able to rely on that for everything.

### 5. Can I use UnrealSharp for commercial projects?

Absolutely! UnrealSharp is completely free of charge and open-source for both personal and commercial use.

### 5. Does UnrealSharp support [ platform ]?
The [Home Page](index.md#supported-platforms) has a Supported Platforms section listing out the supported and planned platforms.

### 6. Is there an ETA for [ feature ]?
To avoid setting expectations or putting stress on any contributors release dates are not provided. UnrealSharp is a passion project worked on in people's free time, so it does not follow a schedule or deadlines.

### 7. What features are being worked on?
You can look at the [Roadmap](https://github.com/orgs/UnrealSharp/projects/3) for a look at what is currently in development and also on the todo list.

### 8. What are the system requirements for UnrealSharp?
UnrealSharp requires the same system specifications as [Unreal Engine](https://dev.epicgames.com/documentation/en-us/unreal-engine/hardware-and-software-specifications-for-unreal-engine). Additionally, the [.NET 8.0 SDK](https://dotnet.microsoft.com/en-us/download/dotnet/8.0) is necessary to use this plugin.


## Technical
### 1. What is reflection?
You can read more about the Unreal reflection system [here](https://www.unrealengine.com/en-US/blog/unreal-property-system-reflection), but in simple terms it's how Unreal exposes C++ classes, functions, properties, and other types to engine systems such blueprints, replication, and garbage collection.

Due to all of Unreal systems being written in C++, if a class, struct, or function is not exposed to reflection, blueprints cannot access it. UnrealSharp utilizes reflection for generating C# code and communicating with Unreal, so it has the same restriction as blueprints.

### 2. What is the difference between a binary and source build of the plugin?
A binary build is a precompiled and packaged version that doesn't need to be manually compiled by the end user. A source build is when the end user needs to download the source code and compile the code themselves for use.

Due to UnrealSharp not being production ready and making quick changes we do not consistently release up-to-date binary builds. You will need to compile the source yourself. Here is a [resource](https://youtu.be/94FvzO1HVzY?si=fWKC3CY-eIKN1VPt) on how to set up an Unreal C++ project to start.

### 3. Do I need to use Blueprints?
Blueprints is not just visual scripting, it's an [interface](https://youtu.be/VMZftEVDuCE?si=QE0sKi4w9Q2YSlYm) to your game assets. It is highly recommended to make blueprint subclasses of C# classes like you would with C++ so designers can easily control properties and functionality of your systems.

### 4. Do I need to use C++?
Most likely yes. UnrealSharp can only access what is exposed to [reflection](#1-what-is-reflection) like Blueprints, so you will need an engineer to use C++ to expose certain systems or features.

### 5. What is the difference between `new T()` and `NewObject<T>()>`?
Use `NewObject<T>()` for any classes inheriting from `uobject`. `new T()` does not work with constructing `uobject`'s, trying to would result in creating an object with no underlying `uobject` or blueprint subclass.  

### 6. Can I make a C# plugin?
Not yet but it is planned.
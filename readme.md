<!--
GENERATED FILE - DO NOT EDIT
This file was generated by [MarkdownSnippets](https://github.com/SimonCropp/MarkdownSnippets).
Source File: /readme.source.md
To change this file edit the source file and then run MarkdownSnippets.
-->

# <img src="/src/icon.png" height="30px"> PackageUpdate

[![Build status](https://ci.appveyor.com/api/projects/status/sq3dnh0uyl7sf9uv/branch/master?svg=true)](https://ci.appveyor.com/project/SimonCropp/PackageUpdate)
[![NuGet Status](https://img.shields.io/nuget/v/PackageUpdate.svg)](https://www.nuget.org/packages/PackageUpdate/)

A [dotnet tool](https://docs.microsoft.com/en-us/dotnet/core/tools/global-tools) that updates packages for all solutions in a directory.

<!-- toc -->
## Contents

  * [Installation](#installation)
  * [Usage](#usage)
    * [Arguments](#arguments)
    * [Behavior](#behavior)
  * [PackageUpdateIgnores](#packageupdateignores)
  * [Add to Windows Explorer](#add-to-windows-explorer)
  * [Security contact information](#security-contact-information)<!-- endtoc -->


## NuGet package

https://nuget.org/packages/PackageUpdate/


## Installation

Ensure [dotnet CLI is installed](https://docs.microsoft.com/en-us/dotnet/core/tools/).

Install [PackageUpdate](https://nuget.org/packages/PackageUpdate/)

```ps
dotnet tool install -g PackageUpdate
```


## Usage

```ps
packageupdate C:\Code\TargetDirectory
```

If no directory is passed the current directory will be used.


### Arguments


#### Target Directory

```ps
packageupdate C:\Code\TargetDirectory
```

```ps
packageupdate -t C:\Code\TargetDirectory
```

```ps
packageupdate --target-directory C:\Code\TargetDirectory
```


#### Package

The package name to update. If not specified, all packages will be updated.

```ps
packageupdate -p packageName
```

```ps
packageupdate --package packageName
```


### Behavior

 * Recursively scan the target directory for all directories containing a `.sln` file.
 * Perform a [dotnet restore](https://docs.microsoft.com/en-us/dotnet/core/tools/dotnet-restore) on the directory.
 * Recursively scan the directory for `*.csproj` files.
 * Call [dotnet list package](https://docs.microsoft.com/en-us/dotnet/core/tools/dotnet-list-package) to get the list of pending packages.
 * Call [dotnet add package](https://docs.microsoft.com/en-us/dotnet/core/tools/dotnet-add-package) with the package and version.


## PackageUpdateIgnores

When processing multiple directories, it is sometimes desirable to "always ignore" certain directories. This can be done by adding a `PackageUpdateIgnores` environment variable:

```
setx PackageUpdateIgnores "AspNetCore,EntityFrameworkCore"
```

The value is comma separated.


## Add to Windows Explorer

Use [/src/context-menu.reg](context-menu.reg) to add PackageUpdate to the Windows Explorer context menu.

<!-- snippet: context-menu.reg -->
<a id='snippet-context-menu.reg'/></a>
```reg
Windows Registry Editor Version 5.00
[HKEY_CLASSES_ROOT\Directory\Shell]
@="none"
[HKEY_CLASSES_ROOT\Directory\shell\packageupdate]
"MUIVerb"="run packageupdate"
"Position"="bottom"
[HKEY_CLASSES_ROOT\Directory\Background\shell\packageupdate]
"MUIVerb"="run packageupdate"
"Position"="bottom"
[HKEY_CLASSES_ROOT\Directory\shell\packageupdate\command]
@="cmd.exe /c packageupdate \"%V\""
[HKEY_CLASSES_ROOT\Directory\Background\shell\packageupdate\command]
@="cmd.exe /c packageupdate \"%V\""
```
<sup><a href='/src/context-menu.reg#L1-L13' title='File snippet `context-menu.reg` was extracted from'>snippet source</a> | <a href='#snippet-context-menu.reg' title='Navigate to start of snippet `context-menu.reg`'>anchor</a></sup>
<!-- endsnippet -->


## Security contact information

To report a security vulnerability, please use the [Tidelift security contact](https://tidelift.com/security). Tidelift will coordinate the fix and disclosure.


## Release Notes

See [closed milestones](../../milestones?state=closed).


## Icon

[Update](https://thenounproject.com/search/?q=update&i=2060555) by [Andy Miranda](https://thenounproject.com/andylontuan88) from [The Noun Project](https://thenounproject.com/).

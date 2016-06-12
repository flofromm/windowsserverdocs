---
title: path
ms.custom: na
ms.prod: windows-server-2012
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1bfa1349-e79a-472b-a9e6-d7a91149ae8f
---
# path
Sets the command path in the path environment variable \(the set of directories used to search for executable files\). if used without parameters, **path** displays the current command path.

for examples of how to use this command, see [Examples](#BKMK_examples).

## Syntax

```
path [[<Drive>:]<path>[;...][;%path%]]
path ;
```

## Parameters

|Parameter|Description|
|-------------|---------------|
|\[<Drive>:\]<path>|Specifies the drive and directory to set in the command path.|
|;|Separates directories in the command path. if used without other parameters, **;** clears the existing command paths from the path environment variable and directs cmd.exe to search only in the current directory.|
|%path%|appends the command path to the existing set of directories listed in the path environment variable.|
|\/?|Displays help at the command prompt.|

## remarks

-   When you include **%path%** in the syntax, cmd.exe replaces it with the command path values found in the path environment variable, eliminating the need to manually enter these values at the command prompt.

-   The current directory is always searched before the directories specified in the command path.

-   You might have files in a directory that share the same file name but have different extensions. for example, you might have a file named Accnt.com that starts an accounting program and another file named Accnt.bat that connects your server to the accounting system network.

    The Windows operating system searches for a file by using default file name extensions in the following order of precedence: .exe, .com, .bat, and .cmd. To run Accnt.bat when Accnt.com exists in the same directory, you must include the .bat extension at the command prompt.

-   if two or more files in the command path have the same file name and extension, **path** first searches for the specified file name in the current directory. Then it searches the directories in the command path in the order that they are listed in the path environment variable.

-   if you place the **path** command in your Autoexec.nt file, the Windows operating system automatically appends the specified MS\-DOS subsystem search path every time you log on to your computer. cmd.exe does not use the Autoexec.nt file. When started from a shortcut, cmd.exe inherits the environment variables set in My computer\/Properties\/Advanced\/Environment.

## <a name="BKMK_examples"></a>Examples
To search the paths C:\\User\\Taxes, B:\\User\\Invest, and B:\\Bin for external commands, type:

`path c:\user\taxes;b:\user\invest;b:\bin`

#### additional references
[Command-Line Syntax Key](commandline-syntax-key.md)


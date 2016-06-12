---
title: chcp
ms.custom: na
ms.prod: windows-server-2012
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: dc7b1c71-7b80-443d-9cf1-9bcf305aa1fd
---
# chcp
changes the active console code page. if used without parameters, **chcp** displays the number of the active console code page.

for examples of how to use this command, see [Examples](#BKMK_examples).

## Syntax

```
chcp [<NNN>]
```

## Parameters

|Parameter|Description|
|-------------|---------------|
|<NNN>|Specifies the code page.|
|\/?|Displays help at the command prompt.|

The following table lists each supported code page and its country\/region or language:

|Code page|Country\/region or language|
|-------------|-------------------------------|
|437|United States|
|850|Multilingual \(Latin I\)|
|852|Slavic \(Latin II\)|
|855|Cyrillic \(Russian\)|
|857|Turkish|
|860|Portuguese|
|861|Icelandic|
|863|Canadian\-French|
|865|Nordic|
|866|Russian|
|869|modern Greek|

## remarks

-   Only the original equipment manufacturer \(OEM\) code page that is installed with Windows appears correctly in a Command prompt window that uses Raster fonts. Other code pages appear correctly in full\-screen mode or in Command prompt windows that use Truetype fonts.

-   You do not need to prepare code pages \(as in MS\-DOS\).

-   Programs that you start after you assign a new code page use the new code page. However, programs \(except cmd.exe\) that you start before you assign the new code page use the original code page.

## <a name="BKMK_examples"></a>Examples
To view the active code page setting, type:

```
chcp
```

A message similar to the following appears:

`active code page: 437`

To change the active code page to 850 \(Multilingual\), type:

```
chcp 850
```

if the specified code page is invalid, the following error message appears:

`Invalid code page`

#### additional references
[Command-Line Syntax Key](commandline-syntax-key.md)


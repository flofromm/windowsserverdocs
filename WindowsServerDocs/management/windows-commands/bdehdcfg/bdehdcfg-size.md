---
title: bdehdcfg: size
ms.custom: na
ms.prod: windows-server-2012
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 80f55b1d-a28d-4edf-9997-1fb918b7b5a1
---
# bdehdcfg: size
Specifies the size of the system partition when a new system drive is being created. for an example of how this command can be used, see [Examples](#BKMK_Examples).

## Syntax

```
bdehdcfg -target {default|unallocated|<DriveLetter> shrink} -size <SizeinMB>
```

### Parameters

|Parameter|Description|
|-------------|---------------|
|<SizeinMB>|Indicates the number of megabytes \(MB\) to use for the new partition.|

## remarks
if you do not specify a size, the tool will use the default value of 300 MB. The minimum size of the system drive is 100 MB. if you will store system recovery or other system tools on the system partition, you should increase the size accordingly.

> [!NOTE]
> The **size** command cannot be combined with the **target**  <DriveLetter> **merge** command.

## <a name="BKMK_Examples"></a>Examples
The following example illustrates using the **size** command to allocate 500 MB to the default system drive.

```
bdehdcfg -target default -size 500
```

## additional references

-   [Command-Line Syntax Key](../commandline-syntax-key.md)

-   [bdehdcfg](../bdehdcfg.md)


---
title: bitsadmin getreplydata
ms.custom: na
ms.prod: windows-server-2012
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 819f97d5-b255-4b2d-9f63-0daa73915434
---
# bitsadmin getreplydata
Retrieves the server's reply data in hexadecimal format.

## Syntax

```
bitsadmin /GetReplyData <Job>
```

## Parameters

|Parameter|Description|
|-------------|---------------|
|Job|The job's display name or GUID|

## remarks
Valid only for upload\-reply jobs.

## <a name="BKMK_examples"></a>Examples
The following example retrieves the reply data for the job named *myDownloadJob*.

```
C:\>bitsadmin /GetReplyData myDownloadJob
```

## additional references
[Command-Line Syntax Key](../commandline-syntax-key.md)


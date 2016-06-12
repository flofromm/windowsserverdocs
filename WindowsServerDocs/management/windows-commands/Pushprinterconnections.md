---
title: pushprinterconnections
ms.custom: na
ms.prod: windows-server-2012
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c30afb97-b149-478f-a4b9-2cbc25361818
author: vhorne
---
# pushprinterconnections
Reads deployed printer Connection settings from Group Policy, and deploys\/removes printer connections as needed.  
  
## Syntax  
  
```  
pushprinterconnections <-log> <-?>  
```  
  
### Parameters  
  
|Parameter|Description|  
|-------------|---------------|  
|<\-log>|Writes a per user debug log file to %temp, or writes a per machine debug log to %windir%\\temp.|  
|<\-?>|Displays help at the command prompt.|  
  
## remarks  
This utility is for use in machine startup or user logon scripts, and should not be run from the command line.  
  
## additional references  
  
-   [Command-Line Syntax Key](commandline-syntax-key.md)  
  
-   [deploy printers by Using Group Policy](http://go.microsoft.com/fwlink/?LinkId=230627)  
  

---
title: query session
ms.custom: na
ms.prod: windows-server-2012
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: abc0ace8-0b74-4b6e-a937-a78bb4b61a1f
---
# query session
Displays information about sessions on a remote Desktop Session Host \(rd Session Host\) server.

The list includes information not only about active sessions but also about other sessions that the server runs.

for examples of how to use this command, see [Examples](#BKMK_examples).

> [!NOTE]
> In Windows Server 2008 R2, Terminal Services was renamed remote Desktop Services. To find out what's new in the latest version, see [What’s New in remote Desktop Services in Windows Server 2012](http://technet.microsoft.com/library/hh831527) in the Windows Server TechNet Library.

## Syntax

```
query session [<SessionName> | <UserName> | <SessionID>] [/server:<ServerName>] [/mode] [/flow] [/connect] [/counter]
```

## Parameters

|Parameter|Description|
|-------------|---------------|
|<SessionName>|Specifies the name of the session that you want to query.|
|<UserName>|Specifies the name of the user whose sessions you want to query.|
|<SessionID>|Specifies the ID of the session that you want to query.|
|\/server:<ServerName>|Identifies the rd Session Host server to query. The default is the current server.|
|\/mode|Displays current line settings.|
|\/flow|Displays current flow\-control settings.|
|\/connect|Displays current connect settings.|
|\/counter|Displays current counters information, including the total number of sessions created, disconnected, and reconnected.|
|\/?|Displays help at the command prompt.|

## remarks

-   A user can always query the session to which the user is currently logged on. To query other sessions, the user must have query Information special access permission.

-   if you do not specify a session by using <*SessionName*>, <*UserName*>, or <*SessionID*>, **query session** displays information about all active sessions in the system.

-   When **query session** returns information, a greater than \(>\) symbol is displayed before the current session. Following is sample output for **query session**:

    ```
    C:\>query session
     SESSIONNAME    USERNAME       ID STatE  type   DEVICE
    >console        Administrator1  0 active wdcon
     rdp-tcp#1      User1           1 active wdtshare
     rdp-tcp                        2 listen wdtshare
                                    4 idle
                                    5 idle
    ```

    The greater than \(>\) symbol indicates the current session. SESSIONNAME specifies the name assigned to the session. USERNAME indicates the user name of the user connected to the session. STatE provides information about the current state of the session. type indicates the session type. DEVICE, which is not present for the console or network\-connected sessions, is the device name assigned to the session. The comment following session information is from the session profile. Any sessions in which the initial state is configured as DISABLED do not show up in the **query session** list until they are enabled.

## <a name="BKMK_examples"></a>Examples

-   To display information about all active sessions on server SERver2, type:

    ```
    query session /server:SERver2
    ```

-   To display information about active session modeM02, type:

    ```
    query session modeM02
    ```

#### additional references
[Command-Line Syntax Key](../commandline-syntax-key.md)

[query](../query.md)

[remote Desktop Services &#40;Terminal Services&#41; Command Reference](../commands-by-server-role/remote-desktop-services-terminal-services-command-reference.md)


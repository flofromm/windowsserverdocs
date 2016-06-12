---
title: dfsdiag TestReferral
ms.custom: na
ms.prod: windows-server-2012
ms.reviewer: na
ms.suite: na
ms.technology: 
  - techgroup-storage
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 877c60dc-e993-4bd5-87dd-e892e3f98a1a
---
# dfsdiag TestReferral
Checks Distributed File System \(DFS\) referrals by performing the following tests:

-   When you use the DFSpath parameter without arguments, this command validates that the referral list includes all trusted domains.

-   When you specify a domain, the command performs a health check of domain controllers \(dfsdiag \/testdcs\) and tests the site associations and domain cache of the local host.

-   When you specify a domain and \\SYSvol or \\NETLOGON, in addition to performing the same health checks as when you specify a domain, the command checks that the time To Live \(TTL\) of SYSvol or NETLOGON referrals match the default value of 900 seconds.

-   When you specify a namespace root, in addition to performing the same health checks as when you specify a domain, the command performs a DFS configuration check \(dfsdiag \/TestDFSConfig\) and a namespace integrity check \(dfsdiag \/TestDFSIntegrity\).

-   When you specify a DFS folder \(link\), in addition to performing the same health checks as when you specify a namespace root, the command validates the site configuration for folder targets \(dfsdiag \/testsites\) and validates the site association of the local host.

for examples of how this command can be used, see [Examples](assetId:///c6d43992-8243-4f0a-8605-3152c8a8fe9a#BKMK_Examples).

## Syntax

```
dfsdiag /TestReferral /DFSpath:<DFS path for getting referrals> [/Full]
```

### Parameters

|Parameter|Description|
|-------------|---------------|
|\/DFSpath:<path for getting referrals>|This DFS path can be one of the following:<br /><br />-   \(blank\): Tests trusted domains.<br />-   \\\\Domain: Domain controller referrals.<br />-   \\\\Domain\\SYSvol: SYSvol referrals.<br />-   \\\\Domain\\NETLOGON: NETLOGON referrals.<br />-   \\\\<Domain or server>\\<Namespace Root>: Namespace root referrals.<br />-   \\\\<Domain or server>\\<Namespace root>\\<DFS folder>: DFS folder \(link\) referrals.|
|\/Full|Applied only to Domain and Root  referrals. verifies the consistency of site association information between the registry and active directory Domain Services \(AD DS\).|

## <a name="BKMK_Examples"></a>Examples
To TBD, type:

```
dfsdiag /TestReferral /DFSpath:\\Contoso.com\MyNamespace
```

To TBD, type:

```
dfsdiag /TestReferral /DFSpath:
```

## additional references

-   [Command-Line Syntax Key](../commandline-syntax-key.md)


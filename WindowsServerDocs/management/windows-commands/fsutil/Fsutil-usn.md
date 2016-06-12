---
title: Fsutil usn
ms.custom: na
ms.prod: windows-server-2012
ms.reviewer: na
ms.suite: na
ms.technology: 
  - techgroup-storage
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 213d36d1-f4ba-4390-93be-72e23df03a67
---
# Fsutil usn
manages the update sequence number \(USN\) change journal.

## Syntax

```
fsutil usn [createjournal] m=<MaxSize> a=<Allocationdelta> <volumepath>
fsutil usn [deletejournal] {/D | /N} <volumepath>
fsutil usn [enumdata] <FileRef> <LowUSN> <HighUSN> <volumepath>
fsutil usn [queryjournal] <volumepath>
fsutil usn [readdata] <FileName>
```

## Parameters

|Parameter|Description|
|-------------|---------------|
|createjournal|creates a USN change journal.|
|m\=<MaxSize>|Specifies the maximum size, in bytes, that NTFS allocates for the change journal.|
|a\=<Allocationdelta>|Specifies the size, in bytes, of memory allocation that is added to the end and removed from the beginning of the change journal.|
|<volumepath>|Specifies the drive letter \(followed by a colon\).|
|deletejournal|deletes or disables an active USN change journal. **Caution:** deleting the change journal impacts the File Replication Service \(FRS\) and the Indexing Service, because it would require these services to perform a complete \(and time\-consuming\) scan of the volume. This in turn negatively impacts FRS SYSvol replication and replication between DFS link alternates while the volume is being rescanned.|
|\/d|Disables an active USN change journal, and returns input\/output \(I\/O\) control while the change journal is being disabled.|
|\/n|Disables an active USN change journal and returns I\/O control only after the change journal is disabled.|
|enumdata|Enumerates and lists the change journal entries between two specified boundaries.|
|<FileRef>|Specifies the ordinal position within the files on the volume at which the enumeration is to begin.|
|<LowUSN>|Specifies the lower boundary of the range of USN values used to filter the records that are returned. Only records whose last change journal USN is between or equal to the *LowUSN* and *HighUSN* member values are returned.|
|<HighUSN>|Specifies the upper boundary of the range of USN values used to filter the files that are returned.|
|queryjournal|Queries a volume's USN data to gather information about the current change journal, its records, and its capacity.|
|readdata|Reads the USN data for a file.|
|<FileName>|Specifies the full path to the file, including the file name and extension for example: C:\\documents\\filename.txt|

## remarks

-   About the USN change journal

    The USN change journal provides a persistent log of all changes made to files on the volume. As files, directories, and other NTFS objects are added, deleted, and modified, NTFS enters records into the USN change journal, one for each volume on the computer. Each record indicates the type of change and the object changed. New records are appended to the end of the stream.

    Programs can consult the USN change journal to determine all the modifications made to a set of files. The USN change journal is much more efficient than checking time stamps or registering for file notifications. The USN change journal is enabled and used by the Indexing Service, File Replication Service \(FRS\), remote Installation Services \(RIS\), and remote Storage.

-   Using **createjournal**

    if a change journal already exists on a volume, the **createjournal** parameter updates the change journal's *MaxSize* and *Allocationdelta* parameters. This enables you to expand the number of records that an active journal maintains without having to disable it.

-   Using **m**

    The change journal can grow larger than this target value, but the change journal is truncated at the next NTFS checkpoint to less than this value. NTFS examines the change journal and trims it when its size exceeds the value of *MaxSize* plus the value of *Allocationdelta*. at NTFS checkpoints, the operating system writes records to the NTFS log file that enable NTFS to determine what processing is required to recover from a failure.

-   Using **a**

    The change journal can grow to more than the sum of the values of *MaxSize* and *Allocationdelta* before being trimmed.

-   Using **deletejournal**

    deleting or disabling an active change journal is very time consuming, because the system must access all the records in the master file table \(MFT\) and set the last USN attribute to 0 \(zero\). This process can take several minutes, and it can continue after the system restarts, if a restart is necessary. During this process, the change journal is not considered active, nor is it disabled. While the system is disabling the journal, it cannot be accessed, and all journal operations return errors. You should use extreme care when disabling an active journal, because it adversely affects other applications that are using the journal.

## <a name="BKMK_examples"></a>Examples
To create a USN change journal on drive C, type:

```
fsutil usn createjournal m=1000 a=100 c:
```

To delete an active USN change journal on drive C, type:

```
fsutil usn deletejournal /d c:
```

To enumerate and list the change journal entries between two specified boundaries on drive C, type:

```
fsutil usn enumdata 1 0 1 c:
```

To query USN data for a volume on drive C, type:

```
fsutil usn queryjournal c:
```

To read the USN data for a file in the \\Temp folder on drive C, type:

```
fsutil usn readdata c:\temp\sample.txt
```

#### additional references
[Command-Line Syntax Key](../commandline-syntax-key.md)

[Fsutil]()


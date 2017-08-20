---
title: "DownloadFileType Value Set"
ms.custom: ""
ms.date: "07/10/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a527ebae-9828-4cab-9b4c-7b894818b888
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# DownloadFileType Value Set
Defines the file formats for a download request.

> [!NOTE]
> The downloaded **Csv** or **Tsv** file will be ZIP compressed.

## Syntax

```xml
\<xs:simpleType name="DownloadFileType">
  \<xs:restriction base="xs:string">
    \<xs:enumeration value="Csv" />
    \<xs:enumeration value="Tsv" />
  \</xs:restriction>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Csv|The file format is comma separated values (CSV).|
|Tsv|The file format is tab separated values (TSV).|

## Requirements
[!INCLUDE[reqbulk](../bulk-api/includes/reqbulk.md)]
## See Also
[DownloadCampaignsByAccountIds](../bulk-api/downloadcampaignsbyaccountids-service-operation.md)  
[DownloadCampaignsByCampaignIds](../bulk-api/downloadcampaignsbycampaignids-service-operation.md)  


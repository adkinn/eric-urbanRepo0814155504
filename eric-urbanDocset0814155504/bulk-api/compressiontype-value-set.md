---
title: "CompressionType Value Set"
ms.custom: ""
ms.date: "07/10/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9dec0902-4d30-4f67-9d43-cd1ae8f139eb
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# CompressionType Value Set
Defines the possible compression types for the file to download.

## Syntax

```xml
\<xs:simpleType name="CompressionType">
  \<xs:restriction base="xs:string">
    \<xs:enumeration value="Zip" />
    \<xs:enumeration value="GZip" />
  \</xs:restriction>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|GZip|The file should be GZIP compressed.|
|Zip|The file should be ZIP compressed.|

## Requirements
[!INCLUDE[reqbulk](../bulk-api/includes/reqbulk.md)]
## See Also
[DownloadCampaignsByAccountIds](../bulk-api/downloadcampaignsbyaccountids-service-operation.md)  
[DownloadCampaignsByCampaignIds](../bulk-api/downloadcampaignsbycampaignids-service-operation.md)  


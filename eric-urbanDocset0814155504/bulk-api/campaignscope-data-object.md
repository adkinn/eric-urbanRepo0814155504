---
title: "CampaignScope Data Object"
ms.custom: ""
ms.date: "07/10/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 20a1964b-5391-4e5c-89dc-90bc5d0f6d83
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# CampaignScope Data Object
Defines an object that identifies a campaign to download.

## Syntax

```xml
<xs:complexType name="CampaignScope">
  <xs:sequence>
    <xs:element minOccurs="0" name="CampaignId" type="xs:long" />
    <xs:element minOccurs="0" name="ParentAccountId" type="xs:long" />
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|`CampaignId`|The identifier of the campaign to download.|`long`|
|`ParentAccountId`|The identifier of the account that owns the campaign to download.|`long`|

## Requirements
[!INCLUDE[reqbulk](../bulk-api/includes/reqbulk.md)]
## See Also
[DownloadCampaignsByCampaignIds](../bulk-api/downloadcampaignsbycampaignids-service-operation.md)


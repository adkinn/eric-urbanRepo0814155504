---
title: "CampaignReportScope Data Object"
ms.custom: ""
ms.date: "05/08/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5fb111ef-2ef4-465d-96a1-c4bba410ab37
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# CampaignReportScope Data Object
Defines a campaign to include in the report.

## Syntax

```xml
\<xs:complexType name="CampaignReportScope">
  \<xs:sequence>
    \<xs:element name="AccountId" type="xs:long" />
    \<xs:element name="CampaignId" type="xs:long" />
  \</xs:sequence>
\</xs:complexType>
```

## <a name="elements"></a>Elements

|Element|Description|Data Type|Required/Optional|
|-----------|---------------|-------------|---------------------|
|*AccountId*|The identifier of the account that the campaign belongs to.|*long*|Required|
|*CampaignId*|The identifier of the campaign to limit the scope to.|*long*|Required|

## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]
## See Also
[AccountThroughAdGroupReportScope](../reporting-api/accountthroughadgroupreportscope-data-object.md)  
[AccountThroughCampaignReportScope](../reporting-api/accountthroughcampaignreportscope-data-object.md)  


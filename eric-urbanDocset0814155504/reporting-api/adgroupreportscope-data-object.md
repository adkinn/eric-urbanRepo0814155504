---
title: "AdGroupReportScope Data Object"
ms.custom: ""
ms.date: "05/08/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3a1e5865-7efb-4d56-b02c-c4299a5a1b6f
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AdGroupReportScope Data Object
Defines an ad group to include in the report.

## Syntax

```xml
\<xs:complexType name="AdGroupReportScope">
  \<xs:sequence>
    \<xs:element name="AccountId" type="xs:long" />
    \<xs:element name="CampaignId" type="xs:long" />
    \<xs:element name="AdGroupId" type="xs:long" />
  \</xs:sequence>
\</xs:complexType>
```

## <a name="elements"></a>Elements

|Element|Description|Data Type|Required/Optional|
|-----------|---------------|-------------|---------------------|
|*AccountId*|The identifier of the account that the ad group belongs to.|*long*|Required|
|*AdGroupId*|The identifier of the ad group to limit the scope to.|*long*|Required|
|*CampaignId*|The identifier of the campaign that the ad group belongs to.|*long*|Required|

## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]
## See Also
[AccountReportScope](../reporting-api/accountreportscope-data-object.md)  
[AccountThroughAdGroupReportScope](../reporting-api/accountthroughadgroupreportscope-data-object.md)  
[AccountThroughCampaignReportScope](../reporting-api/accountthroughcampaignreportscope-data-object.md)  


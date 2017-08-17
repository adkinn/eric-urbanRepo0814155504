---
title: "CampaignType Value Set"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c3222402-dd42-4916-b97b-9f54e5716922
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# CampaignType Value Set
Defines the possible campaign types.

## Syntax

```xml
<xs:simpleType name="CampaignType">
  <xs:list>
    <xs:simpleType>
      <xs:restriction base="xs:string">
        <xs:enumeration value="SearchAndContent" />
        <xs:enumeration value="Shopping" />
        <xs:enumeration value="DynamicSearchAds" />
      </xs:restriction>
    </xs:simpleType>
  </xs:list>
</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|DynamicSearchAds|The campaign is a Dynamic Search Ads campaign.|
|SearchAndContent|The campaign is a Search and Content campaign.|
|Shopping|The campaign is a Bing Shopping campaign.|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[Campaign](../campaign-api/campaign-data-object.md)  


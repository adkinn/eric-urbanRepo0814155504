---
title: "KeywordOpportunityType Value Set"
ms.custom: ""
ms.date: "06/07/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d1eabe94-4667-4079-9856-1850c076bb6b
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# KeywordOpportunityType Value Set
Defines the possible keyword opportunity types you can request when calling [GetKeywordOpportunities](../adinsight-api/getkeywordopportunities-service-operation.md).

## Syntax

```xml
<xs:simpleType name="KeywordOpportunityType">
  <xs:list>
    <xs:simpleType>
      <xs:restriction base="xs:string">
        <xs:enumeration value="BroadMatch">
        <xs:enumeration value="CampaignContext">
      </xs:restriction>
    </xs:simpleType>
  </xs:list>
</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|BroadMatch|The keyword opportunity will be suggested based on the marketplace impact of adding keywords with the broad match type.|
|CampaignContext|The keyword opportunity will be suggested based on the full context of the campaign, including existing keywords, landing page, and ad copy.|

## Requirements
[!INCLUDE[reqadint](../adinsight-api/includes/reqadint.md)]
## See Also
[GetKeywordOpportunities](../adinsight-api/getkeywordopportunities-service-operation.md)


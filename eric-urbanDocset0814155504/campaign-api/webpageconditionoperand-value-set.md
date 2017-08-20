---
title: "WebpageConditionOperand Value Set"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ccc55c33-e701-4963-8757-fe7d045090cd
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# WebpageConditionOperand Value Set
Defines the operands that can be applied to arguments of a webpage condition or criterion for dynamic search ads. 

## Syntax

```xml
<xs:simpleType name="WebpageConditionOperand">
  <xs:list>
    <xs:simpleType>
      <xs:restriction base="xs:string">
        <xs:enumeration value="Unknown"/>
        <xs:enumeration value="Url" />
        <xs:enumeration value="Category" />
        <xs:enumeration value="PageTitle" />
        <xs:enumeration value="PageContent" />
      </xs:restriction>
    </xs:simpleType>
  </xs:list>
</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Category|Set a condition that the argument must match one of the categories that Bing thinks is applicable for your site.|
|PageContent|Set a condition that the argument must match any of your site's content that is indexed by Bing.|
|PageTitle|Set a condition that the argument must match any of your site's page titles that are indexed by Bing.|
|Unknown|Reserved for future use.|
|Url|Set a condition that the argument must match any of your site's URLs that are indexed by Bing.|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]

## See Also
[WebpageCondition](../campaign-api/eventgoal-data-object.md)  

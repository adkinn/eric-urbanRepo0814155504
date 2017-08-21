---
title: "StringOperator Value Set"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7c19365d-09f9-4783-abbd-eb2f16c9cc9c
caps.latest.revision: 3
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# StringOperator Value Set
Defines the operators that can be applied to remarketing list rule item string values.

## Syntax

```xml
<xs:simpleType name="StringOperator">
  <xs:list>
    <xs:simpleType>
      <xs:restriction base="xs:string">
        <xs:enumeration value="None"/>
        <xs:enumeration value="Equals"/>
        <xs:enumeration value="Contains"/>
        <xs:enumeration value="BeginsWith"/>
        <xs:enumeration value="EndsWith"/>
        <xs:enumeration value="NotEquals"/>
        <xs:enumeration value="DoesNotContain"/>
        <xs:enumeration value="DoesNotBeginWith"/>
        <xs:enumeration value="DoesNotEndWith"/>
      </xs:restriction>
    </xs:simpleType>
  </xs:list>
</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|BeginsWith|Begin with the corresponding string value.|
|Contains|Contain the corresponding string value.|
|DoesNotBeginWith|Does not begin with the corresponding string value.|
|DoesNotContain|Does not contain the corresponding string value.|
|DoesNotEndWith|Does not end with the corresponding string value.|
|EndsWith|Does not end with the corresponding string value.|
|Equals|Equals the corresponding string value.|
|None|Reserved for future use.|
|NotEquals|Does not equal the corresponding string value.|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]

## See Also
[StringRuleItem](../campaign-api/stringruleitem-data-object.md)  
[CustomEventsRule](../campaign-api/customeventsrule-data-object.md)  
[RemarketingList](../campaign-api/remarketinglist-data-object.md)  

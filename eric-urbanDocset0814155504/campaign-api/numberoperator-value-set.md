---
title: "NumberOperator Value Set"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7047ef4b-7471-4843-a3a5-be1fa8d22947
caps.latest.revision: 2
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# NumberOperator Value Set
Defines the operators that can be applied to remarketing list rule item number values.

## Syntax

```xml
\<xs:simpleType name="NumberOperator">
  \<xs:list>
    \<xs:simpleType>
      \<xs:restriction base="xs:string">
        \<xs:enumeration value="None"/>
        \<xs:enumeration value="Equals"/>
        \<xs:enumeration value="GreaterThan"/>
        \<xs:enumeration value="LessThan"/>
        \<xs:enumeration value="GreaterThanEqualTo"/>
        \<xs:enumeration value="LessThanEqualTo"/>
      \</xs:restriction>
    \</xs:simpleType>
  \</xs:list>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Equals|Equals the corresponding number value.|
|GreaterThan|Greater than the corresponding number value.|
|GreaterThanEqualTo|Greater than or equal to the corresponding number value.|
|LessThan|Less than the corresponding number value.|
|LessThanEqualTo|Less than or equal to the corresponding number value.|
|None|Reserved for future use.|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]

## See Also
[CustomEventsRule](../campaign-api/customeventsrule-data-object.md)  
[RemarketingList](../campaign-api/remarketinglist-data-object.md)  
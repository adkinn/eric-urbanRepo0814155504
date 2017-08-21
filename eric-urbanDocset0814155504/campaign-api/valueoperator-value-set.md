---
title: "ValueOperator Value Set"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a5e56671-07ff-455f-b98f-696969fd8d91
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# ValueOperator Value Set
Defines the operators that can be applied to values within a conversion event goal. 

## Syntax

```xml
<xs:simpleType name="ValueOperator">
  <xs:list>
    <xs:simpleType>
      <xs:restriction base="xs:string">
        <xs:enumeration value="Equals" />
        <xs:enumeration value="LessThan" />
        <xs:enumeration value="GreaterThan" />
      </xs:restriction>
    </xs:simpleType>
  </xs:list>
</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Equals|The property should be equal to the corresponding value.|
|GreaterThan|The property should be greater than the corresponding value.|
|LessThan|The property should be less than the corresponding value.|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]

## See Also
[EventGoal](../campaign-api/eventgoal-data-object.md)  

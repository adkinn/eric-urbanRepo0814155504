---
title: "ExpressionOperator Value Set"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4c751969-978f-41fd-9aa6-2d0adb309bca
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# ExpressionOperator Value Set
Defines the operators that can be applied to expressions within a conversion goal. 

## Syntax

```xml
<xs:simpleType name="ExpressionOperator">
  <xs:list>
    <xs:simpleType>
      <xs:restriction base="xs:string">
        <xs:enumeration value="Equals" />
        <xs:enumeration value="BeginsWith" />
        <xs:enumeration value="RegularExpression" />       
        <xs:enumeration value="Contains" />
      </xs:restriction>
    </xs:simpleType>
  </xs:list>
</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|BeginsWith|The property should begin with the corresponding fixed string expression.|
|Contains|The property should contain the corresponding fixed string expression.|
|Equals|The property should be equal to the corresponding fixed string expression.|
|RegularExpression|The property should match the corresponding regular expression.|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]

## See Also
[UrlGoal](../campaign-api/urlgoal-data-object.md)  
[EventGoal](../campaign-api/eventgoal-data-object.md)  

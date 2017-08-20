---
title: "Minute Value Set"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c40161f7-57ca-4457-9b9f-a2261f266ea8
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Minute Value Set
Defines the possible minute values for ad extension scheduling or day and time criterion.

## Syntax

```xml
<xs:simpleType name="Minute">
  <xs:restriction base="xs:string">
    <xs:enumeration value="Zero" />
    <xs:enumeration value="Fifteen" />
    <xs:enumeration value="Thirty" />
    <xs:enumeration value="FortyFive" />
  </xs:restriction>
</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Zero|The starting or ending minute of the hour range is zero.|
|Fifteen|The starting or ending minute of the hour range is fifteen.|
|Thirty|The starting or ending minute of the hour range is thirty.|
|FortyFive|The starting or ending minute of the hour range is forty-five.|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[DayTime](../campaign-api/daytime-data-object.md)  
[DayTimeCriterion](../campaign-api/daytimecriterion-data-object.md)  


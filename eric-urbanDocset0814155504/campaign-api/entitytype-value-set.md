---
title: "EntityType Value Set"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4b26ecda-fe9a-4a26-80b5-036655641f91
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# EntityType Value Set
Defines the possible types of entities.

## Syntax

```xml
<xs:simpleType name="EntityType">
  <xs:restriction base="xs:string">
    <xs:enumeration value="Campaign" />
    <xs:enumeration value="AdGroup" />
    <xs:enumeration value="Target" />
    <xs:enumeration value="Ad" />
    <xs:enumeration value="Keyword" />
    <xs:enumeration value="AdExtension" />
  </xs:restriction>
</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Ad|Request editorial appeal or status for ads.|
|AdExtension|Reserved for future use.|
|AdGroup|Reserved for future use.|
|Campaign|Reserved for future use.|
|Keyword|Request editorial appeal or status for keywords.|
|Target|Reserved for future use.|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[AppealEditorialRejections](../campaign-api/appealeditorialrejections-service-operation.md)  
[GetEditorialReasonsByIds](../campaign-api/geteditorialreasonsbyids-service-operation.md)  


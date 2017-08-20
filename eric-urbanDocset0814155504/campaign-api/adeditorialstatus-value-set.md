---
title: "AdEditorialStatus Value Set"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e79f0dfa-2c74-4219-86a8-c2e1a1b810a0
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AdEditorialStatus Value Set
Defines the editorial review status values of an ad.

## Syntax

```xml
<xs:simpleType name="AdEditorialStatus">
  <xs:restriction base="xs:string">
    <xs:enumeration value="Active" />
    <xs:enumeration value="Disapproved" />
    <xs:enumeration value="Inactive" />
    <xs:enumeration value="ActiveLimited" />
  </xs:restriction>
</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Active|The ad passed editorial review.|
|ActiveLimited|The ad passed editorial review in one or more markets, and one or more elements of the ad is undergoing editorial review in another market. For example the ad passed editorial review for Canada and is still pending review in the United States.|
|Disapproved|The ad failed editorial review.|
|Inactive|One or more elements of the ad is undergoing editorial review.|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[Ad](../campaign-api/ad-data-object.md)  
[GetAdsByEditorialStatus](../campaign-api/getadsbyeditorialstatus-service-operation.md)  


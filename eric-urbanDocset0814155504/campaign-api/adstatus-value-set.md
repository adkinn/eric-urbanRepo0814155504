---
title: "AdStatus Value Set"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a205730b-49ed-473a-a8d2-af807f8a5b45
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AdStatus Value Set
Defines the possible status values of an ad.

## Syntax

```xml
\<xs:simpleType name="AdStatus">
  \<xs:restriction base="xs:string">
    \<xs:enumeration value="Inactive" />
    \<xs:enumeration value="Active" />
    \<xs:enumeration value="Paused" />
    \<xs:enumeration value="Deleted" />
  \</xs:restriction>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Active|The ad can be served.|
|Deleted|This status is for internal use only. Because all Get operations do not return deleted objects, you will not see an object with this status.|
|Inactive|The ad is undergoing editorial review or has failed editorial review. To determine the  ad editorial status, see [AdEditorialStatus](../campaign-api/adeditorialstatus-value-set.md).|
|Paused|The ad will not serve until the owner resumes it.|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[Ad](../campaign-api/ad-data-object.md)


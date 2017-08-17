---
title: "AdGroupStatus Value Set"
ms.custom: ""
ms.date: "08/15/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5de54e64-f20c-4282-a6e7-d1a7b9092a62
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AdGroupStatus Value Set
Defines the possible status values of an ad group.

## Syntax

```xml
\<xs:simpleType name="AdGroupStatus">
  \<xs:restriction base="xs:string">
    \<xs:enumeration value="Active" />
    \<xs:enumeration value="Paused" />
    \<xs:enumeration value="Expired" />
    \<xs:enumeration value="Deleted" />
  \</xs:restriction>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Active|The ad group is active, which indicates that the ad group’s ads can be served.|
|Deleted|This status is for internal use only. Because all Get operations do not return deleted objects, you will not see an object with this status.|
|Expired|The ad group expired. This status is set if you specify an end date for the ad group and the end date passes.|
|Paused|The ad group is paused, which indicates that the ad group’s ads will not serve. Ads and keywords that you add in this state are subject to editorial review.|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[AdGroup](../campaign-api/adgroup-data-object.md)


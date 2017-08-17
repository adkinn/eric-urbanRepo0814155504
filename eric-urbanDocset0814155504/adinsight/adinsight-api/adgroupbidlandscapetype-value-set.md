---
title: "AdGroupBidLandscapeType Value Set"
ms.custom: ""
ms.date: "06/07/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8886e310-081c-44ba-9422-a73af1062233
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AdGroupBidLandscapeType Value Set
Defines the possible values that indicate whether all or a subset of an ad group's existing keywords are used to determine the bid landscape.

## Syntax

```xml
\<xs:simpleType name="AdGroupBidLandscapeType">
  \<xs:restriction base="xs:string">
    \<xs:enumeration value="Uniform" />
    \<xs:enumeration value="DefaultBidOnly" />
  \</xs:restriction>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|DefaultBidOnly|Only existing keywords that use the ad group's default bid are used to determine the bid landscape.|
|Uniform|All of an ad group's existing keywords are used to determine the bid landscape.|

## Requirements
[!INCLUDE[reqadint](../adinsight-api/includes/reqadint.md)]
## See Also
[AdGroupBidLandscape](../adinsight-api/adgroupbidlandscape-data-object.md)  
[AdGroupBidLandscapeInput](../adinsight-api/adgroupbidlandscapeinput-data-object.md)  


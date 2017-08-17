---
title: "TargetAdPosition Value Set"
ms.custom: ""
ms.date: "06/07/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0f93fb3d-8c50-4dd3-8b6d-6e6f3e1274d9
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# TargetAdPosition Value Set
Defines the possible positions where you can target an ad to appear in the search results or on a content-based webpage.

## Syntax

```xml
\<xs:simpleType name="TargetAdPosition">
  \<xs:restriction base="xs:string">
    \<xs:enumeration value="MainLine1" />
    \<xs:enumeration value="MainLine" />
    \<xs:enumeration value="SideBar" />
  \</xs:restriction>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|MainLine1|Target the first position at the top of the search results page.|
|MainLine|Target the second, third, and fourth positions at the top of the search results page.|
|SideBar|Target any position on the right side of the search results page.|

## Requirements
[!INCLUDE[reqadint](../adinsight-api/includes/reqadint.md)]
## See Also
[GetEstimatedBidByKeywordIds](../adinsight-api/getestimatedbidbykeywordids-service-operation.md)  
[GetEstimatedBidByKeywords](../adinsight-api/getestimatedbidbykeywords-service-operation.md)  


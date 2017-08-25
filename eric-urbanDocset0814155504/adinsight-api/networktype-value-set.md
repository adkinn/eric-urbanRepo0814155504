---
title: "NetworkType Value Set"
ms.custom: ""
ms.date: "07/12/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bad50c29-1794-41e0-95d8-c95132d83700
caps.latest.revision: 3
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# NetworkType Value Set
Defines the possible search networks on which an ad can display. 

You can specify a network type when calling the [GetKeywordIdeas](../adinsight-api/getkeywordideas-service-operation.md) and [GetKeywordTrafficEstimates](../adinsight-api/getkeywordtrafficestimates-service-operation.md) operations. For more information about networks and ad distribution, see the [About Ad Distribution](http://help.bingads.microsoft.com/#apex/3/en/50871/0) help article.

## Syntax

```xml
<xs:simpleType name="NetworkType">
  <xs:restriction base="xs:string">
    <xs:enumeration value="OwnedAndOperatedAndSyndicatedSearch" />
    <xs:enumeration value="OwnedAndOperatedOnly" />
    <xs:enumeration value="SyndicatedSearchOnly" />
  </xs:restriction>
</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|OwnedAndOperatedAndSyndicatedSearch|Indicates that you want keyword ideas or traffic estimates for ads on owned and operated networks, as well as syndicated search networks.|
|OwnedAndOperatedOnly|Indicates that you want keyword ideas or traffic estimates for ads on only owned and operated networks.<br /><br />Owned and operated networks refer to the Bing?, AOL, and Yahoo search networks.|
|SyndicatedSearchOnly|Indicates that you want keyword ideas or traffic estimates for ads on only syndicated search networks.<br /><br />Syndicated search refers to partner sites that host Bing?, AOL, and Yahoo search.|

## Requirements
[!INCLUDE[reqadint](../adinsight-api/includes/reqadint.md)]
## See Also
[GetKeywordIdeas](../adinsight-api/getkeywordideas-service-operation.md)  
[GetKeywordTrafficEstimates](../adinsight-api/getkeywordtrafficestimates-service-operation.md)  

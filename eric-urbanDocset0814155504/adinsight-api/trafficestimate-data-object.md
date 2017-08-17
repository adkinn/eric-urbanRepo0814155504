---
title: "TrafficEstimate Data Object"
ms.custom: ""
ms.date: "07/12/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b6a51896-a324-4b39-9fd9-141df60564a7
caps.latest.revision: 3
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# TrafficEstimate Data Object
Defines an object that contains traffic estimates based on the campaign, ad group, and keyword criteria you specified when calling [GetKeywordTrafficEstimates](../adinsight-api/getkeywordtrafficestimates-service-operation.md).

## Syntax

```xml
\<xs:complexType name="TrafficEstimate">
  \<xs:sequence>
    \<xs:element minOccurs="0" name="AverageCpc" type="xs:double"/>
    \<xs:element minOccurs="0" name="AveragePosition" type="xs:double"/>
    \<xs:element minOccurs="0" name="Clicks" type="xs:double"/>
    \<xs:element minOccurs="0" name="Ctr" type="xs:double"/>
    \<xs:element minOccurs="0" name="Impressions" type="xs:double"/>
    \<xs:element minOccurs="0" name="TotalCost" type="xs:double"/>
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AverageCpc*|The estimated average CPC.<br /><br />The formula used to calculate the average CPC is (total cost / clicks).|*double*|
|*AveragePosition*|The estimated average CPC.<br /><br />The formula used to calculate the average CPC is (total cost / clicks).|*double*|
|*Clicks*|The estimated number of clicks per week.|*double*|
|*Ctr*|The estimated CTR.<br /><br />The formula used to calculate the CTR is (clicks / impressions) &#42; 100.|*double*|
|*Impressions*|The estimated number of impressions per week.|*double*|
|*TotalCost*|The estimated total cost per week.|*double*|

## Requirements
[!INCLUDE[reqadint](../adinsight-api/includes/reqadint.md)]
## See Also
[GetKeywordTrafficEstimates](../adinsight-api/getkeywordtrafficestimates-service-operation.md)  

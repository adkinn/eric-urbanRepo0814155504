---
title: "KeywordEstimate Data Object"
ms.custom: ""
ms.date: "07/12/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6f94a290-2211-407a-a197-a7bc2a71602f
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# KeywordEstimate Data Object
A suggested keyword with minimum and maximum traffic estimates. Traffic estimates include average CPC, average position, clicks, CTR, impressions, and total cost.

> [!NOTE]
> The estimates are not a prediction or guarantee of future performance. The estimates can vary depending on the filter criteria you provide in the [GetKeywordTrafficEstimates](../Ad Insight Version 11/getkeywordtrafficestimates-service-operation.md) service request.

## Syntax

```xml
\<xs:complexType name="KeywordEstimate">
  \<xs:sequence>
    \<xs:element xmlns:q8="http://schemas.datacontract.org/2004/07/Microsoft.BingAds.Advertiser.AdInsight.Api.DataContract.V11.Entity.Common" minOccurs="0" name="Keyword" nillable="true" type="q8:Keyword"/>
    \<xs:element minOccurs="0" name="Maximum" nillable="true" type="tns:TrafficEstimate"/>
    \<xs:element minOccurs="0" name="Minimum" nillable="true" type="tns:TrafficEstimate"/>
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Keyword*|The suggested keyword.|[Keyword](../Ad Insight Version 11/keyword-data-object.md)|
|*Maximum*|The maximum traffic estimate.<br/><br/>Traffic estimates include average CPC, average position, clicks, CTR, impressions, and total cost.|[TrafficEstimate](../Ad Insight Version 11/trafficestimate-data-object.md)|
|*Minimum*|The minimum traffic estimate.<br/><br/>Traffic estimates include average CPC, average position, clicks, CTR, impressions, and total cost.|[TrafficEstimate](../Ad Insight Version 11/trafficestimate-data-object.md)|

## Requirements
[!INCLUDE[reqadint](../Ad Insight Version 11/includes/reqadint.md)]
## See Also
[GetKeywordTrafficEstimates](../Ad Insight Version 11/getkeywordtrafficestimates-service-operation.md)  

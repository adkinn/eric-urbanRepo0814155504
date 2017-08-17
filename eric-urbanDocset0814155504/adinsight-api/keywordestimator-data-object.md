---
title: "KeywordEstimator Data Object"
ms.custom: ""
ms.date: "07/12/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b00666e5-a6ba-4e3c-8d23-30a60977bc39
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# KeywordEstimator Data Object
Contains a keyword estimators with your keyword level filter criteria for traffic estimates.

## Syntax

```xml
<xs:complexType name="KeywordEstimator">
  <xs:sequence>
    <xs:element xmlns:q7="http://schemas.datacontract.org/2004/07/Microsoft.BingAds.Advertiser.AdInsight.Api.DataContract.V11.Entity.Common" minOccurs="0" name="Keyword" nillable="true" type="q7:Keyword"/>
    <xs:element minOccurs="0" name="MaxCpc" nillable="true" type="xs:double"/>
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|Required|
|-----------|---------------|-------------|-------------|
|*Keyword*|The keyword used for traffic estimates.<br/><br/>You can request estimates for Phrase and Broad match types.|[Keyword](../adinsight-api/keyword-data-object.md)|Yes|
|*MaxCpc*|The maximum cost per click filter criteria for the keyword.<br/><br/>You can set the default maximum CPC for all of the ad group's keywords using the *MaxCpc* element of the [AdGroupEstimator](../adinsight-api/adgroupestimator-data-object.md) object. Use the keyword estimator if you want to override the max CPC for a specific keyword.|*double*|No|

## Requirements
[!INCLUDE[reqadint](../adinsight-api/includes/reqadint.md)]
## See Also
[GetKeywordTrafficEstimates](../adinsight-api/getkeywordtrafficestimates-service-operation.md)  

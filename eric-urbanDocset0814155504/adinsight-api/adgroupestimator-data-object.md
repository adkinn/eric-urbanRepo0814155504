---
title: "AdGroupEstimator Data Object"
ms.custom: ""
ms.date: "07/12/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 348e03a2-6812-4e4f-aacf-8171bf8c30c3
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AdGroupEstimator Data Object
Contains a list of keyword estimators with your keyword level filter criteria for traffic estimates.

## Syntax

```xml
\<xs:complexType name="AdGroupEstimator">
  \<xs:sequence>
    \<xs:element minOccurs="0" name="AdGroupId" nillable="true" type="xs:long"/>
    \<xs:element minOccurs="0" name="KeywordEstimators" nillable="true" type="tns:ArrayOfKeywordEstimator"/>
    \<xs:element minOccurs="0" name="MaxCpc" type="xs:double"/>
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|Required|
|-----------|---------------|-------------|-------------|
|*AdGroupId*|The ad group identifier.<br/><br/>This element is reserved for future use. The returned estimates are not based on any specific ad group.|*long*|No|
|*KeywordEstimators*|The list of keyword estimators with your keyword level filter criteria for traffic estimates.|[KeywordEstimator](../adinsight-api/keywordestimator-data-object.md) array|Yes|
|*MaxCpc*|The maximum cost per click filter criteria for all keyword estimates in the ad group.<br/><br/>You can override this setting for specific keywords with the corresponding keyword estimators.|*double*|Yes|

## Requirements
[!INCLUDE[reqadint](../adinsight-api/includes/reqadint.md)]
## See Also
[GetKeywordTrafficEstimates](../adinsight-api/getkeywordtrafficestimates-service-operation.md)  

---
title: "CampaignEstimator Data Object"
ms.custom: ""
ms.date: "07/12/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3f77198d-c931-48af-96f5-6f6a8a55116d
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# CampaignEstimator Data Object
Contains campaign filter criteria and a nested list of ad group and keyword level filter criteria for traffic estimates.

## Syntax

```xml
<xs:complexType name="CampaignEstimator">
  <xs:sequence>
    <xs:element minOccurs="0" name="AdGroupEstimators" nillable="true" type="tns:ArrayOfAdGroupEstimator"/>
    <xs:element minOccurs="0" name="CampaignId" nillable="true" type="xs:long"/>
    <xs:element xmlns:q5="http://schemas.datacontract.org/2004/07/Microsoft.BingAds.Advertiser.AdInsight.Api.DataContract.V11.Entity.Criterions" minOccurs="0" name="Criteria" nillable="true" type="q5:ArrayOfCriterion"/>
    <xs:element minOccurs="0" name="DailyBudget" type="xs:double"/>
    <xs:element xmlns:q6="http://schemas.datacontract.org/2004/07/Microsoft.BingAds.Advertiser.AdInsight.Api.DataContract.V11.Entity.Common" minOccurs="0" name="NegativeKeywords" nillable="true" type="q6:ArrayOfNegativeKeyword"/>
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|Required|
|-----------|---------------|-------------|-------------|
|*AdGroupEstimators*|The list of ad group estimators with your ad group and keyword level filter criteria for traffic estimates.|[AdGroupEstimator](../adinsight-api/adgroupestimator-data-object.md) array|Yes|
|*CampaignId*|The campaign identifier.<br/><br/>This element is reserved for future use. The returned estimates are not based on any specific campaign.|*long*|No|
|*Criteria*|The list of campaign level criteria for traffic estimates.<br/><br/>Do not try to instantiate a [Criterion](../adinsight-api/criterion-data-object.md). You can include one or more the following objects that derive from it: [DeviceCriterion](../adinsight-api/devicecriterion-data-object.md), [LanguageCriterion](../adinsight-api/languagecriterion-data-object.md), [LocationCriterion](../adinsight-api/locationcriterion-data-object.md), and [NetworkCriterion](../adinsight-api/networkcriterion-data-object.md).<br/><br/>The location, language, and network criterions are required for traffic estimates.|[Criterion](../adinsight-api/criterion-data-object.md) array|Yes|
|*DailyBudget*|The daily budget filter criteria for all keyword traffic estimates in the campaign.|*double*|No|
|*NegativeKeywords*|The list of negative keyword filter criteria for all keyword traffic estimates in the campaign.|[NegativeKeyword](../adinsight-api/negativekeyword-data-object.md) array|No|

## Requirements
[!INCLUDE[reqadint](../adinsight-api/includes/reqadint.md)]
## See Also
[GetKeywordTrafficEstimates](../adinsight-api/getkeywordtrafficestimates-service-operation.md)  

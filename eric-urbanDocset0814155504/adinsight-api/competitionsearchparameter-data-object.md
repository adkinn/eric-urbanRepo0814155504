---
title: "CompetitionSearchParameter Data Object"
ms.custom: ""
ms.date: "07/12/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6ed6793c-d2c7-4aa0-967a-785632329e8d
caps.latest.revision: 2
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# CompetitionSearchParameter Data Object
The competition search parameter filter that you can include when requesting keyword ideas.

If you do not include the competition search parameter when calling [GetKeywordIdeas](../adinsight-api/getkeywordideas-service-operation.md), then keyword ideas will be returned for all competition levels.

## Syntax

```xml
<xs:complexType name="CompetitionSearchParameter">
  <xs:complexContent mixed="false">
    <xs:extension base="tns:SearchParameter">
      <xs:sequence>
        <xs:element xmlns:q8="http://schemas.datacontract.org/2004/07/Microsoft.BingAds.Advertiser.AdInsight.Api.DataContract.V11.Entity.Common" minOccurs="0" name="CompetitionLevels" nillable="true" type="q8:ArrayOfCompetitionLevel"/>
      </xs:sequence>
    </xs:extension>
  </xs:complexContent>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*CompetitionLevels*|The competition levels that you want for the returned keyword ideas.<br/><br/>Competition levels are defined by the number of advertisers bidding on this keyword, relative to all other keywords across Bing Ads. Possible values are *Low*, *Medium*, and *High*.|[CompetitionLevel](../adinsight-api/competitionlevel-value-set.md) array|

## Requirements
[!INCLUDE[reqadint](../adinsight-api/includes/reqadint.md)]
## See Also
[GetKeywordIdeaCategories](../adinsight-api/getkeywordideacategories-service-operation.md)  
[GetKeywordIdeas](../adinsight-api/getkeywordideas-service-operation.md)  

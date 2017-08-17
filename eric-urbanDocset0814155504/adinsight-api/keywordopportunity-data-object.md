---
title: "KeywordOpportunity Data Object"
ms.custom: ""
ms.date: "06/07/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7843acf6-03af-471f-89e5-477556133b67
caps.latest.revision: 10
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# KeywordOpportunity Data Object
Defines an object that contains a suggested keyword and bid value.

## Syntax

```xml
\<xs:complexType name="KeywordOpportunity">
  \<xs:complexContent mixed="false">
    \<xs:extension base="tns:Opportunity">
      \<xs:sequence>
        \<xs:element type="xs:long" name="AdGroupId" minOccurs="0"/>
        \<xs:element type="xs:string" name="AdGroupName" minOccurs="0"/>
        \<xs:element type="xs:long" name="CampaignId" minOccurs="0"/>
        \<xs:element type="xs:string" name="CampaignName" minOccurs="0"/>
        \<xs:element type="xs:double" name="Competition" minOccurs="0"/>
        \<xs:element type="xs:double" name="EstimatedIncreaseInClicks" minOccurs="0"/>
        \<xs:element type="xs:double" name="EstimatedIncreaseInCost" minOccurs="0"/>
        \<xs:element type="xs:long" name="EstimatedIncreaseInImpressions" minOccurs="0"/>
        \<xs:element type="xs:int" name="MatchType" minOccurs="0"/>
        \<xs:element type="xs:long" name="MonthlySearches" minOccurs="0"/>
        \<xs:element type="xs:double" name="SuggestedBid" minOccurs="0"/>
        \<xs:element type="xs:string" name="SuggestedKeyword" minOccurs="0" nillable="true"/>
      \</xs:sequence>
    \</xs:extension>
  \</xs:complexContent>
\</xs:complexType>
```

## <a name="Elements"></a>Elements
The *KeywordOpportunity* object  inherits elements from the [Opportunity](../adinsight-api/opportunity-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#InheritedElements) below.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AdGroupId*|The identifier of the ad group to apply the suggested keyword to.|*long*|
|*AdGroupName*|The name of the ad group to apply the suggested keyword to.|*string*|
|*AverageCPC*|Broad match average CPC  in the marketplace.|*double*|
|*AverageCTR*|Broad match average CTR in the marketplace.|*double*|
|*CampaignId*|The identifier of the campaign that owns the ad group.|*long*|
|*CampaignName*|The name of the campaign that owns the ad group.|*string*|
|*ClickShare*|Broad match click share in the marketplace.|*double*|
|*Competition*|An indicator of competitive bids for this keyword relative to all search keywords. The competition score ranges from 0 to 1.00, where 0 indicates low competition and 1.00 indicates that there is a high number of advertisers competing for this keyword.|*double*|
|*EstimatedIncreaseInClicks*|Estimated increase in clicks if the opportunity is applied.|*long*|
|*EstimatedIncreaseInCost*|Estimated increase in cost if the opportunity is applied.|*long*|
|*EstimatedIncreaseInImpressions*|Estimated increase in impressions if the opportunity is applied.|*long*|
|*MatchType*|The match type that the suggested bid applies to. The following are the possible match-type values:<br /><br />1 – Exact match<br /><br />2 – Phrase match<br /><br />3 – Broad match|*int*|
|*MonthlySearches*|The estimated monthly volume of user search queries that may match the suggested keyword for the corresponding *MatchType* element.|*long*|
|*SuggestedBid*|The suggested bid that may result in your ads serving on the first page of the search query results.|*double*|
|*SuggestedKeyword*|The suggested keyword.|*string*|

## <a name="InheritedElements"></a>Inherited Elements
The *KeywordOpportunity* object inherits the following element from the [Opportunity](../adinsight-api/opportunity-data-object.md) object. 

> [!NOTE]
> The description below is specific to keyword opportunities, and might not apply to other objects that inherit the same element from the [Opportunity](../adinsight-api/opportunity-data-object.md) object.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*OpportunityKey*|An identifier that uniquely identifies the opportunity.|*string*|

## Requirements
[!INCLUDE[reqadint](../adinsight-api/includes/reqadint.md)]
## See Also
[GetKeywordOpportunities](../adinsight-api/getkeywordopportunities-service-operation.md)


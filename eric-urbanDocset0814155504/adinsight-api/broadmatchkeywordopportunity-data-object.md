---
title: "BroadMatchKeywordOpportunity Data Object"
ms.custom: ""
ms.date: "06/07/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f78e2f02-12eb-47d1-8708-eeadd8b53909
caps.latest.revision: 10
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# BroadMatchKeywordOpportunity Data Object
Defines an object that contains the marketplace impact statistics of including broad match type keyword bids.

## Syntax

```xml
<xs:complexType name="BroadMatchKeywordOpportunity">
  <xs:complexContent mixed="false">
    <xs:extension base="tns:KeywordOpportunity">
      <xs:sequence>
        <xs:element type="xs:double" name="AverageCPC" minOccurs="0"/>
        <xs:element type="xs:double" name="AverageCTR" minOccurs="0"/>
        <xs:element type="xs:double" name="ClickShare" minOccurs="0"/>
        <xs:element type="xs:double" name="ImpressionShare" minOccurs="0"/>
        <xs:element type="xs:double" name="ReferenceKeywordBid" minOccurs="0"/>
        <xs:element type="xs:long" name="ReferenceKeywordId" minOccurs="0"/>
        <xs:element type="xs:int" name="ReferenceKeywordMatchType" minOccurs="0"/>
        <xs:element type="tns:ArrayOfBroadMatchSearchQueryKPI" name="SearchQueryKPIs" minOccurs="0" nillable="true"/>
      </xs:sequence>
    </xs:extension>
  </xs:complexContent>
</xs:complexType>
```

## <a name="Elements"></a>Elements
The *BroadMatchKeywordOpportunity* object inherits elements from the [KeywordOpportunity](../adinsight-api/keywordopportunity-data-object.md) and [Opportunity](../adinsight-api/opportunity-data-object.md) objects. For a list of the inherited elements, see [Inherited Elements](#InheritedElements) below.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AverageCPC*|Broad match average CPC  in the marketplace.|*double*|
|*AverageCTR*|Broad match average CTR in the marketplace.|*double*|
|*ClickShare*|Broad match click share in the marketplace.|*double*|
|*ImpressionShare*|Broad match impression share in the marketplace.|*double*|
|*ReferenceKeywordBid*|The bid of an existing reference keyword used by the service to offer the keyword opportunity.|*double*|
|*ReferenceKeywordId*|The identifier of an existing reference keyword used by the service to offer the keyword opportunity.|*long*|
|*ReferenceKeywordMatchType*|The match type of an existing reference keyword used by the service to offer the keyword opportunity.<br /><br />The following are the possible match-type values:<br /><br />1 – Exact match<br /><br />2 – Phrase match|*int*|
|*SearchQueryKPIs*|A list of up to three broad match search query KPI objects. Each item contains search query statistics of including broad match type keyword bids|[BroadMatchSearchQueryKPI](../adinsight-api/broadmatchsearchquerykpi-data-object.md) array|

## <a name="InheritedElements"></a>Inherited Elements
### <a name="InheritedElementsKeywordOpportunity"></a>Inherited Elements from KeywordOpportunity
The *BroadMatchKeywordOpportunity* object inherits the following elements from the [KeywordOpportunity](../adinsight-api/keywordopportunity-data-object.md) object. 

> [!NOTE]
> The descriptions below are specific to broad match keyword opportunities, and might not apply to other objects that inherit the same elements from the [KeywordOpportunity](../adinsight-api/keywordopportunity-data-object.md) object.

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

### <a name="InheritedElementsOpportunity"></a>Inherited Elements from Opportunity
The [KeywordOpportunity](../adinsight-api/keywordopportunity-data-object.md) object inherits the following element from the [Opportunity](../adinsight-api/opportunity-data-object.md) object. 

> [!NOTE]
> The description below is specific to broad match keyword opportunities, and might not apply to other objects that inherit the same element from the [Opportunity](../adinsight-api/opportunity-data-object.md) object.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*OpportunityKey*|An identifier that uniquely identifies the opportunity.|*string*|

## Requirements
[!INCLUDE[reqadint](../adinsight-api/includes/reqadint.md)]
## See Also
[GetKeywordOpportunities](../adinsight-api/getkeywordopportunities-service-operation.md)  
[KeywordOpportunity](../adinsight-api/keywordopportunity-data-object.md)  


---
title: "BidOpportunity Data Object"
ms.custom: ""
ms.date: "06/07/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 618912fc-8288-448c-a530-9adce1f662ff
caps.latest.revision: 10
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# BidOpportunity Data Object
Defines an object that contains the suggested bid with estimated clicks and impressions opportunities.

> [!NOTE]
> The bid opportunity is an estimate based on the last 7 days of performance data, and not a prediction or guarantee of future performance.

## Syntax

```xml
\<xs:complexType name="BidOpportunity">
  \<xs:complexContent mixed="false">
    \<xs:extension base="tns:Opportunity">
      \<xs:sequence>
        \<xs:element minOccurs="0" name="AdGroupId" type="xs:long" />
        \<xs:element minOccurs="0" name="CampaignId" type="xs:long" />
        \<xs:element minOccurs="0" name="CurrentBid" type="xs:double" />
        \<xs:element minOccurs="0" name="EstimatedIncreaseInClicks" type="xs:double" />
        \<xs:element minOccurs="0" name="EstimatedIncreaseInCost" type="xs:double" />
        \<xs:element minOccurs="0" name="EstimatedIncreaseInImpressions" type="xs:long" />
        \<xs:element minOccurs="0" name="KeywordId" type="xs:long" />
        \<xs:element minOccurs="0" name="MatchType" type="xs:string" />
        \<xs:element minOccurs="0" name="SuggestedBid" type="xs:double" />
      \</xs:sequence>
    \</xs:extension>
  \</xs:complexContent>
\</xs:complexType>
```

## <a name="Elements"></a>Elements
The *BidOpportunity* object inherits elements from the [Opportunity](../adinsight-api/opportunity-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#InheritedElements) below.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AdGroupId*|The identifier of the ad group that owns the keyword.|*long*|
|*CampaignId*|The identifier of the campaign for the ad group that owns the keyword.|*long*|
|*CurrentBid*|The current keyword bid amount specified for the match type in the *MatchType* element.|*double*|
|*EstimatedIncreaseInClicks*|The estimated clicks opportunities corresponding to the suggested bid.|*double*|
|*EstimatedIncreaseInCost*|The estimated increase in spend corresponding to the suggested bid.|*double*|
|*EstimatedIncreaseInImpressions*|The estimated impressions opportunities corresponding to the suggested bid.|*long*|
|*KeywordId*|The identifier of the keyword to which the bid opportunity applies.|*long*|
|*MatchType*|The match type to which the suggested bid value applies. The possible values are BroadMatch, ExactMatch, and PhraseMatch.|*string*|
|*SuggestedBid*|The suggested bid based on the last 7 days of performance history for the corresponding ad group.|*double*|

## <a name="InheritedElements"></a>Inherited Elements
The *BidOpportunity* object inherits the following element from the [Opportunity](../adinsight-api/opportunity-data-object.md) object. 

> [!NOTE]
> The description below is specific to bid opportunities, and might not apply to other objects that inherit the same element from the [Opportunity](../adinsight-api/opportunity-data-object.md) object.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*OpportunityKey*|An identifier that uniquely identifies the opportunity.|*string*|

## Requirements
[!INCLUDE[reqadint](../adinsight-api/includes/reqadint.md)]
## See Also
[GetBidOpportunities](../adinsight-api/getbidopportunities-service-operation.md)


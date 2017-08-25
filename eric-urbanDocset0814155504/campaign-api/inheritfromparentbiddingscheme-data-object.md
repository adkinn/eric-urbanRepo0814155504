---
title: "InheritFromParentBiddingScheme Data Object"
ms.custom: ""
ms.date: "08/15/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a49de6c4-53bc-4447-8b7c-d5edc7e19086
caps.latest.revision: 13
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# InheritFromParentBiddingScheme Data Object
Defines an object that represents the inherit from parent bid strategy type.

This is the default bid strategy type for your ad groups and keywords. Use this bid strategy type to inherit the bid strategy type of the respective parent campaign or ad group.

## Syntax

```xml
<xs:complexType name="InheritFromParentBiddingScheme">
  <xs:complexContent mixed="false">
    <xs:extension base="tns:BiddingScheme">
      <xs:sequence>
        <xs:element minOccurs="0" name="InheritedBidStrategyType" nillable="true" type="xs:string"/>
      </xs:sequence>
    </xs:extension>
  </xs:complexContent>
</xs:complexType>
```

## <a name="Elements"></a>Elements
The *InheritFromParentBiddingScheme* object inherits elements from the [BiddingScheme](../campaign-api/biddingscheme-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#inheritedelements) below.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*InheritedBidStrategyType*|The type of bidding scheme (a.k.a. bid strategy type) that is inherited from the parent campaign or ad group. This value is equal to the *Type* element of the campaign or ad group's [BiddingScheme](../campaign-api/biddingscheme-data-object.md) object. Possible values are *EnhancedCpc*, *ManualCpc*, *MaxClicks*, *MaxConversions*, and *TargetCpa*.<br/><br/>**Note:** [!INCLUDE[pilot_comingsoon](../campaign-api/includes/pilot-comingsoon.md)]<br /><br />**Note:** This element is not returned by default. You must include *InheritedBidStrategyType* in the *ReturnAdditionalFields* optional request element when calling [GetAdGroupsByCampaignId](../campaign-api/getadgroupsbycampaignid-service-operation.md), [GetAdGroupsByIds](../campaign-api/getadgroupsbyids-service-operation.md), [GetKeywordsByAdGroupId](../campaign-api/getkeywordsbyadgroupid-service-operation.md), [GetKeywordsByEditorialStatus](../campaign-api/getkeywordsbyeditorialstatus-service-operation.md), and [GetKeywordsByIds](../campaign-api/getkeywordsbyids-service-operation.md).|*string*|

## <a name="InheritedElements"></a>Inherited Elements
The *InheritFromParentBiddingScheme* object inherits the following element from the [BiddingScheme](../campaign-api/biddingscheme-data-object.md) object. 

> [!NOTE]
> The description below is specific to the "inherit from parent" bidding scheme, and might not apply to other objects that inherit the same element from the [BiddingScheme](../campaign-api/biddingscheme-data-object.md) object.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Type*|The type of the bidding scheme. This value is *InheritFromParentBiddingScheme* when you retrieve an "inherit from parent" bidding scheme. For more information about bidding scheme types, see the [BiddingScheme Data Object Remarks](../campaign-api/biddingscheme-data-object.md#remarks).<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|*string*|


## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[AdGroup](../campaign-api/adgroup-data-object.md)  
[Campaign](../campaign-api/campaign-data-object.md)  
[Keyword](../campaign-api/keyword-data-object.md)  

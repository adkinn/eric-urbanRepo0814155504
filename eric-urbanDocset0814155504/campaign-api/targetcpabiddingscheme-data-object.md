---
title: "TargetCpaBiddingScheme Data Object"
ms.custom: ""
ms.date: "08/15/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 68ae730b-bd08-4b8e-a102-473d9673b5d4
caps.latest.revision: 14
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# TargetCpaBiddingScheme Data Object
Defines an object that represents the target CPA bid strategy type.

Use this bid strategy to maximize conversions at the target cost per acquisition (CPA).

[!INCLUDE[autobid_alert_para](../campaign-api/includes/autobid-alert-para.md)]

> [!NOTE]
> [!INCLUDE[pilot_comingsoon](../campaign-api/includes/pilot-comingsoon.md)]
> 
> The *TargetCpa* bid strategy is available only to advertisers from the following countries: Australia, Canada, France, Germany, United Kingdom, and United States.

## Syntax

```xml
<xs:complexType name="TargetCpaBiddingScheme">
  <xs:complexContent mixed="false">
    <xs:extension base="tns:BiddingScheme">
      <xs:sequence>
        <xs:element xmlns:q4="https://bingads.microsoft.com/CampaignManagement/v11" minOccurs="0" name="MaxCpc" nillable="true" type="q4:Bid"/>
        <xs:element name="TargetCpa" nillable="true" type="xs:double"/>
      </xs:sequence>
    </xs:extension>
  </xs:complexContent>
</xs:complexType>
```

## <a name="Elements"></a>Elements
The *TargetCpaBiddingScheme* object inherits elements from the [BiddingScheme](../campaign-api/biddingscheme-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#inheritedelements) below.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*MaxCpc*|The maximum cost per click that you want to spend.<br/><br/>**Add:** Optional<br/>**Update:** Optional|[Bid](../campaign-api/bid-data-object.md)|
|*TargetCpa*|The target cost per acquisition (CPA) that you want used by Bing Ads to maximize conversions.<br/><br/>**Add:** Required<br/>**Update:** Optional|*double*|

## <a name="InheritedElements"></a>Inherited Elements
The *TargetCpaBiddingScheme* object inherits the following element from the [BiddingScheme](../campaign-api/biddingscheme-data-object.md) object. 

> [!NOTE]
> The description below is specific to the target CPA bidding scheme, and might not apply to other objects that inherit the same element from the [BiddingScheme](../campaign-api/biddingscheme-data-object.md) object.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Type*|The type of the bidding scheme. This value is *TargetCpaBiddingScheme* when you retrieve a target CPA bidding scheme. For more information about bidding scheme types, see the [BiddingScheme Data Object Remarks](../campaign-api/biddingscheme-data-object.md#remarks).<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|*string*|


## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[AdGroup](../campaign-api/adgroup-data-object.md)  
[Campaign](../campaign-api/campaign-data-object.md)  
[Keyword](../campaign-api/keyword-data-object.md)  

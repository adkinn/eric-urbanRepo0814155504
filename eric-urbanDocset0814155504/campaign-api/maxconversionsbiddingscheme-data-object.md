---
title: "MaxConversionsBiddingScheme Data Object"
ms.custom: ""
ms.date: "08/15/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0716787f-04a4-4dda-921d-7c65af81ebc6
caps.latest.revision: 12
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# MaxConversionsBiddingScheme Data Object
Defines an object that represents the maximum conversions bid strategy type.

Use this bid strategy to maximize the number of conversions given your maximum allowed budget.

[!INCLUDE[autobid_alert_para](../campaign-api/includes/autobid-alert-para.md)]

> [!NOTE]
> [!INCLUDE[pilot_comingsoon](../campaign-api/includes/pilot-comingsoon.md)]
> 
> The *MaxConversions* bid strategy is available only to advertisers from the following countries: Australia, Canada, France, Germany, United Kingdom, and United States.

## Syntax

```xml
<xs:complexType name="MaxConversionsBiddingScheme">
  <xs:complexContent mixed="false">
    <xs:extension base="tns:BiddingScheme">
      <xs:sequence>
        <xs:element xmlns:q2="https://bingads.microsoft.com/CampaignManagement/v11" minOccurs="0" name="MaxCpc" nillable="true" type="q2:Bid"/>
      </xs:sequence>
    </xs:extension>
  </xs:complexContent>
</xs:complexType>
```

## <a name="Elements"></a>Elements
The *MaxConversionsBiddingScheme* object inherits elements from the [BiddingScheme](../campaign-api/biddingscheme-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#InheritedElements) below.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*MaxCpc*|The maximum cost per click that you want to spend.<br/><br/>**Add:** Optional<br/>**Update:** Optional|[Bid](../campaign-api/bid-data-object.md)

## <a name="InheritedElements"></a>Inherited Elements
The *MaxConversionsBiddingScheme* object inherits the following element from the [BiddingScheme](../campaign-api/biddingscheme-data-object.md) object. 

> [!NOTE]
> The description below is specific to the max conversions bidding scheme, and might not apply to other objects that inherit the same element from the [BiddingScheme](../campaign-api/biddingscheme-data-object.md) object.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Type*|The type of the bidding scheme. This value is *MaxConversionsBiddingScheme* when you retrieve a maximum conversions bidding scheme. For more information about bidding scheme types, see the [BiddingScheme Data Object Remarks](../campaign-api/biddingscheme-data-object.md#remarks).<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|*string*|


## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[AdGroup](../campaign-api/adgroup-data-object.md)  
[Campaign](../campaign-api/campaign-data-object.md)  
[Keyword](../campaign-api/keyword-data-object.md)  

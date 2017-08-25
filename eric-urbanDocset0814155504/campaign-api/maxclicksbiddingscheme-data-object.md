---
title: "MaxClicksBiddingScheme Data Object"
ms.custom: ""
ms.date: "08/15/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f987d41a-77e2-4d69-aeda-d969d2bc7c64
caps.latest.revision: 14
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# MaxClicksBiddingScheme Data Object
Defines an object that represents the maximum clicks bid strategy type.

Use this bid strategy to maximize the number of clicks given your maximum allowed budget.

[!INCLUDE[autobid_alert_para](../campaign-api/includes/autobid-alert-para.md)]

> [!NOTE]
> [!INCLUDE[pilot_comingsoon](../campaign-api/includes/pilot-comingsoon.md)]
> 
> The *MaxClicks* bid strategy is available only to advertisers from the following countries: Australia, Canada, France, Germany, India, Italy, Netherlands, Spain, Sweden, Switzerland, United Kingdom, and United States.

## Syntax

```xml
<xs:complexType name="MaxClicksBiddingScheme">
  <xs:complexContent mixed="false">
    <xs:extension base="tns:BiddingScheme">
      <xs:sequence>
        <xs:element xmlns:q1="https://bingads.microsoft.com/CampaignManagement/v11" minOccurs="0" name="MaxCpc" nillable="true" type="q1:Bid"/>
      </xs:sequence>
    </xs:extension>
  </xs:complexContent>
</xs:complexType>
```

## <a name="Elements"></a>Elements
The *MaxClicksBiddingScheme* object inherits elements from the [BiddingScheme](../campaign-api/biddingscheme-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#inheritedelements) below.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*MaxCpc*|The maximum cost per click that you want to spend.<br/><br/>**Add:** Optional<br/>**Update:** Optional|[Bid](../campaign-api/bid-data-object.md)|

## <a name="InheritedElements"></a>Inherited Elements
The *MaxClicksBiddingScheme* object inherits the following element from the [BiddingScheme](../campaign-api/biddingscheme-data-object.md) object. 

> [!NOTE]
> The description below is specific to the max clicks bidding scheme, and might not apply to other objects that inherit the same element from the [BiddingScheme](../campaign-api/biddingscheme-data-object.md) object.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Type*|The type of the bidding scheme. This value is *MaxClicksBiddingScheme* when you retrieve a maximum clicks bidding scheme. For more information about bidding scheme types, see the [BiddingScheme Data Object Remarks](../campaign-api/biddingscheme-data-object.md#remarks).<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|*string*|


## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[AdGroup](../campaign-api/adgroup-data-object.md)  
[Campaign](../campaign-api/campaign-data-object.md)  
[Keyword](../campaign-api/keyword-data-object.md)  

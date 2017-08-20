---
title: "EnhancedCpcBiddingScheme Data Object"
ms.custom: ""
ms.date: "08/15/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b9481096-e7a2-46e5-89bf-d93a2de8116d
caps.latest.revision: 14
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# EnhancedCpcBiddingScheme Data Object
Defines an object that represents the enhanced CPC bid strategy type.

Use the enhanced CPC bid strategy type to set your ad group and keyword bids, and Bing Ads will automatically adjust your bids in real time so that you bid up to 30% higher on users that are more likely to convert and up to 100% less on users less likely to convert. Bing Ads will still respect your campaign budget limit.

[!INCLUDE[autobid_alert_para](../campaign-api/includes/autobid-alert-para.md)]

## Syntax

```xml
<xs:complexType name="EnhancedCpcBiddingScheme">
  <xs:complexContent mixed="false">
    <xs:extension base="tns:BiddingScheme">
      <xs:sequence/>
    </xs:extension>
  </xs:complexContent>
</xs:complexType>
```

## <a name="Elements"></a>Elements
The *EnhancedCpcBiddingScheme* object inherits elements from the [BiddingScheme](../campaign-api/biddingscheme-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#InheritedElements) below.

## <a name="InheritedElements"></a>Inherited Elements
The *EnhancedCpcBiddingScheme* object inherits the following element from the [BiddingScheme](../campaign-api/biddingscheme-data-object.md) object. 

> [!NOTE]
> The description below is specific to the enhanced CPC bidding scheme, and might not apply to other objects that inherit the same element from the [BiddingScheme](../campaign-api/biddingscheme-data-object.md) object.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Type*|The type of the bidding scheme. This value is *EnhancedCpcBiddingScheme* when you retrieve an enhanced CPC bidding scheme. For more information about bidding scheme types, see the [BiddingScheme Data Object Remarks](../campaign-api/biddingscheme-data-object.md#remarks).<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|*string*|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[AdGroup](../campaign-api/adgroup-data-object.md)  
[Campaign](../campaign-api/campaign-data-object.md)  
[Keyword](../campaign-api/keyword-data-object.md)  

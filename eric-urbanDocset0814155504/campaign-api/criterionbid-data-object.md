---
title: "CriterionBid Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eda55633-ae9a-4b08-8ed6-cc5376d4448a
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# CriterionBid Data Object
Defines a base class for criterion bids.

Do not try to instantiate a *CriterionBid*. You can create the following object that derives from it.
-   [BidMultiplier](../campaign-api/bidmultiplier-data-object.md)  
-   [FixedBid](../campaign-api/fixedbid-data-object.md)  

For a list of criterion bids that you can use with [BiddableCampaignCriterion](../campaign-api/biddablecampaigncriterion-data-object.md), see the [CampaignCriterionType](../campaign-api/campaigncriteriontype-value-set.md) value set.

For a list of criterion bids that you can use with [BiddableAdGroupCriterion](../campaign-api/biddableadgroupcriterion-data-object.md), see the [AdGroupCriterionType](../campaign-api/adgroupcriteriontype-value-set.md) value set.

## Syntax

```xml
\<xs:complexType name="CriterionBid">
  \<xs:sequence>
    \<xs:element minOccurs="0" name="Type" nillable="true" type="xs:string" />
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Type*|The type of criterion bid. For more information, see [Remarks](#remarks).|*string*|

## <a name="remarks"></a>Remarks
For Java and the .NET languages, do not set the *Type* element because the value is determined by whether you instantiate a bid multiplier or fixed bid.

If you generate the SOAP manually, use the *type* attribute of the `<CriterionBid>` node (as shown in the following example) to specify the type of criterion.

```
\<CriterionBid i:type="BidMultiplier" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
     . . .
</CriterionBid>
```

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[BiddableAdGroupCriterion](../campaign-api/biddableadgroupcriterion-data-object.md)  
[AdGroupCriterionType](../campaign-api/adgroupcriteriontype-value-set.md)  
[BiddableCampaignCriterion](../campaign-api/biddablecampaigncriterion-data-object.md)  
[CampaignCriterionType](../campaign-api/campaigncriteriontype-value-set.md)  


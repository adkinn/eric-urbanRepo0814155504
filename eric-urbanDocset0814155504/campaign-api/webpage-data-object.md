---
title: "Webpage Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 823b6daf-03fe-4a45-9cc0-53b0113ee886
caps.latest.revision: 11
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Webpage Data Object
Defines a webpage parameter that contains a list of webpage conditions or criteria that help determine whether you want to show dynamic search ads.

The *Webpage* criterion can be included within [BiddableAdGroupCriterion](../campaign-api/biddableadgroupcriterion-data-object.md), [NegativeAdGroupCriterion](../campaign-api/negativeadgroupcriterion-data-object.md), and [NegativeCampaignCriterion](../campaign-api/negativecampaigncriterion-data-object.md) objects. If ad group level negative webpage criterions are specified, the campaign level negative webpage criterions are ignored for that ad group. In other words the ad group negative webpage criterions override the campaign negative webpage criterions, and are not applied as a union.   

> [!NOTE]
> [!INCLUDE[pilot_comingsoon](../campaign-api/includes/pilot-comingsoon.md)]

## Syntax

```xml
<xs:complexType name="Webpage">
  <xs:complexContent mixed="false">
    <xs:extension base="tns:Criterion">
      <xs:sequence>
        <xs:element minOccurs="0" name="Parameter" nillable="true" type="tns:WebpageParameter"/>
      </xs:sequence>
    </xs:extension>
  </xs:complexContent>
</xs:complexType>
```

## <a name="Elements"></a>Elements
The *Webpage* object derives from the [Criterion](../campaign-api/criterion-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#InheritedElements) below.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Parameter*|The webpage parameter that contains a list of webpage conditions or criteria.<br/><br/>**Add:** Required<br/>**Update:** Optional. You can update the criterion name, but cannot update the webpage conditions. To update the conditions you must delete the criterion and add a new criterion.|[WebpageParameter](../campaign-api/webpageparameter-data-object.md)|

## <a name="InheritedElements"></a>Inherited Elements
The *Webpage* object derives from the [Criterion](../campaign-api/criterion-data-object.md) object, and inherits the following element. 

> [!NOTE]
> The descriptions below are specific to webpage criterions, and might not apply to other objects that inherit the same elements from the [Criterion](../campaign-api/criterion-data-object.md) object.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Type*|The type of the criterion. This value is *Webpage* when you retrieve a webpage criterion. For more information about criterion types, see the [Criterion Data Object Remarks](../campaign-api/criterion-data-object.md#remarks).<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|*string*|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[DynamicSearchAd](../campaign-api/dynamicsearchad-data-object.md)  
[Criterion](../campaign-api/criterion-data-object.md)  


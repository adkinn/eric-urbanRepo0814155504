---
title: "ProductAd Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 11a31a5d-bdc1-4cf0-83d9-d51237a42c1e
caps.latest.revision: 10
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# ProductAd Data Object
Defines a product ad. A product ad is not used directly for delivered ad copy.  Instead, the delivery engine generates product ads from the product details that it finds in the customer’s [!INCLUDE[storebrand](../campaign-api/includes/storebrand.md)] store.

## Syntax

```xml
<xs:complexType name="ProductAd">
  <xs:complexContent mixed="false">
    <xs:extension base="tns:Ad">
      <xs:sequence>
        <xs:element minOccurs="0" name="PromotionalText" nillable="true" type="xs:string" />
      </xs:sequence>
    </xs:extension>
  </xs:complexContent>
</xs:complexType>
```

## <a name="Elements"></a>Elements
The *ProductAd* object inherits elements from the [Ad](../campaign-api/ad-data-object.md). object. For a list of the inherited elements, see [Inherited Elements](#InheritedElements) below.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*PromotionalText*|The promotional text to display in a product ad. If you do not want to add promotional text to the product ads, set *PromotionalText* to null or an empty string.<br /><br />The text can contain a maximum of 45 characters. The promotional text of product ads within an ad group must be unique.<br /><br />**Add:** Optional<br/>**Update:** Optional|*string*|
  
## <a name="InheritedElements"></a>Inherited Elements
The *ProductAd* object inherits the following elements from the [Ad](../campaign-api/ad-data-object.md) object. 

> [!NOTE]
> The descriptions below are specific to product ads, and might not apply to other objects that inherit the same elements from the [Ad](../campaign-api/ad-data-object.md) object.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AdFormatPreference*|This element is not applicable for product ads.|*string*|
|*DevicePreference*|Not supported for product ads.|*long*|
|*EditorialStatus*|The editorial review status of the ad, which indicates whether the ad is pending review, has been approved, or has been disapproved.<br /><br />**Add:** Read-only<br/>**Update:** Read-only|[AdEditorialStatus](../campaign-api/adeditorialstatus-value-set.md)|
|*FinalAppUrls*|Not supported for product ads.|[AppUrl](../campaign-api/appurl-data-object.md) array|
|*FinalMobileUrls*|Not supported for product ads.|*string* array|
|*FinalUrls*|Not supported for product ads.|*string* array|
|*ForwardCompatibilityMap*|The list of key and value strings for forward compatibility. This element can be used to avoid otherwise breaking changes when new elements are added in future releases.<br /><br />There are currently not any ForwardCompatibilityMap key and value pairs that are applicable for product ads.|*KeyValuePairOfstringstring* array|
|*Id*|The unique Bing Ads identifier for the ad.<br /><br />**Add:** Read-only<br/>**Update:** Required and Read-only|*long*|
|*Status*|The status of the ad.<br /><br />**Add:** Optional<br/>**Update:** Optional|[AdStatus](../campaign-api/adstatus-value-set.md)|
|*TrackingUrlTemplate*|Not supported for product ads.|*string*|
|*Type*|The type of the ad. This value is *Product* when you retrieve a product ad. For more information about ad types, see the [Ad Data Object Remarks](../campaign-api/ad-data-object.md#remarks).<br /><br />**Add:** Read-only<br/>**Update:** Read-only|[AdType](../campaign-api/adtype-value-set.md)|
|*UrlCustomParameters*|Not supported for product ads.|[CustomParameters](../campaign-api/customparameters-data-object.md)|


## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[AddAds](../campaign-api/addads-service-operation.md)  
[DeleteAds](../campaign-api/deleteads-service-operation.md)  
[GetAdsByAdGroupId](../campaign-api/getadsbyadgroupid-service-operation.md)  
[GetAdsByEditorialStatus](../campaign-api/getadsbyeditorialstatus-service-operation.md)  
[GetAdsByIds](../campaign-api/getadsbyids-service-operation.md)  
[UpdateAds](../campaign-api/updateads-service-operation.md)  


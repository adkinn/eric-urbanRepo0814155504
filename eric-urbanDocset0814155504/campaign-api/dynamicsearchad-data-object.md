---
title: "DynamicSearchAd Data Object"
ms.custom: ""
ms.date: "08/15/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f51dcd7d-1443-4688-9cc0-faab4d63d6e0
caps.latest.revision: 12
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# DynamicSearchAd Data Object
Defines a dynamic search ad. With a dynamic search ads campaign, the ad title and display URL are generated automatically based on the website domain and language that you want to target.

> [!NOTE]
> [!INCLUDE[pilot_comingsoon](../campaign-api/includes/pilot-comingsoon.md)]

To get started with dynamic search ads, first you'll need to [add](../campaign-api/addcampaigns-service-operation.md) a new [Campaign](../campaign-api/campaign-data-object.md) with its type set to *DynamicSearchAds*. When you create the campaign, you'll need to include a [DynamicSearchAdsSetting](../campaign-api/dynamicsearchadssetting-data-object.md) that specifies the target website domain and language.

Next, [create](../campaign-api/addadgroups-service-operation.md) a new [AdGroup](../campaign-api/adgroup-data-object.md) within the dynamic search ads campaign. You can add one or more [Webpage](../campaign-api/webpage-data-object.md) criterion to each ad group that helps determine whether or not to serve dynamic search ads, by calling the [AddAdGroupCriterions](../campaign-api/addadgroupcriterions-service-operation.md) operation. 

If you want to exclude certain portions of your website, you can add negative [Webpage](../campaign-api/webpage-data-object.md) criterion at the campaign and ad group level using the respective [AddCampaignCriterions](../campaign-api/addcampaigncriterions-service-operation.md) and [AddAdGroupCriterions](../campaign-api/addadgroupcriterions-service-operation.md) service operations. The negative [Webpage](../campaign-api/webpage-data-object.md) criterion at the campaign level applies to all ad groups within the campaign; however, if you define ad group level negative [Webpage](../campaign-api/webpage-data-object.md) criterion, the campaign criterion is ignored for that ad group. 

Whether the criterion is positive or negative, you can choose whether you want the criterion argument to match partial URLs, page content, page title, or categories that Bing thinks applies to your website. To discover the categories that you can use for [Webpage](../campaign-api/webpage-data-object.md) criterion (positive or negative), use the [GetDomainCategories](~/adinsight-api/getdomaincategories-service-operation.md) operation with the Ad Insight service.

Finally you can [add](../campaign-api/addads-service-operation.md) a [DynamicSearchAd](../campaign-api/dynamicsearchad-data-object.md) to the ad group. The ad title and display URL are generated automatically based on the website domain and language that you want to target.

## Syntax

```xml
<xs:complexType name="DynamicSearchAd">
  <xs:complexContent mixed="false">
    <xs:extension base="tns:Ad">
      <xs:sequence>
        <xs:element minOccurs="0" name="Path1" nillable="true" type="xs:string"/>
        <xs:element minOccurs="0" name="Path2" nillable="true" type="xs:string"/>
        <xs:element name="Text" nillable="true" type="xs:string"/>
      </xs:sequence>
    </xs:extension>
  </xs:complexContent>
</xs:complexType>
```

## <a name="Elements"></a>Elements
The *DynamicSearchAd* object inherits elements from the [Ad](../campaign-api/ad-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#InheritedElements) below.

> [!NOTE]
> The combination of the *Path1*, *Path2*, and *Text* elements make the dynamic search ad unique.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Path1*|The first part of the optional path that will be appended to the domain portion of your display URL. The display URL e.g. *www.contoso.com* will be generated from the domain of your display URL. Then if you have specified a value for *Path 1* it will be appended to the display URL. If you have also specified a value for *Path 2*, then it will also be appended to the display URL after *Path 1*. For example if your domain is *contoso.com*, *Path 1* is set to *subdirectory1*, and *Path 2* is set to *subdirectory2*, then the URL displayed will be *www.contoso.com/subdirectory1/subdirectory2*. <br /><br />The maximum input length of the path is 15 characters. Note that for languages with double-width characters e.g. Traditional Chinese the maximum input length of the path is 7 characters. Although dynamic text substitution is supported for other ad types like Expanded Text ads, it is not supported for dynamic search ads.<br /><br />The path cannot contain the forward slash (/) or newline (\n) characters.<br /><br />If the path includes a space, it will be replaced with an underscore (_) when the ad is shown.<br/><br/>**Add:** Optional<br/>**Update:** Optional|*string*|
|*Path2*|The second part of the optional path that will be appended to the domain portion of your display URL. The display URL e.g. *www.contoso.com* will be generated from the domain of your dynamic search ads campaign level settings. Then if you have specified a value for *Path 1* it will be appended to the display URL. If you have also specified a value for *Path 2*, then it will also be appended to the display URL after *Path 1*. For example if your domain is *contoso.com*, *Path 1* is set to *subdirectory1*, and *Path 2* is set to *subdirectory2*, then the URL displayed will be *www.contoso.com/subdirectory1/subdirectory2*.<br /><br />You can only specify *Path2* if *Path1* is also set. <br /><br />The maximum input length of the path is 15 characters. Note that for languages with double-width characters e.g. Traditional Chinese the maximum input length of the path is 7 characters. Although dynamic text substitution is supported for other ad types like Expanded Text ads, it is not supported for dynamic search ads.<br /><br />The path cannot contain the forward slash (/) or newline (\n) characters.<br /><br />If the path includes a space, it will be replaced with an underscore (_) when the ad is shown.<br/><br/>**Add:** Optional<br/>**Update:** Optional|*string*|
|*Text*|The ad copy.<br /><br />The text must contain at least one word.<br /><br />The maximum input length of the copy is 80 characters. Note that for ad groups that use Traditional Chinese the maximum input length of the copy is 40 characters. Although dynamic text substitution is supported for other ad types like Expanded Text ads, it is not supported for dynamic search ads.<br /><br />The text cannot contain the newline (\n) character.<br/><br/>**Add:** Required<br/>**Update:** Optional|*string*|
  
## <a name="InheritedElements"></a>Inherited Elements
The *DynamicSearchAd* object inherits the following elements from the [Ad](../campaign-api/ad-data-object.md) object. 

> [!NOTE]
> The descriptions below are specific to dynamic search ads, and might not apply to other objects that inherit the same elements from the [Ad](../campaign-api/ad-data-object.md) object.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AdFormatPreference*|This element is not applicable for dynamic search ads.|*string*|
|*DevicePreference*|This element is not applicable for dynamic search ads.|*long*|
|*EditorialStatus*|The editorial review status of the ad, which indicates whether the ad is pending review, has been approved, or has been disapproved.<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|[AdEditorialStatus](../campaign-api/adeditorialstatus-value-set.md)|
|*FinalAppUrls*|This element is not applicable for dynamic search ads.|[AppUrl](../campaign-api/appurl-data-object.md) array|
|*FinalMobileUrls*|This element is not applicable for dynamic search ads.|*string* array|
|*FinalUrls*|This element is not applicable for dynamic search ads.|*string* array|
|*ForwardCompatibilityMap*|The list of key and value strings for forward compatibility. This element can be used to avoid otherwise breaking changes when new elements are added in future releases.<br /><br />Currently there are no supported forward compatibility map key and value pairs for dynamic search ads.|*KeyValuePairOfstringstring* array|
|*Id*|The unique Bing Ads identifier of the ad.<br/><br/>**Add:** Read-only<br/>**Update:** Required and Read-Only|*long*|
|*Status*|The status of the ad.<br/><br/>**Add:** Optional<br/>**Update:** Optional|[AdStatus](../campaign-api/adstatus-value-set.md)|
|*TrackingUrlTemplate*|The tracking template to use as a default for all landing page URLs.<br /><br />[!INCLUDE[validationrules_trackingurltemplate_dsa](../campaign-api/includes/validationrules-trackingurltemplate-dsa.md)]<br/><br/>**Add:** Optional<br/>**Update:** Optional|*string*|
|*Type*|The type of the ad. This value is *DynamicSearch* when you retrieve an dynamic search ad. For more information about ad types, see the [Ad Data Object Remarks](../campaign-api/ad-data-object.md#remarks).<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|[AdType](../campaign-api/adtype-value-set.md)|
|*UrlCustomParameters*|Your custom collection of key and value parameters for URL tracking.<br /><br />You may include up to 3 individual [CustomParameter](../campaign-api/customparameter-data-object.md) objects within the [CustomParameters](../campaign-api/customparameters-data-object.md) object. Each [CustomParameter](../campaign-api/customparameter-data-object.md) contains a *Key* and *Value* element.<br /><br />On update, set the *UrlCustomParameters* element to null or empty to retain any existing custom parameters. To remove all custom parameters, set the *Parameters* element of the [CustomParameters](../campaign-api/customparameters-data-object.md) object to null or empty. To remove a subset of custom parameters, specify the custom parameters that you want to keep in the *Parameters* element of the [CustomParameters](../campaign-api/customparameters-data-object.md) object.<br/><br/>**Add:** Optional<br/>**Update:** Optional|[CustomParameters](../campaign-api/customparameters-data-object.md)|


## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[AddAds](../campaign-api/addads-service-operation.md)  
[DeleteAds](../campaign-api/deleteads-service-operation.md)  
[GetAdsByAdGroupId](../campaign-api/getadsbyadgroupid-service-operation.md)  
[GetAdsByEditorialStatus](../campaign-api/getadsbyeditorialstatus-service-operation.md)  
[GetAdsByIds](../campaign-api/getadsbyids-service-operation.md)  
[UpdateAds](../campaign-api/updateads-service-operation.md)  

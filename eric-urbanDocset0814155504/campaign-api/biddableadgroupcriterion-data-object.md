---
title: "BiddableAdGroupCriterion Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5f7752d5-234f-4668-bc4e-ae2026dd41e1
caps.latest.revision: 26
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# BiddableAdGroupCriterion Data Object
Defines a biddable criterion that you want applied to the specified ad group.

## Syntax

```xml
<xs:complexType name="BiddableAdGroupCriterion">
  <xs:complexContent mixed="false">
    <xs:extension base="tns:AdGroupCriterion">
      <xs:sequence>
        <xs:element minOccurs="0" name="CriterionBid" nillable="true" type="tns:CriterionBid" />
        <xs:element name="DestinationUrl" type="xs:string" nillable="true" minOccurs="0"/>
        <xs:element name="EditorialStatus" type="tns:AdGroupCriterionEditorialStatus" nillable="true" minOccurs="0"/>
        <xs:element name="FinalAppUrls" type="q74:ArrayOfAppUrl" nillable="true" minOccurs="0" xmlns:q74="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V10"/>
        <xs:element name="FinalMobileUrls" type="q75:ArrayOfstring" nillable="true" minOccurs="0" xmlns:q75="http://schemas.microsoft.com/2003/10/Serialization/Arrays"/>
        <xs:element name="FinalUrls" type="q76:ArrayOfstring" nillable="true" minOccurs="0" xmlns:q76="http://schemas.microsoft.com/2003/10/Serialization/Arrays"/>
        <xs:element name="TrackingUrlTemplate" type="xs:string" nillable="true" minOccurs="0"/>
        <xs:element name="UrlCustomParameters" type="q77:CustomParameters" nillable="true" minOccurs="0" xmlns:q77="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V10"/>
      </xs:sequence>
    </xs:extension>
  </xs:complexContent>
</xs:complexType>
```

## <a name="Elements"></a>Elements
The *BiddableAdGroupCriterion* object derives from the [AdGroupCriterion](../campaign-api/adgroupcriterion-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#InheritedElements) below.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*CriterionBid*|The bid to use in the auction.<br/><br/>**Add:** Requirements vary depending on the type of *Criterion* that is [inherited](#InheritedElements) from the [AdGroupCriterion](../campaign-api/adgroupcriterion-data-object.md) object. The bid is optional and will be set to the default of *0* if not included for [AgeCriterion](../campaign-api/agecriterion-data-object.md), [DayTimeCriterion](../campaign-api/daytimecriterion-data-object.md), [DeviceCriterion](../campaign-api/devicecriterion-data-object.md), [GenderCriterion](../campaign-api/gendercriterion-data-object.md), [LocationCriterion](../campaign-api/locationcriterion-data-object.md), [RadiusCriterion](../campaign-api/radiuscriterion-data-object.md), [AudienceCriterion](../campaign-api/audiencecriterion-data-object.md), and [Webpage](../campaign-api/webpage-data-object.md) criterions. The bid is not applicable for [LocationIntentCriterion](../campaign-api/locationintentcriterion-data-object.md) (The service will not return any error and the bid will be ignored even if you include it). When you add a [ProductPartition](../campaign-api/productpartition-data-object.md) with the [ApplyProductPartitionActions](../campaign-api/applyproductpartitionactions-service-operation.md) operation the bid is required unless the product partition type is *Subdivision*, in which case the bid is not allowed.<br/>**Update:** Requirements vary depending on the type of *Criterion* that is [inherited](#InheritedElements) from the [AdGroupCriterion](../campaign-api/adgroupcriterion-data-object.md) object. The bid is required for [AgeCriterion](../campaign-api/agecriterion-data-object.md), [DayTimeCriterion](../campaign-api/daytimecriterion-data-object.md), [DeviceCriterion](../campaign-api/devicecriterion-data-object.md), [GenderCriterion](../campaign-api/gendercriterion-data-object.md), [LocationCriterion](../campaign-api/locationcriterion-data-object.md), and [RadiusCriterion](../campaign-api/radiuscriterion-data-object.md). The bid is not applicable for [LocationIntentCriterion](../campaign-api/locationintentcriterion-data-object.md) (The service will not return any error and the bid will be ignored even if you include it). For [AudienceCriterion](../campaign-api/audiencecriterion-data-object.md) and [Webpage](../campaign-api/webpage-data-object.md) criterions the bid is optional, and if no value is specified on update, this Bing Ads setting is not changed. When you update a [ProductPartition](../campaign-api/productpartition-data-object.md) with the [ApplyProductPartitionActions](../campaign-api/applyproductpartitionactions-service-operation.md) operation the bid is optional, and if no value is specified on update, this Bing Ads setting is not changed.|[CriterionBid](../campaign-api/criterionbid-data-object.md)|
|*DestinationUrl*|The URL of the webpage that the user is taken to when they click the ad.<br /><br />This element is only used if the *Criterion* property that is [inherited](#InheritedElements) from the [AdGroupCriterion](../campaign-api/adgroupcriterion-data-object.md) object is a [ProductPartition](../campaign-api/productpartition-data-object.md) criterion. For details see [ProductPartition Usage](#productpartition) below.|*string*|
|*EditorialStatus*|Reserved for future use.|[AdGroupCriterionEditorialStatus](../campaign-api/adgroupcriterioneditorialstatus-value-set.md)|
|*FinalAppUrls*|Reserved for future use.|[AppUrl](../campaign-api/appurl-data-object.md) array|
|*FinalMobileUrls*|Reserved for future use.|*string* array|
|*FinalUrls*|Reserved for future use.|*string* array|
|*TrackingUrlTemplate*|[!INCLUDE[trackingurltemplate](../campaign-api/includes/trackingurltemplate.md)]<br/><br/>This element is only used if the *Criterion* property that is [inherited](#InheritedElements) from the [AdGroupCriterion](../campaign-api/adgroupcriterion-data-object.md) object is either a [ProductPartition](../campaign-api/productpartition-data-object.md) or [Webpage](../campaign-api/webpage-data-object.md) criterion. For details see [ProductPartition Usage](#productpartition) and [Webpage Usage](#webpage) below.|*string*|
|*UrlCustomParameters*|Your custom collection of key and value parameters for URL tracking.<br/><br/>This element is only used if the *Criterion* property that is [inherited](#InheritedElements) from the [AdGroupCriterion](../campaign-api/adgroupcriterion-data-object.md) object is either a [ProductPartition](../campaign-api/productpartition-data-object.md) or [Webpage](../campaign-api/webpage-data-object.md) criterion. For details see [ProductPartition Usage](#productpartition) and [Webpage Usage](#webpage) below.|[CustomParameters](../campaign-api/customparameters-data-object.md)|

## <a name="InheritedElements"></a>Inherited Elements
The *BiddableAdGroupCriterion* object derives from the [AdGroupCriterion](../campaign-api/adgroupcriterion-data-object.md) object, and inherits the following elements. 

> [!NOTE]
> The descriptions below are specific to biddable ad group criterion, and might not apply to other objects that inherit the same elements from the [AdGroupCriterion](../campaign-api/adgroupcriterion-data-object.md) object.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AdGroupId*|The identifier of the ad group to apply the criterion to.<br/><br/>**Add:** Required<br/>**Update:** Required|*long*|
|*Criterion*|The criterion to apply to the ad group. The criterion helps determine whether ads in the ad group are served.<br/><br/>For a list of available criterion types, see [AdGroupCriterionType](../campaign-api/adgroupcriteriontype-value-set.md).<br/><br/>**Add:** Optional<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../campaign-api/includes/update-optional-setting-unchanged.md)]|[Criterion](../campaign-api/criterion-data-object.md)|
|*Id*|The unique Bing Ads identifier for the ad group criterion.<br/><br/>**Add:** Read-only<br/>**Update:** Required|*long*|
|*Status*|A status value that determines whether the criterion applies for the ad group.<br/><br/>For most biddable ad group criterions the only supported status value is *Active*. For exceptions, see [Webpage Usage](#webpage) below.<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|[AdGroupCriterionStatus](../campaign-api/adgroupcriterionstatus-value-set.md)|
|*Type*|The type of the ad group criterion. This value is *BiddableAdGroupCriterion* when you retrieve a biddable ad group criterion. For more information about ad group criterion types, see the [AdGroupCriterion Data Object Remarks](../campaign-api/adgroupcriterion-data-object.md#remarks).<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|*string*|

## <a name="productpartition"></a>ProductPartition Usage
If the *Criterion* property that is [inherited](#InheritedElements) from the [AdGroupCriterion](../campaign-api/adgroupcriterion-data-object.md) object is a [ProductPartition](../campaign-api/productpartition-data-object.md) criterion, please note the following usage of *BiddableAdGroupCriterion* properties.

### <a name="productpartition_destinationurl"></a>DestinationUrl
If you are currently using Destination URLs, you must eventually replace them with Tracking Templates. For more information, see [URL Tracking with Upgraded URLs](https://msdn.microsoft.com/library/bing-ads-tracking-template-urls-guide.aspx).

The URL can contain dynamic parameters such as {MatchType}. For a list of supported parameters, see the Bing Ads help article [What tracking or URL parameters can I use?](https://help.bingads.microsoft.com/#apex/3/en/56799/2).

The URL can contain a maximum of 1,024 characters. If the URL does not specify a protocol, the system uses the HTTP protocol when a user clicks the ad. If the URL specifies the HTTP protocol when you add an ad, the service will remove the http:// protocol string (the HTTP protocol string does not count against the 1,024 character limit); however, the service will not remove an HTTPS protocol string (https://) from the URL.

On update, to remove the destination URL, set it to an empty string (*""*). If you leave the element null it will not be updated.

The destination URL is used if specified; otherwise, the destination URL is determined by the corresponding value of the 'Link' that you specified  for the product offer in your [!INCLUDE[storebrand](../campaign-api/includes/storebrand.md)] catalog.

**Add:** Optional  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../campaign-api/includes/update-optional-setting-unchanged.md)]  

### <a name="productpartition_trackingurltemplate"></a>TrackingUrlTemplate
The tracking templates can be used in tandem with the URL specified in the 'Link' field for the product offer that you submitted via the [Content API](https://msdn.microsoft.com/library/bing-ads-content-api.aspx). By combining the feed URL with the tracking template, the landing page URL is assembled where a user is directed after clicking the ad. When you use the *TrackingUrlTemplate* element to update the URL parameters instead of updating them in the feed URL, the feed URL doesn't need to go through editorial review and your ads will continue to serve uninterrupted. For example if your product offer URL in the catalog feed is *http://contoso.com/*, you could specify the following tracking template: *{lpurl}?matchtype={matchtype}&device={device}*.

[!INCLUDE[validationrules_trackingurltemplate_bsc](../campaign-api/includes/validationrules-trackingurltemplate-bsc.md)]

**Add:** Optional  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../campaign-api/includes/update-optional-setting-unchanged.md)]  

### <a name="productpartition_urlcustomparameters"></a>UrlCustomParameters
You may include up to 3 individual [CustomParameter](../campaign-api/customparameter-data-object.md) objects within the [CustomParameters](../campaign-api/customparameters-data-object.md) object. Each [CustomParameter](../campaign-api/customparameter-data-object.md) contains a *Key* and *Value* element.

On update, set the *UrlCustomParameters* element to null or empty to retain any existing custom parameters. To remove all custom parameters, set the *Parameters* element of the [CustomParameters](../campaign-api/customparameters-data-object.md) object to null or empty. To remove a subset of custom parameters, specify the custom parameters that you want to keep in the *Parameters* element of the [CustomParameters](../campaign-api/customparameters-data-object.md) object.

**Add:** Optional  
**Update:** Optional  

## <a name="webpage"></a>Webpage Usage
If the *Criterion* property that is [inherited](#InheritedElements) from the [AdGroupCriterion](../campaign-api/adgroupcriterion-data-object.md) object is a [Webpage](../campaign-api/webpage-data-object.md) criterion, please note the following usage of *BiddableAdGroupCriterion* properties.

### <a name="webpage_status"></a>Status
**Add:** Optional. You can set the status to *Active* or *Paused*. You cannot set the status to *Deleted*.     
**Update:** [!INCLUDE[update_optional_setting_unchanged](../campaign-api/includes/update-optional-setting-unchanged.md)]  

### <a name="webpage_trackingurltemplate"></a>TrackingUrlTemplate
For [Webpage](../campaign-api/webpage-data-object.md) criterion the tracking templates can be used in tandem with the landing page URL that is generated dynamically from the domain that you specified for your Dynamic Search Ads campaign. By combining the domain with the tracking template, the landing page URL is assembled where a user is directed after clicking the ad. Here is an example tracking template: *{lpurl}?matchtype={matchtype}&device={device}*.

[!INCLUDE[validationrules_trackingurltemplate_bsc](../campaign-api/includes/validationrules-trackingurltemplate-dsa.md)]

**Add:** Optional  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../campaign-api/includes/update-optional-setting-unchanged.md)]  

### <a name="webpage_urlcustomparameters"></a>UrlCustomParameters
You may include up to 3 individual [CustomParameter](../campaign-api/customparameter-data-object.md) objects within the [CustomParameters](../campaign-api/customparameters-data-object.md) object. Each [CustomParameter](../campaign-api/customparameter-data-object.md) contains a *Key* and *Value* element.

On update, set the *UrlCustomParameters* element to null or empty to retain any existing custom parameters. To remove all custom parameters, set the *Parameters* element of the [CustomParameters](../campaign-api/customparameters-data-object.md) object to null or empty. To remove a subset of custom parameters, specify the custom parameters that you want to keep in the *Parameters* element of the [CustomParameters](../campaign-api/customparameters-data-object.md) object.

**Add:** Optional  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../campaign-api/includes/update-optional-setting-unchanged.md)]    

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[AddAdGroupCriterions](../campaign-api/addadgroupcriterions-service-operation.md)  
[ApplyProductPartitionActions](../campaign-api/applyproductpartitionactions-service-operation.md)  
[GetAdGroupCriterionsByIds](../campaign-api/getadgroupcriterionsbyids-service-operation.md)  
[UpdateAdGroupCriterions](../campaign-api/updateadgroupcriterions-service-operation.md)  


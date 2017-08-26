---
title: "AppInstallAd Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d208bb27-21c2-4251-af99-133000df0048
caps.latest.revision: 15
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AppInstallAd Data Object
Defines an app install ad. Create an app install ad if your intention is to drive app downloads, and not necessarily to direct leads to a web site. If you want to direct leads to a web site in addition to driving app downloads, then you should create a text ad with app ad extensions.

> [!NOTE]
> Before you can use app install ads, you must upgrade to Final Urls. For more information, see [URL Tracking with Upgraded URLs](~/concepts/url-tracking-with-upgraded-urls.md).
>
> Bing Ads only supports *EN-US* apps.

## Syntax

```xml
<xs:complexType name="AppInstallAd">
  <xs:complexContent mixed="false">
    <xs:extension base="tns:Ad">
      <xs:sequence>
        <xs:element minOccurs="0" name="AppPlatform" nillable="true" type="xs:string"/>
        <xs:element minOccurs="0" name="AppStoreId" nillable="true" type="xs:string"/>
        <xs:element name="Text" nillable="true" type="xs:string"/>
        <xs:element name="Title" nillable="true" type="xs:string"/>
      </xs:sequence>
    </xs:extension>
  </xs:complexContent>
</xs:complexType>
```

## <a name="Elements"></a>Elements
The *AppInstallAd* object inherits elements from the [Ad](../campaign-api/ad-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#inheritedelements) below.

> [!NOTE]
> The combination of the *AppPlatform*, *AppStoreId*, *Text*, and *Title* elements make the app install ad unique.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AppPlatform*|The application platform.<br /><br />Possible values include *iOS* and *Android*.<br /><br />**Add:** Required<br/>**Update:** Optional|*string*|
|*AppStoreId*|The application identifier provided by the app store.<br /><br />**Note:** If the application is new, please expect to wait 4-7 days before the ad will be eligible to deliver.<br /><br />**Add:** Required<br/>**Update:** Optional|*string*|
|*Text*|The ad copy. The copy must contain at least one word. The ad's copy and title combined must total at least three words.<br /><br />The ad copy cannot contain dynamic text strings such as {keyword}. <br /><br />The maximum input length of the copy is 71 characters. Note that for ad groups that use Traditional Chinese, the text is limited to 38 characters.<br /><br />The ad copy cannot contain the newline (\n) character.<br /><br />**Add:** Required<br/>**Update:** Optional|*string*|
|*Title*|The title of the ad. The title must contain at least one word. The ad's copy and title combined must total at least three words.<br /><br />The title cannot contain dynamic text strings such as {keyword}.<br /><br />The maximum input length of the title is 25 characters. Note that for ad groups that use Traditional Chinese, the title is limited to 15 characters.<br /><br />The title cannot contain the newline (\n) character.<br /><br />**Add:** Required<br/>**Update:** Optional|*string*|

## <a name="InheritedElements"></a>Inherited Elements
The *AppInstallAd* object inherits the following elements from the [Ad](../campaign-api/ad-data-object.md) object. 

> [!NOTE]
> The descriptions below are specific to app install ads, and might not apply to other objects that inherit the same elements from the [Ad](../campaign-api/ad-data-object.md) object.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AdFormatPreference*|This element is not applicable for app install ads.|*string*|
|*DevicePreference*|This element determines whether the preference is for app install ads to be displayed on mobile and tablet devices or only on mobile devices. (App install ads are not currently supported on desktop computers.)<br /><br />To specify a preference for mobile devices only (i.e. excluding tablets), set this element to *30001*.<br /><br />To specify a preference for both mobile and tablet devices, set this element to *0* (zero) or leave the element nil. By default, this element will be nil. <br /><br />**Add:** Optional<br/>**Update:** Optional|*long*|
|*EditorialStatus*|The editorial review status of the ad, which indicates whether the ad is pending review, has been approved, or has been disapproved.<br /><br />**Add:** Read-only<br/>**Update:** Read-only|[AdEditorialStatus](../campaign-api/adeditorialstatus-value-set.md)|
|*FinalAppUrls*|Not supported for app install ads.|[AppUrl](../campaign-api/appurl-data-object.md) array|
|*FinalMobileUrls*|Not supported for app install ads.|*string* array|
|*FinalUrls*|The URL where a search user lands and can choose to install an app.<br /><br />**Add:** Required<br/>**Update:** Optional|*string* array|
|*ForwardCompatibilityMap*|The list of key and value strings for forward compatibility. This element can be used to avoid otherwise breaking changes when new elements are added in future releases.<br /><br />There are currently not any ForwardCompatibilityMap key and value pairs that are applicable for this object.|*KeyValuePairOfstringstring* array|
|*Id*|The unique Bing Ads identifier for the ad.<br /><br />**Add:** Read-only<br/>**Update:** Required and Read-only|*long*|
|*Status*|The status of the ad.<br /><br />**Add:** Optional<br/>**Update:** Optional|[AdStatus](../campaign-api/adstatus-value-set.md)|
|*TrackingUrlTemplate*|The tracking template to use as a default for the URL specified with *FinalUrls*.<br /><br />[!INCLUDE[validationrules_trackingurltemplate](../campaign-api/includes/validationrules-trackingurltemplate.md)]<br /><br />**Add:** Optional<br/>**Update:** Optional|*string*|
|*Type*|The type of the ad. This value is *AppInstall* when you retrieve an app install ad. For more information about ad types, see the [Ad Data Object Remarks](../campaign-api/ad-data-object.md#remarks).<br /><br />**Add:** Read-only<br/>**Update:** Read-only|[AdType](../campaign-api/adtype-value-set.md)|
|*UrlCustomParameters*|Your custom collection of key and value parameters for URL tracking.<br /><br />You may include up to 3 individual [CustomParameter](../campaign-api/customparameter-data-object.md) objects within the [CustomParameters](../campaign-api/customparameters-data-object.md) object. Each [CustomParameter](../campaign-api/customparameter-data-object.md) contains a *Key* and *Value* element.<br /><br />On update, set the *UrlCustomParameters* element to null or empty to retain any existing custom parameters. To remove all custom parameters, set the *Parameters* element of the [CustomParameters](../campaign-api/customparameters-data-object.md) object to null or empty. To remove a subset of custom parameters, specify the custom parameters that you want to keep in the *Parameters* element of the [CustomParameters](../campaign-api/customparameters-data-object.md) object.<br /><br />**Add:** Optional<br/>**Update:** Optional|[CustomParameters](../campaign-api/customparameters-data-object.md)|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[AddAds](../campaign-api/addads-service-operation.md)  
[DeleteAds](../campaign-api/deleteads-service-operation.md)  
[GetAdsByAdGroupId](../campaign-api/getadsbyadgroupid-service-operation.md)  
[GetAdsByEditorialStatus](../campaign-api/getadsbyeditorialstatus-service-operation.md)  
[GetAdsByIds](../campaign-api/getadsbyids-service-operation.md)  
[UpdateAds](../campaign-api/updateads-service-operation.md)  

---
title: "TextAd Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f8db6e41-eceb-4af7-b3de-536c2f114ab6
caps.latest.revision: 19
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# TextAd Data Object
Defines a text ad.

[!INCLUDE[deprecate_sta](../campaign-api/includes/deprecate-sta.md)]

## Syntax

```xml
\<xs:complexType name="TextAd">
  \<xs:complexContent mixed="false">
    \<xs:extension base="tns:Ad">
      \<xs:sequence>
        \<xs:element minOccurs="0" name="DestinationUrl" nillable="true" type="xs:string" />
        \<xs:element name="DisplayUrl" nillable="true" type="xs:string" />
        \<xs:element name="Text" nillable="true" type="xs:string" />
        \<xs:element name="Title" nillable="true" type="xs:string" />
      \</xs:sequence>
    \</xs:extension>
  \</xs:complexContent>
\</xs:complexType>
```

## <a name="Elements"></a>Elements
The *TextAd* object inherits elements from the [Ad](../campaign-api/ad-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#InheritedElements) below.

> [!NOTE]
> The combination of the *DestinationUrl*, *DisplayUrl*, *Text*, and *Title* elements make the text ad unique.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*DestinationUrl*|The URL of the webpage to take the user to when they click the ad.<br /><br />The URL can contain dynamic parameters such as {MatchType}.<br/><br/>For a list of supported parameters, see the Bing Ads help article [What tracking or URL parameters can I use?](https://help.bingads.microsoft.com/#apex/3/en/56799/2).<br /><br />The URL can contain a maximum of 1,024 characters. If the URL does not specify a protocol, the system uses the HTTP protocol when a user clicks the ad. If the URL specifies the HTTP protocol when you add an ad, the service will remove the http:// protocol string (the HTTP protocol string does not count against the 1,024 character limit); however, the service will not remove an HTTPS protocol string (https://) from the URL.<br/><br/>[!INCLUDE[deprecate_destinationurl](../campaign-api/includes/deprecate-destinationurl.md)]<br /><br />**Note:** This URL is used only if the keyword does not specify a destination URL.<br /><br />**Add:** Required<br />**Update:** Optional|*string*|
|*DisplayUrl*|The URL to display in the ad.<br /><br />The subdirectory of the display URL can contain dynamic text strings such as {keyword}; however, the URL hostname cannot contain dynamic text. For more information, see the Bing Ads help article [Automatically customize your ads with dynamic text parameters](http://help.bingads.microsoft.com/#apex/3/en/50811/1).<br /><br />The maximum input length of the URL is 200 characters, and can contain dynamic text strings. However, the ad will fail to display if the URL exceeds 35 characters after dynamic text substitution occurs.<br /><br />**Add:** Required<br />**Update:** Optional|*string*|
|*Text*|The ad copy. The copy must contain at least one word. The ad’s copy and title combined must total at least three words.<br /><br />The text can contain dynamic text strings such as {keyword}. For more information, see the Bing Ads help article [Automatically customize your ads with dynamic text parameters](http://help.bingads.microsoft.com/#apex/3/en/50811/1).<br /><br />The maximum input length of the copy is 300 characters, and can contain dynamic text strings. However, the ad will fail to display if the copy exceeds 71 characters after dynamic text substitution occurs. Note that for ad groups that use Traditional Chinese, the text is limited to 38 characters after substitution.<br /><br />The text cannot contain the newline (\n) character.<br /><br />**Add:** Required<br />**Update:** Optional|*string*|
|*Title*|The title of the ad. The title must contain at least one word. The ad’s copy and title combined must total at least three words.<br /><br />The title can contain dynamic text strings such as {keyword}. For more information, see the Bing Ads help article [Automatically customize your ads with dynamic text parameters](http://help.bingads.microsoft.com/#apex/3/en/50811/1).<br /><br />The maximum input length of the title is 80 characters, and can contain dynamic text strings. However, the ad will fail to display if title exceeds 25 characters after dynamic text substitution occurs. Note that for ad groups that use Traditional Chinese, the title is limited to 15 characters after substitution.<br /><br />The title cannot contain the newline (\n) character.<br /><br />**Add:** Required<br />**Update:** Optional|*string*|
  
## <a name="InheritedElements"></a>Inherited Elements
The *TextAd* object inherits the following elements from the [Ad](../campaign-api/ad-data-object.md) object. 

> [!NOTE]
> The descriptions below are specific to text ads, and might not apply to other objects that inherit the same elements from the [Ad](../campaign-api/ad-data-object.md) object.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AdFormatPreference*|The Ad Format Preference is used to indicate whether or not you prefer the ad copy to be shown to users as a search or native ad. Search ads tend to be written as a call to action, whereas native ads should be written in more of an informational style.<br /><br />By defining at least one ad that should be used as native, the search ads will only be shown in search results.<br /><br />**IMPORTANT:** You must define at least one text ad per ad group that is not native preferred, otherwise the ad copy of all text ads will be eligible for both search and native ads.<br/><br/>Possible values are *Native* and *All*. If set to *All*, the ad will be eligible for both search and native ad formats. If set to *Native*, the ad will only be eligible for the native ad format.<br/><br/>**Add:** Optional. If you do not set this field when creating a text ad, by default the ad format preference will be set to *All*.<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../campaign-api/includes/update-optional-setting-unchanged.md)]|*string*|
|*DevicePreference*|This element determines whether the preference is for text ads to be displayed on mobile devices or all devices.<br /><br />To specify a preference for mobile devices, set this element to *30001*.<br /><br />To specify all devices, set this element to *0* (zero) or leave the element nil. By default, this element will be nil. You must define at least one text ad per ad group that is not mobile preferred, otherwise the ad will be eligible for all devices. <br /><br />**Add:** Optional<br />**Update:** Optional|*long*|
|*EditorialStatus*|The editorial review status of the ad, which indicates whether the ad is pending review, has been approved, or has been disapproved.<br /><br />**Add:** Read-only<br />**Update:** Read-only|[AdEditorialStatus](../campaign-api/adeditorialstatus-value-set.md)|
|*FinalAppUrls*|Not supported for text ads.|[AppUrl](../campaign-api/appurl-data-object.md) array|
|*FinalMobileUrls*|The mobile landing page URL.<br /><br />**Note:** This URL is used only if the keyword does not specify a final mobile URL.<br /><br />[!INCLUDE[validationrules_finalurls](../campaign-api/includes/validationrules-finalurls.md)]Also note that for [TextAd](../campaign-api/textad-data-object.md) objects you may not specify *FinalMobileUrls* if the *DevicePreference* is set to *30001* (mobile).|*string* array|
|*FinalUrls*|The landing page URL.<br /><br />**Note:** This URL is used only if the keyword does not specify a final URL.<br /><br />[!INCLUDE[validationrules_finalurls](../campaign-api/includes/validationrules-finalurls.md)]Also note that  if this ad's *TrackingUrlTemplate* or *UrlCustomParameters* element are set, then at least one final URL is required.<br /><br />**Add:** Required<br />**Update:** Optional|*string* array|
|*ForwardCompatibilityMap*|The list of key and value strings for forward compatibility. This element can be used to avoid otherwise breaking changes when new elements are added in future releases.<br /><br />Forward compatibility changes will be noted here in future releases. There are currently no forward compatibility changes for this object.|*KeyValuePairOfstringstring* array|
|*Id*|The unique Bing Ads identifier for the ad.<br /><br />**Add:** Read-only<br />**Update:** Required and Read-only|*long*|
|*Status*|The status of the ad.<br /><br />**Add:** Optional<br />**Update:** Optional|[AdStatus](../campaign-api/adstatus-value-set.md)|
|*TrackingUrlTemplate*|The tracking template to use as a default for all landing page URLs.<br /><br />[!INCLUDE[validationrules_trackingurltemplate](../campaign-api/includes/validationrules-trackingurltemplate.md)]<br /><br />**Add:** Optional<br />**Update:** Optional|*string*|
|*Type*|The type of the ad. This value is *Text* when you retrieve a text ad. For more information about ad types, see the [Ad Data Object Remarks](../campaign-api/ad-data-object.md#remarks).<br /><br />**Add:** Read-only<br />**Update:** Read-only|[AdType](../campaign-api/adtype-value-set.md)|
|*UrlCustomParameters*|Your custom collection of key and value parameters for URL tracking.<br /><br />You may include up to 3 individual [CustomParameter](../campaign-api/customparameter-data-object.md) objects within the [CustomParameters](../campaign-api/customparameters-data-object.md) object. Each [CustomParameter](../campaign-api/customparameter-data-object.md) contains a *Key* and *Value* element.<br /><br />On update, set the *UrlCustomParameters* element to null or empty to retain any existing custom parameters. To remove all custom parameters, set the *Parameters* element of the [CustomParameters](../campaign-api/customparameters-data-object.md) object to null or empty. To remove a subset of custom parameters, specify the custom parameters that you want to keep in the *Parameters* element of the [CustomParameters](../campaign-api/customparameters-data-object.md) object.<br /><br />**Add:** Optional<br />**Update:** Optional|[CustomParameters](../campaign-api/customparameters-data-object.md)|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[AddAds](../campaign-api/addads-service-operation.md)  
[DeleteAds](../campaign-api/deleteads-service-operation.md)  
[GetAdsByAdGroupId](../campaign-api/getadsbyadgroupid-service-operation.md)  
[GetAdsByEditorialStatus](../campaign-api/getadsbyeditorialstatus-service-operation.md)  
[GetAdsByIds](../campaign-api/getadsbyids-service-operation.md)  
[UpdateAds](../campaign-api/updateads-service-operation.md)  


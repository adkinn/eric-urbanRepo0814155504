---
title: "ExpandedTextAd Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1b2a4202-8fda-4324-99cf-93297d7644a1
caps.latest.revision: 19
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# ExpandedTextAd Data Object
Defines an expanded text ad.

This ad format works seamlessly on mobile, tablet and desktop devices so you can focus more on crafting your longer ad copy and optimizing your ad text to better engage your customers before they click your ad.

> [!NOTE]
> Before you can use expanded text ads, you must upgrade to Final Urls. For more information, see [URL Tracking with Upgraded URLs](~/concepts/url-tracking-with-upgraded-urls.md).

## Syntax

```xml
<xs:complexType name="ExpandedTextAd">
  <xs:complexContent mixed="false">
    <xs:extension base="tns:Ad">
      <xs:sequence>
        <xs:element name="DisplayUrl" type="xs:string" nillable="true" minOccurs="0"/>
        <xs:element name="Path1" nillable="true" type="xs:string" />
        <xs:element name="Path2" nillable="true" type="xs:string" />
        <xs:element name="Text" nillable="true" type="xs:string" />
        <xs:element name="TitlePart1" nillable="true" type="xs:string" />
        <xs:element name="TitlePart2" nillable="true" type="xs:string" />
      </xs:sequence>
    </xs:extension>
  </xs:complexContent>
</xs:complexType>
```

## <a name="Elements"></a>Elements
The *ExpandedTextAd* object inherits elements from the [Ad](../campaign-api/ad-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#inheritedelements) below.

> [!NOTE]
> The combination of the *FinalUrls*, *Path1*, *Path2*, *Text*, *TitlePart1* and *TitlePart2* elements make the expanded text ad unique.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*DisplayUrl*|The URL that will be displayed instead of the final URL. The final URL will still be used for the landing page URL.<br/><br/>Reserved for limited pilot usage e.g. pharmaceutical customers.<br/><br/>The domain portion of the URL in combination with the path 1 and path 2 strings cannot exceed 67 characters.|*string*|
|*Path1*|The first part of the optional path that will be appended to the domain portion of your display URL. The domain portion of your display URL e.g. *http://www.contoso.com* will be generated from the domain of your Final URL (*FinalUrls* element).  Then if you have specified a value for *Path1* it will be appended to the display URL. If you have also specified a value for *Path2*, then it will also be appended to the display URL after *Path1*. For example if your *FinalUrls* contains *http://www.contoso.com*, *Path1* is set to *subdirectory1*, and *Path2* is set to *subdirectory2*, then the URL displayed will be *http://www.contoso.com/subdirectory1/subdirectory2*.<br/><br/>The path can contain a countdown function. For more details see [Countdown Functions](~/concepts/expanded-text-ads#countdown.md).<br /><br />The path can contain dynamic parameters such as {MatchType}. For a list of supported parameters, see the Bing Ads help article [What tracking or URL parameters can I use?](https://help.bingads.microsoft.com/#apex/3/en/56799/2).<br /><br />The maximum input length of the path is 50 characters with dynamic text strings. However, the ad will fail to display if the path exceeds 15 characters after dynamic text substitution occurs. Note that for languages with double-width characters e.g. Traditional Chinese the maximum input length of the path is 25 characters, and the path is limited to 7 characters after substitution.<br/><br/>**IMPORTANT:** Starting the week of September 18th, the double-width character check will be done according to the characters used instead of the ad group language settings. Double-width characters include Korean, Japanese and Chinese languages characters as well as Emojis. Our support team will contact you if your current ads are affected by this change.<br /><br />The path cannot contain the forward slash (/) or newline (\n) characters.<br /><br />If the path includes a space, it will be replaced with an underscore (_) when the ad is shown.<br/><br/>**Add:** Optional<br/>**Update:** Optional|*string*|
|*Path2*|The second part of the optional path that will be appended to the domain portion of your display URL. The domain portion of your display URL e.g. *http://www.contoso.com* will be generated from the domain of your Final URL (*FinalUrls* element).  Then if you have specified a value for *Path1* it will be appended to the display URL. If you have also specified a value for *Path2*, then it will also be appended to the display URL after *Path1*. For example if your *FinalUrls* contains *http://www.contoso.com*, *Path1* is set to *subdirectory1*, and *Path2* is set to *subdirectory2*, then the URL displayed will be *http://www.contoso.com/subdirectory1/subdirectory2*.<br /><br />You can only specify *Path2* if *Path1* is also set.<br/><br/>The path can contain a countdown function. For more details see [Countdown Functions](~/concepts/expanded-text-ads#countdown.md).<br /><br />The path can contain dynamic parameters such as {MatchType}. For a list of supported parameters, see the Bing Ads help article [What tracking or URL parameters can I use?](https://help.bingads.microsoft.com/#apex/3/en/56799/2).<br /><br />The maximum input length of the path is 50 characters with dynamic text strings. However, the ad will fail to display if the path exceeds 15 characters after dynamic text substitution occurs. Note that for languages with double-width characters e.g. Traditional Chinese the maximum input length of the path is 25 characters, and the path is limited to 7 characters after substitution.<br/><br/>**IMPORTANT:** Starting the week of September 18th, the double-width character check will be done according to the characters used instead of the ad group language settings. Double-width characters include Korean, Japanese and Chinese languages characters as well as Emojis. Our support team will contact you if your current ads are affected by this change.<br /><br />The path cannot contain the forward slash (/) or newline (\n) characters.<br /><br />If the path includes a space, it will be replaced with an underscore (_) when the ad is shown.<br/><br/>**Add:** Optional<br/>**Update:** Optional|*string*|
|*Text*|The ad copy.<br /><br />The text must contain at least one word. <br/><br/>The text can contain a countdown function. For more details see [Countdown Functions](~/concepts/expanded-text-ads#countdown.md).<br/><br/> The text can contain dynamic text strings such as {keyword}. For more information, see the Bing Ads help article [Automatically customize your ads with dynamic text parameters](http://help.bingads.microsoft.com/#apex/3/en/50811/1).<br /><br />The maximum input length of the copy is 300 characters, and can contain dynamic text strings. However, the ad will fail to display if the copy exceeds 80 characters after dynamic text substitution occurs. Note that for languages with double-width characters e.g. Traditional Chinese the maximum input length of the copy is 150 characters, and the text is limited to 40 characters after substitution.<br/><br/>**IMPORTANT:** Starting the week of September 18th, the double-width character check will be done according to the characters used instead of the ad group language settings. Double-width characters include Korean, Japanese and Chinese languages characters as well as Emojis. Our support team will contact you if your current ads are affected by this change.<br /><br />The text cannot contain the newline (\n) character.<br/><br/>**Add:** Required<br/>**Update:** Optional|*string*|
|*TitlePart1*|The first part of the ad title. The *TitlePart1* and *TitlePart2* values will be automatically separated by a space, dash, and space (" - ") when the ad is shown, and you may not specify the dash in either of the title parts. Each part of the title must contain at least one word.<br/><br/>The title can contain a countdown function. For more details see [Countdown Functions](~/concepts/expanded-text-ads#countdown.md). <br /><br />The title can contain dynamic text strings such as {keyword}. For more information, see the Bing Ads help article [Automatically customize your ads with dynamic text parameters](http://help.bingads.microsoft.com/#apex/3/en/50811/1).<br /><br />The maximum input length of each title part is 30 characters without dynamic text. If dynamic text strings are used, the maximum input length of *TitlePart1* and *TitlePart2* combined is 77 characters. However, the ad will fail to display if either *TitlePart1* or *TitlePart2* exceeds 30 characters after dynamic text substitution occurs. Note that for languages with double-width characters e.g. Traditional Chinese the maximum input length of each title part is 15 characters without dynamic text. If dynamic text strings are used, the maximum input length of *TitlePart1* and *TitlePart2* combined is 37 characters. However, the ad will fail to display if either *TitlePart1* or *TitlePart2* exceeds 15 characters after dynamic text substitution occurs.<br/><br/>**IMPORTANT:** Starting the week of September 18th, the double-width character check will be done according to the characters used instead of the ad group language settings. Double-width characters include Korean, Japanese and Chinese languages characters as well as Emojis. Our support team will contact you if your current ads are affected by this change.<br /><br />The title cannot contain the newline (\n) character.<br/><br/>**Add:** Required<br/>**Update:** Optional|*string*|
|*TitlePart2*|The second part of the ad title. The *TitlePart1* and *TitlePart2* values will be automatically separated by a space, dash, and space (" - ") when the ad is shown, and you may not specify the dash in either of the title parts. Each part of the title must contain at least one word.<br/><br/>The title can contain a countdown function. For more details see [Countdown Functions](~/concepts/expanded-text-ads#countdown.md). <br /><br />The title can contain dynamic text strings such as {keyword}. For more information, see the Bing Ads help article [Automatically customize your ads with dynamic text parameters](http://help.bingads.microsoft.com/#apex/3/en/50811/1).<br /><br />The maximum input length of each title part is 30 characters without dynamic text. If dynamic text strings are used, the maximum input length of *TitlePart1* and *TitlePart2* combined is 77 characters. However, the ad will fail to display if either *TitlePart1* or *TitlePart2* exceeds 30 characters after dynamic text substitution occurs. Note that for languages with double-width characters e.g. Traditional Chinese the maximum input length of each title part is 15 characters without dynamic text. If dynamic text strings are used, the maximum input length of *TitlePart1* and *TitlePart2* combined is 37 characters. However, the ad will fail to display if either *TitlePart1* or *TitlePart2* exceeds 15 characters after dynamic text substitution occurs.<br/><br/>**IMPORTANT:** Starting the week of September 18th, the double-width character check will be done according to the characters used instead of the ad group language settings. Double-width characters include Korean, Japanese and Chinese languages characters as well as Emojis. Our support team will contact you if your current ads are affected by this change.<br /><br />The title cannot contain the newline (\n) character.<br/><br/>**Add:** Required<br/>**Update:** Optional|*string*|
  
## <a name="InheritedElements"></a>Inherited Elements
The *ExpandedTextAd* object inherits the following elements from the [Ad](../campaign-api/ad-data-object.md) object. 

> [!NOTE]
> The descriptions below are specific to expanded text ads, and might not apply to other objects that inherit the same elements from the [Ad](../campaign-api/ad-data-object.md) object.

|Element|Description|Data Type|
|-----------|---------------|-------------|
  |*AdFormatPreference*|The Ad Format Preference is used to indicate whether or not you prefer the ad copy to be shown to users as a search or native ad. Search ads tend to be written as a call to action, whereas native ads should be written in more of an informational style.<br /><br />By defining at least one ad that should be used as native, the search ads will only be shown in search results.<br /><br />**IMPORTANT:** You must define at least one expanded text ad per ad group that is not native preferred, otherwise the ad copy of all expanded text ads will be eligible for both search and native ads.<br/><br/>Possible values are *Native* and *All*. If set to *All*, the ad will be eligible for both search and native ad formats. If set to *Native*, the ad will only be eligible for the native ad format.<br/><br/>**Add:** Optional. If you do not set this field when creating a text ad, by default the ad format preference will be set to *All*.<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../campaign-api/includes/update-optional-setting-unchanged.md)]|*string*|
|*DevicePreference*|This element is not applicable for expanded text ads.|*long*|
|*EditorialStatus*|The editorial review status of the ad, which indicates whether the ad is pending review, has been approved, or has been disapproved.<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|[AdEditorialStatus](../campaign-api/adeditorialstatus-value-set.md)|
|*FinalAppUrls*|This element is not applicable for expanded text ads.|[AppUrl](../campaign-api/appurl-data-object.md) array|
|*FinalMobileUrls*|The mobile landing page URL.<br /><br />[!INCLUDE[validationrules_finalurls](../campaign-api/includes/validationrules-finalurls.md)]<br /><br />**Note:** This URL is used only if the keyword does not specify a final mobile URL.<br/><br/>**Add:** Optional<br/>**Update:** Optional|*string* array|
|*FinalUrls*|The landing page URL.<br /><br />The domain portion of the URL in combination with the path 1 and path 2 strings cannot exceed 67 characters.<br /><br />[!INCLUDE[validationrules_finalurls](../campaign-api/includes/validationrules-finalurls.md)]Also note that  if this ad's *TrackingUrlTemplate* or *UrlCustomParameters* element are set, then at least one final URL is required.<br /><br />**Note:** This URL is used only if the keyword does not specify a final URL.<br/><br/>**Add:** Required<br/>**Update:** Required|*string* array|
|*ForwardCompatibilityMap*|The list of key and value strings for forward compatibility. This element can be used to avoid otherwise breaking changes when new elements are added in future releases.<br /><br />Forward compatibility changes will be noted here in future releases. There are currently no forward compatibility changes for this object.|*KeyValuePairOfstringstring* array|
|*Id*|The unique Bing Ads identifier of the ad.<br/><br/>**Add:** Read-only<br/>**Update:** Required and Read-Only|*long*|
|*Status*|The status of the ad.<br/><br/>**Add:** Optional<br/>**Update:** Optional|[AdStatus](../campaign-api/adstatus-value-set.md)|
|*TrackingUrlTemplate*|The tracking template to use as a default for all landing page URLs.<br /><br />[!INCLUDE[validationrules_trackingurltemplate](../campaign-api/includes/validationrules-trackingurltemplate.md)]<br/><br/>**Add:** Optional<br/>**Update:** Optional|*string*|
|*Type*|The type of the ad. This value is *ExpandedText* when you retrieve an expanded text ad. For more information about ad types, see the [Ad Data Object Remarks](../campaign-api/ad-data-object.md#remarks).<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|[AdType](../campaign-api/adtype-value-set.md)|
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


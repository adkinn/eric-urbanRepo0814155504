---
title: "Keyword Data Object"
ms.custom: ""
ms.date: "08/15/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 916e6bc1-10b6-4954-b676-dd19aecbabb2
caps.latest.revision: 20
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Keyword Data Object
Defines a keyword.

## Syntax

```xml
<xs:complexType name="Keyword">
  <xs:sequence>
    <xs:element xmlns:q35="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" minOccurs="0" name="BiddingScheme" nillable="true" type="q35:BiddingScheme"/>
    <xs:element minOccurs="0" name="Bid" nillable="true" type="tns:Bid" />
    <xs:element minOccurs="0" name="DestinationUrl" nillable="true" type="xs:string" />
    <xs:element minOccurs="0" name="EditorialStatus" nillable="true" type="tns:KeywordEditorialStatus" />
    <xs:element xmlns:q36="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" minOccurs="0" name="FinalAppUrls" nillable="true" type="q36:ArrayOfAppUrl"/>
    <xs:element xmlns:q37="http://schemas.microsoft.com/2003/10/Serialization/Arrays" minOccurs="0" name="FinalMobileUrls" nillable="true" type="q37:ArrayOfstring"/>
    <xs:element xmlns:q38="http://schemas.microsoft.com/2003/10/Serialization/Arrays" minOccurs="0" name="FinalUrls" nillable="true" type="q38:ArrayOfstring"/>
    <xs:element xmlns:q39="http://schemas.datacontract.org/2004/07/System.Collections.Generic" minOccurs="0" name="ForwardCompatibilityMap" nillable="true" type="q39:ArrayOfKeyValuePairOfstringstring"/>
    <xs:element minOccurs="0" name="Id" nillable="true" type="xs:long" />
    <xs:element minOccurs="0" name="MatchType" nillable="true" type="tns:MatchType" />
    <xs:element minOccurs="0" name="Param1" nillable="true" type="xs:string" />
    <xs:element minOccurs="0" name="Param2" nillable="true" type="xs:string" />
    <xs:element minOccurs="0" name="Param3" nillable="true" type="xs:string" />
    <xs:element minOccurs="0" name="Status" nillable="true" type="tns:KeywordStatus" />
    <xs:element minOccurs="0" name="Text" nillable="true" type="xs:string" />
    <xs:element minOccurs="0" name="TrackingUrlTemplate" nillable="true" type="xs:string"/>
    <xs:element xmlns:q40="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" minOccurs="0" name="UrlCustomParameters" nillable="true" type="q40:CustomParameters"/>
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Bid*|The bid to use when the user’s search  term and the keyword match.<br /><br />To use the [AdGroup](../campaign-api/adgroup-data-object.md) default match type bid, set the *Amount* element of the [Bid](../campaign-api/bid-data-object.md) object to null.<br/><br/>**Add:** Required<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../campaign-api/includes/update-optional-setting-unchanged.md)]|[Bid](../campaign-api/bid-data-object.md)|
|*BiddingScheme*|The bid strategy type for how you want to manage your bids.<br/><br/>For keywords you can use either of the [InheritFromParentBiddingScheme](../campaign-api/inheritfromparentbiddingscheme-data-object.md) or [ManualCpcBiddingScheme](../campaign-api/manualcpcbiddingscheme-data-object.md) objects. <br/><br/>[!INCLUDE[autobid_alert](../campaign-api/includes/autobid-alert.md)]<br /><br />[!INCLUDE[tip_biddingscheme](../campaign-api/includes/tip-biddingscheme.md)]<br/><br/>**Note:** This element is not supported for campaigns of type *Shopping*.<br/><br/>**Add:** Optional. If you do not set this element, then [InheritFromParentBiddingScheme](../campaign-api/inheritfromparentbiddingscheme-data-object.md) is used by default.<br/>**Update:** Optional|[BiddingScheme](../campaign-api/biddingscheme-data-object.md)|
|*DestinationUrl*|The URL of the webpage to take the user to when they click the ad. The keyword’s destination URL is used if specified; otherwise, the ad’s destination URL is used.<br/><br/>[!INCLUDE[deprecate_destinationurl](../campaign-api/includes/deprecate-destinationurl.md)]<br/><br/>**Add:** Optional<br/>**Update:** Optional|*string*|
|*EditorialStatus*|The editorial review status of the keyword, which indicates whether the keyword is pending review, has been approved, or has been disapproved.<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|[KeywordEditorialStatus](../campaign-api/keywordeditorialstatus-value-set.md)|
|*FinalAppUrls*|Reserved for future use.|[AppUrl](../campaign-api/appurl-data-object.md) array|
|*FinalMobileUrls*|The mobile landing page URL. The keyword’s final mobile URL is used if specified; otherwise, the ad’s final mobile URL is used.<br/><br/>**Add:** Optional<br/>**Update:** Optional|*string* array|
|*FinalUrls*|The landing page URL. The keyword’s final URL is used if specified; otherwise, the ad’s final URL is used.<br /><br />[!INCLUDE[validationrules_finalurls](../campaign-api/includes/validationrules-finalurls.md)] Also note that  if the *TrackingUrlTemplate* or *UrlCustomParameters* element are set, then at least one final URL is required.<br/><br/>**Add:** Optional<br/>**Update:** Optional|*string* array|
|*ForwardCompatibilityMap*|The list of key and value strings for forward compatibility. This element can be used to avoid otherwise breaking changes when new elements are added in future releases.<br /><br />**Note:** Forward compatibility changes will be noted here in future releases. There are currently no forward compatibility changes for the *Keyword* object.|*KeyValuePairOfstringstring* array|
|*Id*|The system-generated identifier of the keyword.<br/><br/>**Add:** Read-only<br/>**Update:** Required|*long*|
|*MatchType*|The type of match to compare the keyword and the user's search term.<br/><br/>**Add:** Required<br/>**Update:** Read-only|[MatchType](../campaign-api/matchtype-value-set.md)|
|*Param1*|The string to use as the substitution value in an ad if the ad’s title, text, display URL, or destination URL contains the {Param1} dynamic substitution string.<br /><br />**Note:** Although you can use {Param1} to specify an ad’s destination URL, you are encouraged not to. Instead, you should set the keyword's *DestinationUrl* element.<br /><br />The string can contain a maximum of 1,022 characters. The actual limit depends on the length of the element that references the substitution string. For example, the length of a text ad’s title can contain a maximum of 25 characters.<br /><br />When implementing dynamic text in your ad copy you should provide a default string e.g. {Param1:default} that the system will use if Param1 for a keyword is null or empty, or if including the Param1 substitution value will cause the expanded string to exceed the element’s limit; otherwise the ad will not serve with this keyword. For more information, see the Bing Ads help article [Automatically customize your ads with dynamic text parameters](https://help.bingads.microsoft.com/#apex/3/en/50811/1).<br/><br/>Also note that if the ad group only has one ad, and if that ad uses {Param1} but does not provide a default string e.g. {Param1:default}, then you must supply a valid *Param1* value for that substitution. Otherwise this keyword cannot be added or updated.<br/><br/>**Add:** Optional<br/>**Update:** Optional|*string*|
|*Param2*|The string to use as the substitution value in an ad if the title, text, display URL, or destination URL contains the {Param2} dynamic substitution string.<br /><br />Typically, you use the {Param2} substitution string in the title or text (ad copy description) elements of an ad.<br /><br />The string can contain a maximum of 70 characters. The actual limit depends on the length of the element that references the substitution string. For example, the length of a text ad’s title can contain a maximum of 25 characters.<br /><br />When implementing dynamic text in your ad copy you should provide a default string e.g. {Param2:default} that the system will use if Param2 for a keyword is null or empty, or if including the Param2 substitution value will cause the expanded string to exceed the element’s limit; otherwise the ad will not serve with this keyword. For more information, see the Bing Ads help article [Automatically customize your ads with dynamic text parameters](https://help.bingads.microsoft.com/#apex/3/en/50811/1).<br/><br/>Also note that if the ad group only has one ad, and if that ad uses {Param2} but does not provide a default string e.g. {Param2:default}, then you must supply a valid *Param2* value for that substitution. Otherwise this keyword cannot be added or updated.<br/><br/>**Add:** Optional<br/>**Update:** Optional|*string*|
|*Param3*|The string to use as the substitution value in an ad if the title, text, display URL, or destination URL contains the {Param3} dynamic substitution string.<br /><br />Typically, you use the {Param3} substitution string in the title or text (ad copy description) elements of an ad.<br /><br />The string can contain a maximum of 70 characters. The actual limit depends on the length of the element that references the substitution string. For example, the length of a text ad’s title can contain a maximum of 25 characters.<br /><br />When implementing dynamic text in your ad copy you should provide a default string e.g. {Param3:default} that the system will use if Param3 for a keyword is null or empty, or if including the Param3 substitution value will cause the expanded string to exceed the element’s limit; otherwise the ad will not serve with this keyword. For more information, see the Bing Ads help article [Automatically customize your ads with dynamic text parameters](https://help.bingads.microsoft.com/#apex/3/en/50811/1).<br/><br/>Also note that if the ad group only has one ad, and if that ad uses {Param3} but does not provide a default string e.g. {Param3:default}, then you must supply a valid *Param3* value for that substitution. Otherwise this keyword cannot be added or updated.<br/><br/>**Add:** Optional<br/>**Update:** Optional|*string*|
|*Status*|The keyword’s status. By default, the status is set to Active.<br/><br/>**Add:** Optional<br/>**Update:** Optional|[KeywordStatus](../campaign-api/keywordstatus-value-set.md)|
|*Text*|The keyword text. The text can contain a maximum of 100 characters. You should specify the keyword in the locale of the *Language* value that you specified for the ad group to which the keyword belongs.<br/><br/>**Add:** Required<br/>**Update:** Read-only|*string*|
|*TrackingUrlTemplate*|The tracking template to use as a default for all *FinalUrls* and *FinalMobileUrls*.<br /><br />[!INCLUDE[validationrules_trackingurltemplate](../campaign-api/includes/validationrules-trackingurltemplate.md)]<br/><br/>**Add:** Optional<br/>**Update:** Optional|*string*|
|*UrlCustomParameters*|Your custom collection of key and value parameters for URL tracking.<br /><br />You may include up to 3 individual [CustomParameter](../campaign-api/customparameter-data-object.md) objects within the [CustomParameters](../campaign-api/customparameters-data-object.md) object. Each [CustomParameter](../campaign-api/customparameter-data-object.md) contains a *Key* and *Value* element.<br /><br />On update, set the *UrlCustomParameters* element to null or empty to retain any existing custom parameters. To remove all custom parameters, set the *Parameters* element of the [CustomParameters](../campaign-api/customparameters-data-object.md) object to null or empty. To remove a subset of custom parameters, specify the custom parameters that you want to keep in the *Parameters* element of the [CustomParameters](../campaign-api/customparameters-data-object.md) object.<br /><br />Note that custom parameters for a keyword are allowed, even if the *FinalUrls* element is not specified.<br/><br/>**Add:** Optional<br/>**Update:** Optional|[CustomParameters](../campaign-api/customparameters-data-object.md)|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]

## See Also
[AddKeywords](../campaign-api/addkeywords-service-operation.md)  
[GetKeywordsByAdGroupId](../campaign-api/getkeywordsbyadgroupid-service-operation.md)  
[GetKeywordsByEditorialStatus](../campaign-api/getkeywordsbyeditorialstatus-service-operation.md)  
[GetKeywordsByIds](../campaign-api/getkeywordsbyids-service-operation.md)  
[UpdateKeywords](../campaign-api/updatekeywords-service-operation.md)  


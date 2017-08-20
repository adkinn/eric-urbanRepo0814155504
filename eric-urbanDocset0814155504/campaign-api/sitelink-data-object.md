---
title: "SiteLink Data Object"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5b7b2aff-9ddb-405f-a3ef-495a39aa525a
caps.latest.revision: 12
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# SiteLink Data Object
Defines a site link to include in an ad. The link should take the user to content in your website that is relevant in the context of the ad.

> [!IMPORTANT]
> [!INCLUDE[sitelinks_migration_eta](../campaign-api/includes/sitelinks-migration-eta.md)] 

## Syntax

```xml
\<xs:complexType name="SiteLink">
  \<xs:sequence>
    \<xs:element minOccurs="0" name="Description1" nillable="true" type="xs:string"/>
    \<xs:element minOccurs="0" name="Description2" nillable="true" type="xs:string"/>
    \<xs:element minOccurs="0" name="DestinationUrl" nillable="true" type="xs:string"/>
    \<xs:element minOccurs="0" name="DevicePreference" nillable="true" type="xs:long"/>
    \<xs:element name="DisplayText" nillable="true" type="xs:string"/>
    \<xs:element xmlns:q49="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V10" minOccurs="0" name="FinalAppUrls" nillable="true" type="q49:ArrayOfAppUrl"/>
    \<xs:element xmlns:q50="http://schemas.microsoft.com/2003/10/Serialization/Arrays" minOccurs="0" name="FinalMobileUrls" nillable="true" type="q50:ArrayOfstring"/>
    \<xs:element xmlns:q51="http://schemas.microsoft.com/2003/10/Serialization/Arrays" minOccurs="0" name="FinalUrls" nillable="true" type="q51:ArrayOfstring"/>
    \<xs:element minOccurs="0" name="TrackingUrlTemplate" nillable="true" type="xs:string"/>
    \<xs:element name="Scheduling" type="tns:Schedule" nillable="true" minOccurs="0"/>
    \<xs:element xmlns:q52="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V10" minOccurs="0" name="UrlCustomParameters" nillable="true" type="q52:CustomParameters"/>
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Description1*|The site link description line 1.<br /><br />The maximum input length is 35 characters. If any Traditional Chinese characters are included, the limit is 15 characters.<br/><br/>**NOTE:** Starting the week of September 18th, the limit will be relaxed such that only the Traditional Chinese characters will be counted double against the character limit. Each Traditional Chinese character will count as two and each English character will count only as one character.<br /><br />**Note:** If you specify *Description1* then *Description2* is required.<br/><br/>**Add:** Optional<br/>**Update:** Optional|*string*|
|*Description2*|The site link description line 2.<br /><br />The maximum input length is 35 characters. If any Traditional Chinese characters are included, the limit is 15 characters.<br/><br/>**NOTE:** Starting the week of September 18th, the limit will be relaxed such that only the Traditional Chinese characters will be counted double against the character limit. Each Traditional Chinese character will count as two and each English character will count only as one character.<br /><br />**Note:** If you specify *Description2* then *Description1* is required.<br/><br/>**Add:** Optional<br/>**Update:** Optional|*string*|
|*DestinationUrl*|The URL of the webpage that users are taken to when they click the site link.<br /><br />The URL can contain dynamic parameters such as {MatchType}. For a list of supported parameters, see the Available parameters section within the Bing Ads help article [How do I set up destination URL tracking?](https://help.bingads.microsoft.com/#apex/3/en/51091/2).<br /><br />The URL can contain a maximum of 1,024 characters. If the URL does not specify a protocol, the system uses the HTTP protocol when a user clicks the ad. If the URL specifies the HTTP protocol when you add an ad, the service will remove the http:// protocol string (the HTTP protocol string does not count against the 1,024 character limit); however, the service will not remove an HTTPS protocol string (https://) from the URL.<br/><br/>[!INCLUDE[deprecate_destinationurl](../campaign-api/includes/deprecate-destinationurl.md)]<br /><br />**Add:** Required<br/>**Update:** Optional|*string*|
|*DevicePreference*|This element determines whether the preference is for site links to be displayed on mobile devices or all devices.<br /><br />To specify a preference for mobile devices, set this element to *30001*.<br /><br />To specify all devices, set this element to *0* (zero) or leave the element nil. By default, this element will be nil.<br/><br/>**Add:** Optional<br/>**Update:** Optional|*long*|
|*DisplayText*|The site-link text displayed in the ad.<br /><br />If you specify Description1 or Description2 then the display text can contain a maximum of 25 characters; otherwise, the display text can contain a maximum of 35 characters. If any Traditional Chinese characters are included, the limits are 11 characters given Description1 or Description2, and 15 characters otherwise.<br/><br/>**NOTE:** Starting the week of September 18th, the limit will be relaxed such that only the Traditional Chinese characters will be counted double against the character limit. Each Traditional Chinese character will count as two and each English character will count only as one character.<br/><br/>**Add:** Required<br/>**Update:** Optional|*string*|
|*FinalAppUrls*|Reserved for future use.|[AppUrl](../campaign-api/appurl-data-object.md) array|
|*FinalMobileUrls*|The mobile landing page URL.<br /><br />[!INCLUDE[validationrules_finalurls](../campaign-api/includes/validationrules-finalurls.md)]Also note that you may not specify *FinalMobileUrls* if the *DevicePreference* is set to *30001* (mobile).<br/><br/>**Add:** Optional<br/>**Update:** Optional|*string* array|
|*FinalUrls*|The landing page URL.<br /><br />[!INCLUDE[validationrules_finalurls](../campaign-api/includes/validationrules-finalurls.md)]Also note that  if this site link's *TrackingUrlTemplate* or *UrlCustomParameters* element are set, then at least one final URL is required.<br/><br/>**Add:** Optional<br/>**Update:** Optional|*string* array|
|*Scheduling*|Determines the calendar day and time ranges when the sitelink is eligible to be shown in ads.<br/><br/>**Note:** This element is used instead of - not in addition to - setting the *Scheduling* element of the sitelinks ad extension; A *Scheduling* element is not included in the [SiteLinksAdExtension](../campaign-api/sitelinksadextension-data-object.md) object. (For all other ad extension types including [Sitelink2AdExtension](../campaign-api/sitelink2adextension-data-object.md), the [AdExtension](../campaign-api/adextension-data-object.md) object will include the *Scheduling* element.)<br/><br/>**Add:** Optional<br/>**Update:** Optional. If you set this element null, any existing scheduling set for the sitelink will remain unchanged. If you set this to any non-null [Schedule](../campaign-api/schedule-data-object.md) object, you are effectively replacing existing scheduling settings for the sitelink. To remove all scheduling set this element to an empty [Schedule](../campaign-api/schedule-data-object.md) object.|[Schedule](../campaign-api/schedule-data-object.md)|
|*TrackingUrlTemplate*|The tracking template to use as a default for all *FinalUrls* and *FinalMobileUrls*.<br /><br />[!INCLUDE[validationrules_trackingurltemplate](../campaign-api/includes/validationrules-trackingurltemplate.md)]<br/><br/>**Add:** Optional<br/>**Update:** Optional|*string*|
|*UrlCustomParameters*|Your custom collection of key and value parameters for URL tracking.<br /><br />You may include up to 3 individual [CustomParameter](../campaign-api/customparameter-data-object.md) objects within the [CustomParameters](../campaign-api/customparameters-data-object.md) object. Each [CustomParameter](../campaign-api/customparameter-data-object.md) contains a *Key* and *Value* element.<br /><br />On update, set the *UrlCustomParameters* element to null or empty to retain any existing custom parameters. To remove all custom parameters, set the *Parameters* element of the [CustomParameters](../campaign-api/customparameters-data-object.md) object to null or empty. To remove a subset of custom parameters, specify the custom parameters that you want to keep in the *Parameters* element of the [CustomParameters](../campaign-api/customparameters-data-object.md) object.<br/><br/>**Add:** Optional<br/>**Update:** Optional|[CustomParameters](../campaign-api/customparameters-data-object.md)|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[SiteLinksAdExtension](../campaign-api/sitelinksadextension-data-object.md)  


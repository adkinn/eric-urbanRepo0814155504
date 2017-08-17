---
title: "Sitelink2AdExtension Data Object"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 36f8ef2e-5b5d-4217-8fe9-4f056a862fd9
caps.latest.revision: 11
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Sitelink2AdExtension Data Object
Defines an object with *one* sitelink per ad extension. You can use the sitelink to promote certain products, services, or sections of your website and take potential customers to exactly the information they were searching for. This can increase both click-through-rate and conversions.

> [!IMPORTANT]
> [!INCLUDE[sitelinks_migration_eta](../campaign-api/includes/sitelinks-migration-eta.md)] 

## Syntax

```xml
<xs:complexType name="Sitelink2AdExtension">
  <xs:complexContent mixed="false">
    <xs:extension base="tns:AdExtension">
      <xs:sequence>
        <xs:element name="Description1" nillable="true" type="xs:string"/>
        <xs:element name="Description2" nillable="true" type="xs:string"/>
        <xs:element name="DestinationUrl" nillable="true" type="xs:string"/>
        <xs:element name="DisplayText" nillable="true" type="xs:string"/>
        <xs:element xmlns:q67="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V10" minOccurs="0" name="FinalAppUrls" nillable="true" type="q67:ArrayOfAppUrl"/>
        <xs:element xmlns:q68="http://schemas.microsoft.com/2003/10/Serialization/Arrays" minOccurs="0" name="FinalMobileUrls" nillable="true" type="q68:ArrayOfstring"/>
        <xs:element xmlns:q69="http://schemas.microsoft.com/2003/10/Serialization/Arrays" minOccurs="0" name="FinalUrls" nillable="true" type="q69:ArrayOfstring"/>
        <xs:element minOccurs="0" name="TrackingUrlTemplate" nillable="true" type="xs:string"/>
        <xs:element xmlns:q70="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V10" minOccurs="0" name="UrlCustomParameters" nillable="true" type="q70:CustomParameters"/>
      </xs:sequence>
    </xs:extension>
  </xs:complexContent>
</xs:complexType>
```

## <a name="Elements"></a>Elements
The *Sitelink2AdExtension* object inherits elements from the [AdExtension](../campaign-api/adextension-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#InheritedElements) below.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Description1*|The site link description line 1.<br /><br />The maximum input length is 35 characters. If any Traditional Chinese characters are included, the limit is 15 characters.<br/><br/>**NOTE:** Starting the week of September 18th, the limit will be relaxed such that only the Traditional Chinese characters will be counted double against the character limit. Each Traditional Chinese character will count as two and each English character will count only as one character.<br /><br />**Note:** If you specify *Description1* then *Description2* is required.<br/><br/>**Add:** Optional<br/>**Update:** Optional|*string*|
|*Description2*|The site link description line 2.<br /><br />The maximum input length is 35 characters. If any Traditional Chinese characters are included, the limit is 15 characters.<br/><br/>**NOTE:** Starting the week of September 18th, the limit will be relaxed such that only the Traditional Chinese characters will be counted double against the character limit. Each Traditional Chinese character will count as two and each English character will count only as one character.<br /><br />**Note:** If you specify *Description2* then *Description1* is required.<br/><br/>**Add:** Optional<br/>**Update:** Optional|*string*|
|*DestinationUrl*|[!INCLUDE[deprecate_destinationurl](../campaign-api/includes/deprecate-destinationurl.md)]The URL of the webpage that users are taken to when they click the site link.<br /><br />The URL can contain dynamic parameters such as {MatchType}. For a list of supported parameters, see the *Available parameters* section within the Bing Ads help article [Learn more about each click: Use URL tracking](http://help.bingads.microsoft.com/#apex/3/en/51091/2).<br /><br />The URL can contain a maximum of 1,024 characters. If the URL does not specify a protocol, the system uses the HTTP protocol when a user clicks the ad. If the URL specifies the HTTP protocol when you add an ad, the service will remove the http:// protocol string (the HTTP protocol string does not count against the 1,024 character limit); however, the service will not remove an HTTPS protocol string (https://) from the URL.<br/><br/>**Add:** Required<br/>**Update:** Optional|*string*|
|*DisplayText*|The site-link text displayed in the ad.<br /><br />If you specify Description1 or Description2 then the display text can contain a maximum of 25 characters; otherwise, the display text can contain a maximum of 35 characters. If any Traditional Chinese characters are included, the limits are 11 characters given Description1 or Description2, and 15 characters otherwise.<br/><br/>**NOTE:** Starting the week of September 18th, the limit will be relaxed such that only the Traditional Chinese characters will be counted double against the character limit. Each Traditional Chinese character will count as two and each English character will count only as one character.<br/><br/>**Add:** Required<br/>**Update:** Optional|*string*|
|*FinalAppUrls*|Reserved for future use.|[AppUrl](../campaign-api/appurl-data-object.md) array|
|*FinalMobileUrls*|The mobile landing page URL.<br /><br />[!INCLUDE[validationrules_finalurls](../campaign-api/includes/validationrules-finalurls.md)]Also note that you may not specify *FinalMobileUrls* if the *DevicePreference* is set to *30001* (mobile).<br/><br/>**Add:** Optional<br/>**Update:** Optional|*string* array|
|*FinalUrls*|The landing page URL.<br /><br />[!INCLUDE[validationrules_finalurls](../campaign-api/includes/validationrules-finalurls.md)]Also note that  if this site link's *TrackingUrlTemplate* or *UrlCustomParameters* element are set, then at least one final URL is required.<br/><br/>**Add:** Optional<br/>**Update:** Optional|*string* array|
|*TrackingUrlTemplate*|The tracking template to use as a default for all *FinalUrls* and *FinalMobileUrls*.<br /><br />[!INCLUDE[validationrules_trackingurltemplate](../campaign-api/includes/validationrules-trackingurltemplate.md)]<br/><br/>**Add:** Optional<br/>**Update:** Optional|*string*|
|*UrlCustomParameters*|Your custom collection of key and value parameters for URL tracking.<br /><br />You may include up to 3 individual [CustomParameter](../campaign-api/customparameter-data-object.md) objects within the [CustomParameters](../campaign-api/customparameters-data-object.md) object. Each [CustomParameter](../campaign-api/customparameter-data-object.md) contains a *Key* and *Value* element.<br /><br />On update, set the *UrlCustomParameters* element to null or empty to retain any existing custom parameters. To remove all custom parameters, set the *Parameters* element of the [CustomParameters](../campaign-api/customparameters-data-object.md) object to null or empty. To remove a subset of custom parameters, specify the custom parameters that you want to keep in the *Parameters* element of the [CustomParameters](../campaign-api/customparameters-data-object.md) object.<br/><br/>**Add:** Optional<br/>**Update:** Optional|[CustomParameters](../campaign-api/customparameters-data-object.md)|

## <a name="InheritedElements"></a>Inherited Elements
The *Sitelink2AdExtension* object inherits the following elements from the [AdExtension](../campaign-api/adextension-data-object.md) object. 

> [!NOTE]
> The descriptions below are specific to sitelink2 ad extensions, and might not apply to other objects that inherit the same elements from the [AdExtension](../campaign-api/adextension-data-object.md) object.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*DevicePreference*|This element determines whether the preference is for the ad extension to be displayed on mobile devices or all devices.<br /><br />To specify a preference for mobile devices, set this element to *30001*.<br /><br />To specify all devices, set this element to *0* (zero) or leave the element nil. By default, this element will be nil.<br/><br/>**Add:** Optional<br/>**Update:** Optional|*long*|
|*ForwardCompatibilityMap*|The list of key and value strings for forward compatibility. This element can be used to avoid otherwise breaking changes when new elements are added in future releases.<br /><br />There are currently no forward compatibility changes for the *AdExtension* object.<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|*KeyValuePairOfstringstring* array|
|*Id*|The unique Bing Ads identifier of the ad extension.<br/><br/>**Add:** Read-only and Required<br/>**Update:** Read-only|*long*|
|*Scheduling*|Determines the calendar day and time ranges when the ad extension is eligible to be shown in ads.<br/><br/>**Add:** Optional<br/>**Update:** Optional. If you set this element null, any existing scheduling set for the ad extension will remain unchanged. If you set this to any non-null [Schedule](../campaign-api/schedule-data-object.md) object, you are effectively replacing existing scheduling settings for the ad extension. To remove all scheduling set this element to an empty [Schedule](../campaign-api/schedule-data-object.md) object.|[Schedule](../campaign-api/schedule-data-object.md)|
|*Status*|The status of the ad extension. The value will always be *Active* because the Campaign Management service does not return deleted ad extensions.<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|[AdExtensionStatus](../campaign-api/adextensionstatus-value-set.md)|
|*Type*|The type of the ad extension. This value is *Sitelink2AdExtension* when you retrieve a sitelink2 ad extension. <br/><br/>**Add:** Read-only<br/>**Update:** Read-only<br/><br/>For more information about ad extension types, see the [Ad Extension Data Object Remarks](../campaign-api/adextension-data-object.md#remarks).|*string*|
|*Version*|The number of times the contents of the ad extension has been updated. The version is set to 1 when you add the extension and is incremented each time it’s revised.<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|*int*|


## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]

## See Also

[AdExtensionAssociation](../campaign-api/adextensionassociation-data-object.md)  
[AddAdExtensions](../campaign-api/addadextensions-service-operation.md)  
[GetAdExtensionsByIds](../campaign-api/getadextensionsbyids-service-operation.md)  
[UpdateAdExtensions](../campaign-api/updateadextensions-service-operation.md)  
[GetAccountMigrationStatuses](../campaign-api/getaccountmigrationstatuses-service-operation.md)  

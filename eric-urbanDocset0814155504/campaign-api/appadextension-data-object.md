---
title: "AppAdExtension Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ab00a360-a30f-4813-a36d-7295e7b3aaa7
caps.latest.revision: 18
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AppAdExtension Data Object
Defines an app ad extension that can be included in a text ad.

You can associate an app ad extension with one or more campaigns and ad groups. Each campaign or ad group can be associated with multiple app ad extensions.

## Syntax

```xml
<xs:complexType name="AppAdExtension">
  <xs:complexContent mixed="false">
    <xs:extension base="tns:AdExtension">
      <xs:sequence>
        <xs:element name="AppPlatform" type="xs:string" nillable="true"/>
        <xs:element name="AppStoreId" type="xs:string" nillable="true"/>
        <xs:element name="DestinationUrl" type="xs:string" nillable="true"/>
        <xs:element name="DisplayText" type="xs:string" nillable="true"/> 
        <xs:element xmlns:q49="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V10" minOccurs="0" name="FinalAppUrls" nillable="true" type="q49:ArrayOfAppUrl"/>
        <xs:element xmlns:q50="http://schemas.microsoft.com/2003/10/Serialization/Arrays" minOccurs="0" name="FinalMobileUrls" nillable="true" type="q50:ArrayOfstring"/>
        <xs:element xmlns:q51="http://schemas.microsoft.com/2003/10/Serialization/Arrays" minOccurs="0" name="FinalUrls" nillable="true" type="q51:ArrayOfstring"/>
        <xs:element minOccurs="0" name="TrackingUrlTemplate" nillable="true" type="xs:string"/>
        <xs:element xmlns:q52="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V10" minOccurs="0" name="UrlCustomParameters" nillable="true" type="q52:CustomParameters"/> 
      </xs:sequence>
    </xs:extension>
  </xs:complexContent>
</xs:complexType>
```

## <a name="Elements"></a>Elements
The *AppAdExtension* object inherits elements from the [AdExtension](../campaign-api/adextension-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#inheritedelements) below.

> [!IMPORTANT]
> If you set *AppPlatform* to a platform that conflicts with the *AppStoreId* or vice versa, the service operation will not throw an error; however, the app ad extension will not deliver. For example if you set the *AppPlatform* to Windows and used an *AppStoreId* provisioned for the iOS app store, the ad extension will not deliver.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AppPlatform*|The application platform.<br /><br />Possible values include iOS, Android, Windows Phone, and Windows.<br/><br/>**Add:** Required<br/>**Update:** Optional|*string*|
|*AppStoreId*|The application identifier provided by the app store.<br /><br />**Note:** If the application is new, please expect to wait 4-7 days before the ad will be eligible to deliver.<br/><br/>**Add:** Required<br/>**Update:** Optional|*string*|
|*DestinationUrl*|The URL of the app store download webpage that users are taken to when they click the app extension link.<br /><br />The URL can contain dynamic text strings such as {keyword}. For a list of supported parameters, see the Available parameters section within the Bing Ads help article [What tracking or URL parameters can I use?](http://help.bingads.microsoft.com/#apex/3/en/56799/2).<br /><br />The URL can contain a maximum of 1,024 characters. If the URL does not specify a protocol, the system uses the HTTP protocol when a user clicks the ad. If the URL specifies the HTTP protocol when you add an ad, the service will remove the http:// protocol string (the HTTP protocol string does not count against the 1,024 character limit); however, the service will not remove an HTTPS protocol string (https://) from the URL.<br/><br/>**Add:** Required<br/>**Update:** Optional|*string*|
|*DisplayText*|The text displayed in the app ad extension. The text can contain a maximum of 35 characters.<br/><br/>**Add:** Required<br/>**Update:** Optional|*string*|
|*FinalAppUrls*|Reserved for future use.|[AppUrl](../campaign-api/appurl-data-object.md) array|
|*FinalMobileUrls*|Reserved for future use.|*string* array|
|*FinalUrls*|Reserved for future use.|*string* array|
|*TrackingUrlTemplate*|Reserved for future use.|*string*|
|*UrlCustomParameters*|Reserved for future use.|[CustomParameters](../campaign-api/customparameters-data-object.md)|

## <a name="InheritedElements"></a>Inherited Elements
The *AppAdExtension* object inherits the following elements from the [AdExtension](../campaign-api/adextension-data-object.md) object. 

> [!NOTE]
> The descriptions below are specific to app ad extensions, and might not apply to other objects that inherit the same elements from the [AdExtension](../campaign-api/adextension-data-object.md) object.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*DevicePreference*|This element determines whether the preference is for the app extension to be displayed on mobile devices or all devices.<br /><br />To specify a preference for mobile devices, set this element to *30001*.<br /><br />To specify all devices, set this element to *0* (zero) or leave the element nil. By default, this element will be nil.<br/><br/>**Add:** Optional<br/>**Update:** Optional|*long*|
|*ForwardCompatibilityMap*|The list of key and value strings for forward compatibility. This element can be used to avoid otherwise breaking changes when new elements are added in future releases.<br /><br />There are currently no forward compatibility changes for the *AdExtension* object.<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|*KeyValuePairOfstringstring* array|
|*Id*|The unique Bing Ads identifier of the ad extension.<br/><br/>**Add:** Read-only and Required<br/>**Update:** Read-only|*long*|
|*Scheduling*|Determines the calendar day and time ranges when the ad extension is eligible to be shown in ads.<br/><br/>**Add:** Optional<br/>**Update:** Optional. If you set this element null, any existing scheduling set for the ad extension will remain unchanged. If you set this to any non-null [Schedule](../campaign-api/schedule-data-object.md) object, you are effectively replacing existing scheduling settings for the ad extension. To remove all scheduling set this element to an empty [Schedule](../campaign-api/schedule-data-object.md) object.|[Schedule](../campaign-api/schedule-data-object.md)|
|*Status*|The status of the ad extension. The value will always be *Active* because the Campaign Management service does not return deleted ad extensions.<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|[AdExtensionStatus](../campaign-api/adextensionstatus-value-set.md)|
|*Type*|The type of the ad extension. This value is *AppAdExtension* when you retrieve an app ad extension.<br/><br/>**Add:** Read-only<br/>**Update:** Read-only<br/><br/>For more information about ad extension types, see the [Ad Extension Data Object Remarks](../campaign-api/adextension-data-object.md#remarks).|*string*|
|*Version*|The number of times the contents of the ad extension has been updated. The version is set to 1 when you add the extension and is incremented each time it?s revised.<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|*int*|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[AdExtensionAssociation](../campaign-api/adextensionassociation-data-object.md)  
[AddAdExtensions](../campaign-api/addadextensions-service-operation.md)  
[GetAdExtensionsByIds](../campaign-api/getadextensionsbyids-service-operation.md)  
[UpdateAdExtensions](../campaign-api/updateadextensions-service-operation.md)  


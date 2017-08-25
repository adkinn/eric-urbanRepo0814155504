---
title: "ImageAdExtension Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0bdfaf45-f60a-4aa3-99f0-f462b833885d
caps.latest.revision: 15
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# ImageAdExtension Data Object
Defines an ad extension that specifies an image with alternative text to include in a text ad.

## Syntax

```xml
<xs:complexType name="ImageAdExtension">
  <xs:complexContent mixed="false">
    <xs:extension base="tns:AdExtension">
      <xs:sequence>
        <xs:element type="xs:string" name="AlternativeText" nillable="true"/>
        <xs:element type="xs:string" name="Description" nillable="true" minOccurs="0"/>
        <xs:element type="xs:string" name="DestinationUrl" nillable="true" minOccurs="0"/>
        <xs:element xmlns:q57="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V10" minOccurs="0" name="FinalAppUrls" nillable="true" type="q57:ArrayOfAppUrl"/>
        <xs:element xmlns:q58="http://schemas.microsoft.com/2003/10/Serialization/Arrays" minOccurs="0" name="FinalMobileUrls" nillable="true" type="q58:ArrayOfstring"/>
        <xs:element xmlns:q59="http://schemas.microsoft.com/2003/10/Serialization/Arrays" minOccurs="0" name="FinalUrls" nillable="true" type="q59:ArrayOfstring"/>
        <xs:element xmlns:q60="http://schemas.microsoft.com/2003/10/Serialization/Arrays" name="ImageMediaIds" nillable="true" type="q60:ArrayOflong"/>
        <xs:element minOccurs="0" name="TrackingUrlTemplate" nillable="true" type="xs:string"/>
        <xs:element xmlns:q61="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V10" minOccurs="0" name="UrlCustomParameters" nillable="true" type="q61:CustomParameters"/> 
      </xs:sequence>
    </xs:extension>
  </xs:complexContent>
</xs:complexType>
```

## <a name="Elements"></a>Elements
The *ImageAdExtension* object inherits elements from the [AdExtension](../campaign-api/adextension-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#inheritedelements) below.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AlternativeText*|Alternative description of the image media for usability. If the image could not be displayed, the alternative text is used instead.<br /><br />The maximum length for this element is 35 characters.<br/><br/>**Add:** Optional<br/>**Update:** Optional|*string*|
|*Description*|Description that can be used by the advertiser, agency, or account manager to track, label, or manage image media. This description is not displayed with the ad or image.<br /><br />The maximum length for this element is 100 characters.<br/><br/>**Add:** Optional<br/>**Update:** Optional|*string*|
|*DestinationUrl*|The URL of the webpage to take the user to when they click the image.<br /><br />The URL can contain dynamic text strings such as {keyword}. For more information, see [What tracking or URL parameters can I use?](https://help.bingads.microsoft.com/#apex/3/en/56799/2).<br /><br />The URL can contain a maximum of 1,024 characters. If the URL does not specify a protocol, the system uses the HTTP protocol when a user clicks the ad. If the URL specifies the HTTP protocol when you add an ad, the service will remove the *http://* protocol string (the HTTP protocol string does not count against the 1,024 character limit); however, the service will not remove an HTTPS protocol string (https://) from the URL.<br /><br />**Note:** If the URL is not specified for the image ad extension, the URL of the ad is used.<br/><br/>**Add:** Optional<br/>**Update:** Optional|*string*|
|*DevicePreference*|Reserved for future use.|*long*|
|*FinalAppUrls*|Reserved for future use.|[AppUrl](../campaign-api/appurl-data-object.md) array|
|*FinalMobileUrls*|Reserved for future use.|*string* array|
|*FinalUrls*|Reserved for future use.|*string* array|
|*ImageMediaIds*|The identifiers of the images to include in the ad. You may not specify media identifiers for more than one image of the same aspect ratio. In other words each of  the referenced images must have different aspect ratios.<br /><br />You can specify up to four (4) image media  identifiers. While the minimum required is one image media ID, in order to qualify for all native ad placements you must provide four image media identifiers, where each ID corresponds to an [Image](../campaign-api/image-data-object.md) of one of the four supported [Media](../campaign-api/media-data-object.md) types (aspect ratios). The supported aspect ratios for native ads are 16:9, 1.5:1, 4:3, and 1.2:1. For more information see the [Image](../campaign-api/image-data-object.md) data object reference documentation.<br /><br />You can get the identifier of each [Image](../campaign-api/image-data-object.md) when you add them to the image library by calling the [AddMedia](../campaign-api/addmedia-service-operation.md) operation. Otherwise after the media has been added to your image library you can get the media identifiers with the [GetMediaMetaDataByAccountId](../campaign-api/getmediametadatabyaccountid-service-operation.md) operation.<br/><br/>**Add:** Required<br/>**Update:** Optional|*long*|
|*TrackingUrlTemplate*|Reserved for future use.|*string*|
|*UrlCustomParameters*|Reserved for future use.|[CustomParameters](../campaign-api/customparameters-data-object.md)|

## <a name="InheritedElements"></a>Inherited Elements
The *ImageAdExtension* object inherits the following elements from the [AdExtension](../campaign-api/adextension-data-object.md) object. 

> [!NOTE]
> The descriptions below are specific to image ad extensions, and might not apply to other objects that inherit the same elements from the [AdExtension](../campaign-api/adextension-data-object.md) object.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*ForwardCompatibilityMap*|The list of key and value strings for forward compatibility. This element can be used to avoid otherwise breaking changes when new elements are added in future releases.<br /><br />There are currently no forward compatibility changes for the *AdExtension* object.<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|*KeyValuePairOfstringstring* array|
|*Id*|The unique Bing Ads identifier of the ad extension.<br/><br/>**Add:** Read-only and Required<br/>**Update:** Read-only|*long*|
|*Scheduling*|This element is not supported for image ad extensions. Scheduling is supported for other ad extension types.|[Schedule](../campaign-api/schedule-data-object.md)|
|*Status*|The status of the ad extension. The value will always be *Active* because the Campaign Management service does not return deleted ad extensions.<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|[AdExtensionStatus](../campaign-api/adextensionstatus-value-set.md)|
|*Type*|The type of the ad extension. This value is *ImageAdExtension* when you retrieve an image ad extension. <br/><br/>**Add:** Read-only<br/>**Update:** Read-only<br/><br/>For more information about ad extension types, see the [Ad Extension Data Object Remarks](../campaign-api/adextension-data-object.md#remarks).|*string*|
|*Version*|The number of times the contents of the ad extension has been updated. The version is set to 1 when you add the extension and is incremented each time it?s revised.<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|*int*|


## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[AdExtensionAssociation](../campaign-api/adextensionassociation-data-object.md)  
[AddAdExtensions](../campaign-api/addadextensions-service-operation.md)  
[GetAdExtensionsByIds](../campaign-api/getadextensionsbyids-service-operation.md)  
[UpdateAdExtensions](../campaign-api/updateadextensions-service-operation.md)  


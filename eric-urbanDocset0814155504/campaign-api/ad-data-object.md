---
title: "Ad Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c3150088-32b0-41d0-b91d-5e65e072eb26
caps.latest.revision: 24
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Ad Data Object
Defines the base object of an ad.

Do not try to instantiate an *Ad*. You can create one or more following objects that derive from it.
- [AppInstallAd](../campaign-api/appinstallad-data-object.md)
- [DynamicSearchAd](../campaign-api/dynamicsearchad-data-object.md)
- [ExpandedTextAd](../campaign-api/expandedtextad-data-object.md)
- [TextAd](../campaign-api/textad-data-object.md)
- [ProductAd](../campaign-api/productad-data-object.md) 

## Syntax

```xml
\<xs:complexType name="Ad">
  \<xs:sequence>
    \<xs:element minOccurs="0" name="AdFormatPreference" nillable="true" type="xs:string" />
    \<xs:element minOccurs="0" name="DevicePreference" nillable="true" type="xs:long" />
    \<xs:element minOccurs="0" name="EditorialStatus" nillable="true" type="tns:AdEditorialStatus" />
    \<xs:element xmlns:q1="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" minOccurs="0" name="FinalAppUrls" nillable="true" type="q1:ArrayOfAppUrl"/>
    \<xs:element xmlns:q2="http://schemas.microsoft.com/2003/10/Serialization/Arrays" minOccurs="0" name="FinalMobileUrls" nillable="true" type="q2:ArrayOfstring"/>
    \<xs:element xmlns:q3="http://schemas.microsoft.com/2003/10/Serialization/Arrays" minOccurs="0" name="FinalUrls" nillable="true" type="q3:ArrayOfstring"/>
    \<xs:element xmlns:q4="http://schemas.datacontract.org/2004/07/System.Collections.Generic" minOccurs="0" name="ForwardCompatibilityMap" nillable="true" type="q4:ArrayOfKeyValuePairOfstringstring"/>
    \<xs:element minOccurs="0" name="Id" nillable="true" type="xs:long" />
    \<xs:element minOccurs="0" name="Status" nillable="true" type="tns:AdStatus" />
    \<xs:element minOccurs="0" name="TrackingUrlTemplate" nillable="true" type="xs:string"/>
    \<xs:element minOccurs="0" name="Type" nillable="true" type="tns:AdType" />
    \<xs:element xmlns:q5="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" minOccurs="0" name="UrlCustomParameters" nillable="true" type="q5:CustomParameters"/>
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AdFormatPreference*|The Ad Format Preference is used to indicate whether or not you prefer the ad copy to be shown to users as a search or native ad. Search ads tend to be written as a call to action, whereas native ads should be written in more of an informational style.<br /><br />By defining at least one ad that should be used as native, the search ads will only be shown in search results.<br/><br/>Possible values are *Native* and *All*. If set to *All*, the ad will be eligible for both search and native ad formats. If set to *Native*, the ad will only be eligible for the native ad format.<br /><br />Ad Format Preference is only supported for [ExpandedTextAd](../campaign-api/expandedtextad-data-object.md) and [TextAd](../campaign-api/textad-data-object.md) objects.|*string*|
|*DevicePreference*|Determines the device preference for showing the ad. <br /><br />Device preference is only supported for [AppInstallAd](../campaign-api/appinstallad-data-object.md) and [TextAd](../campaign-api/textad-data-object.md) objects.|*long*|
|*EditorialStatus*|The editorial review status of the ad, which indicates whether the ad is pending review, has been approved, or has been disapproved.|[AdEditorialStatus](../campaign-api/adeditorialstatus-value-set.md)|
|*FinalAppUrls*|Reserved for future use.|[AppUrl](../campaign-api/appurl-data-object.md) array|
|*FinalMobileUrls*|The mobile landing page URL. <br /><br />Final mobile URLs is only supported for text ads. For more details see [TextAd](../campaign-api/textad-data-object.md).|*string* array|
|*FinalUrls*|The last or final URL where a user is ultimately taken, whether or not the click to final URL path included any redirects.<br /><br />Final URLs are only supported for [AppInstallAd](../campaign-api/appinstallad-data-object.md), [ExpandedTextAd](../campaign-api/expandedtextad-data-object.md), and [TextAd](../campaign-api/textad-data-object.md) objects.|*string* array|
|*ForwardCompatibilityMap*|The list of key and value strings for forward compatibility. This element can be used to avoid otherwise breaking changes when new elements are added in future releases.<br /><br />Forward compatibility changes will be noted here in future releases. There are currently no forward compatibility changes for this object.|*KeyValuePairOfstringstring* array|
|*Id*|The unique Bing Ads identifier for the ad.|*long*|
|*Status*|The status of the ad.|[AdStatus](../campaign-api/adstatus-value-set.md)|
|*TrackingUrlTemplate*|The tracking template to use as a default for all landing page URLs.<br /><br />Tracking template is only supported for [AppInstallAd](../campaign-api/appinstallad-data-object.md), [DynamicSearchAd](../campaign-api/dynamicsearchad-data-object.md), [ExpandedTextAd](../campaign-api/expandedtextad-data-object.md), and [TextAd](../campaign-api/textad-data-object.md) objects. It is not supported for the [ProductAd](../campaign-api/productad-data-object.md) object.|*string*|
|*Type*|The type of the ad. For more information about ad types, see the [Remarks](#remarks).|[AdType](../campaign-api/adtype-value-set.md)|
|*UrlCustomParameters*|Your custom collection of key and value parameters for URL tracking.<br /><br />Custom parameters are only supported for [AppInstallAd](../campaign-api/appinstallad-data-object.md), [DynamicSearchAd](../campaign-api/dynamicsearchad-data-object.md), [ExpandedTextAd](../campaign-api/expandedtextad-data-object.md), and [TextAd](../campaign-api/textad-data-object.md) objects. They are not supported for the [ProductAd](../campaign-api/productad-data-object.md) object.|[CustomParameters](../campaign-api/customparameters-data-object.md)|

## <a name="remarks"></a>Remarks
For Java and the .NET languages, do not set the *Type* element because the value is determined by whether you instantiate an expanded text ad or another type of ad.

If you generate the SOAP manually, use the *type* attribute of the *Ad* node as shown in the following example, to specify whether the ad is an expanded text ad or another type of ad.

```xml
\<Ads xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
  \<Ad i:type="ExpandedTextAd">
    \<DevicePreference i:nil="true" />
    \<EditorialStatus i:nil="true" />
    \<ForwardCompatibilityMap i:nil="true" />
    \<Id i:nil="true" />
    \<Status i:nil="true" />
    \<FinalUrls xmlns:a="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
      \<a:string>http://www.contoso.com/womenshoesale\</a:string>
    </FinalUrls>
    <Path1>seattle</Path1>
    <Path2>shoe sale</Path2>
    <Text>Find New Customers & Increase Sales! Start Advertising on Contoso Today.</Text>
    <TitlePart1>Contoso</TitlePart1>
    <TitlePart2>Fast & Easy Setup</TitlePart2>
  </Ad>
</Ads>
```

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[AddAds](../campaign-api/addads-service-operation.md)  
[DeleteAds](../campaign-api/deleteads-service-operation.md)  
[GetAdsByAdGroupId](../campaign-api/getadsbyadgroupid-service-operation.md)  
[GetAdsByEditorialStatus](../campaign-api/getadsbyeditorialstatus-service-operation.md)  
[GetAdsByIds](../campaign-api/getadsbyids-service-operation.md)  
[UpdateAds](../campaign-api/updateads-service-operation.md)  


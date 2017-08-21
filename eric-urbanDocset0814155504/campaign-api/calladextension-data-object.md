---
title: "CallAdExtension Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 04ae6deb-7c6c-4204-abc8-205218a15dc2
caps.latest.revision: 21
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# CallAdExtension Data Object
Defines an object that specifies a click-to-call phone number to include in a text ad.

You can associate a call ad extension with one or more campaigns; however, a campaign can be associated with only one call ad extension.

## Syntax

```xml
<xs:complexType name="CallAdExtension">
  <xs:complexContent mixed="false">
    <xs:extension base="tns:AdExtension">
      <xs:sequence>
        <xs:element name="CountryCode" nillable="true" type="xs:string" />
        <xs:element name="IsCallOnly" type="xs:boolean" />
        <xs:element minOccurs="0" name="IsCallTrackingEnabled" nillable="true" type="xs:boolean" />
        <xs:element minOccurs="0" name="PhoneNumber" nillable="true" type="xs:string" />
        <xs:element minOccurs="0" name="RequireTollFreeTrackingNumber" nillable="true" type="xs:boolean" /> 
      </xs:sequence>
    </xs:extension>
  </xs:complexContent>
</xs:complexType>
```

## <a name="Elements"></a>Elements
The *CallAdExtension* object inherits elements from the [AdExtension](../campaign-api/adextension-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#InheritedElements) below.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*CountryCode*|The country code where the phone number is registered. The country code must contain a 2 character country code. For a list of country code values, see [Geographical Location Codes](http://msdn.microsoft.com/library/bing-ads-geographical-location-codes.aspx).<br/><br/>**Add:** Required<br/>**Update:** Optional|*string*|
|*IsCallOnly*|The option to show both your phone number and website, or just your phone number, to people seeing your ads on a smartphone. You might want to show only your phone number if your business requires that you talk to each customer.<br/><br/>Set this property to *true* if you want the ad extension to only show the phone number without a link to your website, and otherwise if you want the ad extension include a link to your website in addition to the phone number set it to *false*.<br/><br/>**Add:** Optional. If you do not specify this field or leave it empty, the default value of *false* will be set and the ad extension will include a link to your website in addition to the phone number.<br/>**Update:** Optional|*boolean*|
|*IsCallTrackingEnabled*|Determines whether call tracking is enabled for the call ad extension.<br /><br />**Note:** Call tracking is only supported in the United States and United Kingdom.<br /><br />Set this property to *true* to enable call tracking, and otherwise set it to *false*.<br/><br/>**Add:** Optional. If you do not specify this field or leave it empty, the default value of *false* will be set.<br/>**Update:** Optional|*boolean*|
|*PhoneNumber*|The clickable phone number to include in the ad. <br /><br />The phone number can contain a maximum of 35 characters and must be valid for the specified country.<br /><br />If the campaign includes call and location ad extensions, this phone number will override the phone number specified in the location ad extensions.<br /><br />Note that the phone number may be reformatted. For example, if you set phone number to 4255551212, it would be reformatted to (425) 555-1212.<br/><br/>**Add:** Required<br/>**Update:** Optional|*string*|
|*RequireTollFreeTrackingNumber*|You can either use your own phone number or use a Bing Ads forwarding phone number. A Bing Ads forwarding phone number is a unique phone number that is routed to your business phone number. With a Bing Ads forwarding number, you can track all calls from your ad so that you can analyze the ad’s performance. This element determines whether a toll-free Bing Ads forwarding phone number should be created for call tracking. This element can only be set if *IsCallTrackingEnabled* is also true.<br /><br />Set this property to *true* if a Bing Ads forwarding phone number should be created for call tracking, and otherwise set it to *false*.<br /><br />**Important:** Beginning the week of August 14th, 2017 you can no longer create a new toll-free Bing Ads forwarding phone number. If you set this value *True* then the operation will succeed; however, a toll-free number will not be created and when you retrieve the call ad extension this property will be set to *False*. If a toll-free forwarding number was provisioned prior to the week of August 14th, 2017 then this property will be *True* if the number is still active when you retrieve the call ad extension.<br/><br/>**Add:** Optional. If you do not specify this field or leave it empty, the default value of *false* will be set.<br/>**Update:** Optional|*boolean*|

## <a name="InheritedElements"></a>Inherited Elements
The *CallAdExtension* object inherits the following elements from the [AdExtension](../campaign-api/adextension-data-object.md) object. 

> [!NOTE]
> The descriptions below are specific to call ad extensions, and might not apply to other objects that inherit the same elements from the [AdExtension](../campaign-api/adextension-data-object.md) object.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*DevicePreference*|Reserved for future use.|*long*|
|*ForwardCompatibilityMap*|The list of key and value strings for forward compatibility. This element can be used to avoid otherwise breaking changes when new elements are added in future releases.<br /><br />There are currently no forward compatibility changes for the *AdExtension* object.<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|*KeyValuePairOfstringstring* array|
|*Id*|The unique Bing Ads identifier of the ad extension.<br/><br/>**Add:** Read-only and Required<br/>**Update:** Read-only|*long*|
|*Scheduling*|Determines the calendar day and time ranges when the ad extension is eligible to be shown in ads.<br/><br/>**Add:** Optional<br/>**Update:** Optional. If you set this element null, any existing scheduling set for the ad extension will remain unchanged. If you set this to any non-null [Schedule](../campaign-api/schedule-data-object.md) object, you are effectively replacing existing scheduling settings for the ad extension. To remove all scheduling set this element to an empty [Schedule](../campaign-api/schedule-data-object.md) object.|[Schedule](../campaign-api/schedule-data-object.md)|
|*Status*|The status of the ad extension. The value will always be *Active* because the Campaign Management service does not return deleted ad extensions.<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|[AdExtensionStatus](../campaign-api/adextensionstatus-value-set.md)|
|*Type*|The type of the ad extension. This value is *CallAdExtension* when you retrieve a call ad extension. <br/><br/>**Add:** Read-only<br/>**Update:** Read-only<br/><br/>For more information about ad extension types, see the [Ad Extension Data Object Remarks](../campaign-api/adextension-data-object.md#remarks).|*string*|
|*Version*|The number of times the contents of the ad extension has been updated. The version is set to 1 when you add the extension and is incremented each time it’s revised.<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|*int*|


## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[AdExtensionAssociation](../campaign-api/adextensionassociation-data-object.md)  
[AddAdExtensions](../campaign-api/addadextensions-service-operation.md)  
[GetAdExtensionsByIds](../campaign-api/getadextensionsbyids-service-operation.md)  
[UpdateAdExtensions](../campaign-api/updateadextensions-service-operation.md)  


---
title: "CalloutAdExtension Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 68a1f34b-e9d6-47a5-a91e-0f522008f5b1
caps.latest.revision: 18
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# CalloutAdExtension Data Object
Defines an object that specifies additional text about your business, products, or services to include in a text ad.

You can associate a callout ad extension with one or more campaigns and ad groups. Each campaign or ad group can be associated with between 2 and 20 callout ad extensions. If you associate one or fewer callout extensions with your campaign or ad group, no callout text will serve with your ad. A text ad may include between 2 to 4 callouts per impression. 

Ad extensions that are associated at the ad group level will override ad extensions of the same type that are associated at the campaign level. For example if you have 2 callout extensions set for *Campaign A*, zero callout extensions associated with *Ad Group AA*, and one callout extension associated with *Ad Group AB*, then only *Ad Group AA* is eligible to have its text ads decorated with callouts.

## Syntax

```xml
<xs:complexType name="CalloutAdExtension">
  <xs:complexContent mixed="false">
    <xs:extension base="tns:AdExtension">
      <xs:sequence>
        <xs:element name="Text" type="xs:string" nillable="true"/> 
      </xs:sequence>
    </xs:extension>
  </xs:complexContent>
</xs:complexType>
```

## <a name="Elements"></a>Elements
The *CalloutAdExtension* object inherits elements from the [AdExtension](../campaign-api/adextension-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#inheritedelements) below.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Text*|Additional callout text about your business, products, or services to include in a text ad. The callout extension text must be different than the text of your ad.<br/><br/>The length of this string must be between 1 and 25 characters. Note that for Traditional Chinese characters, the length of this string must be between 1 and 12 characters.<br/><br/>**Add:** Required<br/>**Update:** Required|*string*|

## <a name="InheritedElements"></a>Inherited Elements
The *CalloutAdExtension* object inherits the following elements from the [AdExtension](../campaign-api/adextension-data-object.md) object. 

> [!NOTE]
> The descriptions below are specific to callout ad extensions, and might not apply to other objects that inherit the same elements from the [AdExtension](../campaign-api/adextension-data-object.md) object.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*DevicePreference*|Reserved for future use.|*long*|
|*ForwardCompatibilityMap*|The list of key and value strings for forward compatibility. This element can be used to avoid otherwise breaking changes when new elements are added in future releases.<br /><br />There are currently no forward compatibility changes for the *AdExtension* object.<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|*KeyValuePairOfstringstring* array|
|*Id*|The unique Bing Ads identifier of the ad extension.<br/><br/>**Add:** Read-only and Required<br/>**Update:** Read-only|*long*|
|*Scheduling*|Determines the calendar day and time ranges when the ad extension is eligible to be shown in ads.<br/><br/>**Add:** Optional<br/>**Update:** Optional. If you set this element null, any existing scheduling set for the ad extension will remain unchanged. If you set this to any non-null [Schedule](../campaign-api/schedule-data-object.md) object, you are effectively replacing existing scheduling settings for the ad extension. To remove all scheduling set this element to an empty [Schedule](../campaign-api/schedule-data-object.md) object.|[Schedule](../campaign-api/schedule-data-object.md)|
|*Status*|The status of the ad extension. The value will always be *Active* because the Campaign Management service does not return deleted ad extensions.<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|[AdExtensionStatus](../campaign-api/adextensionstatus-value-set.md)|
|*Type*|The type of the ad extension. This value is *CalloutAdExtension* when you retrieve a callout ad extension. <br/><br/>**Add:** Read-only<br/>**Update:** Read-only<br/><br/>For more information about ad extension types, see the [Ad Extension Data Object Remarks](../campaign-api/adextension-data-object.md#remarks).|*string*|
|*Version*|The number of times the contents of the ad extension has been updated. The version is set to 1 when you add the extension and is incremented each time it's revised.<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|*int*|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[AdExtensionAssociation](../campaign-api/adextensionassociation-data-object.md)  
[AddAdExtensions](../campaign-api/addadextensions-service-operation.md)  
[GetAdExtensionsByIds](../campaign-api/getadextensionsbyids-service-operation.md)  
[UpdateAdExtensions](../campaign-api/updateadextensions-service-operation.md)  

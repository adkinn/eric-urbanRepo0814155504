---
title: "ReviewAdExtension Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 412d15bb-0f5b-4216-89d8-72435f80187b
caps.latest.revision: 21
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# ReviewAdExtension Data Object
Defines an object that specifies third-party reviews (exact or paraphrased) about your business, products, or services to include in a text ad.

You can associate a review ad extension with one or more campaigns and ad groups. Each campaign or ad group can be associated with between 1 and 20 review ad extensions. A text ad will only include one review per impression.

## Syntax

```xml
\<xs:complexType name="ReviewAdExtension">
  \<xs:complexContent mixed="false">
    \<xs:extension base="tns:AdExtension">
      \<xs:sequence>
        \<xs:element name="IsExact" type="xs:boolean" minOccurs="0"/>
        \<xs:element name="Source" type="xs:string" nillable="true" minOccurs="0"/> 
        \<xs:element name="Text" type="xs:string" nillable="true" minOccurs="0"/> 
        \<xs:element name="Url" type="xs:string" nillable="true" minOccurs="0"/>  
      \</xs:sequence>
    \</xs:extension>
  \</xs:complexContent>
\</xs:complexType>
```

## <a name="Elements"></a>Elements
The *ReviewAdExtension* object inherits elements from the [AdExtension](../campaign-api/adextension-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#InheritedElements) below.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*IsExact*|Determines whether the review text is an exact quote or paraphrased. <br/><br/>If not specified, the default value of false indicates that the review text is paraphrased from the source. If set to *True*, the review text will be surrounded automatically with quotation marks when displayed with the ad.<br/><br/>**Add:** Optional<br/>**Update:** Optional|*boolean*|
|*Source*|The review source name.<br/><br/>The combined length of the *Source* and *Text* strings must not exceed 67 characters. Note that for Traditional Chinese characters, the combined length of the Source and Text *Source* and *Text* strings is limited to 33 characters.<br/><br/>**Add:** Required<br/>**Update:** Optional|*string*|
|*Text*|The text that is either a paraphrase or an exact quote from the review source.<br/><br/>The combined length of the *Source* and *Text* strings must not exceed 67 characters. Note that for Traditional Chinese characters, the combined length of the Source and Text *Source* and *Text* strings is limited to 33 characters.<br/><br/>**Note:** Do not surround the text with quotation marks. If *IsExact* is set to *True*, the review text will be surrounded automatically with quotation marks when displayed with the ad.<br/><br/>**Add:** Required<br/>**Update:** Optional|*string*|
|*Url*|The review source Url.<br/><br/>The Url must begin with either the *http://* or *https://* prefix.<br/><br/>The length of this string is limited to 2,048 characters.<br/><br/>**Add:** Required<br/>**Update:** Optional|*string*|

## <a name="InheritedElements"></a>Inherited Elements
The *ReviewAdExtension* object inherits the following elements from the [AdExtension](../campaign-api/adextension-data-object.md) object. 

> [!NOTE]
> The descriptions below are specific to review ad extensions, and might not apply to other objects that inherit the same elements from the [AdExtension](../campaign-api/adextension-data-object.md) object.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*DevicePreference*|Reserved for future use.|*long*|
|*ForwardCompatibilityMap*|The list of key and value strings for forward compatibility. This element can be used to avoid otherwise breaking changes when new elements are added in future releases.<br /><br />There are currently no forward compatibility changes for the *AdExtension* object.<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|*KeyValuePairOfstringstring* array|
|*Id*|The unique Bing Ads identifier of the ad extension.<br/><br/>**Add:** Read-only and Required<br/>**Update:** Read-only|*long*|
|*Scheduling*|Determines the calendar day and time ranges when the ad extension is eligible to be shown in ads.<br/><br/>**Add:** Optional<br/>**Update:** Optional. If you set this element null, any existing scheduling set for the ad extension will remain unchanged. If you set this to any non-null [Schedule](../campaign-api/schedule-data-object.md) object, you are effectively replacing existing scheduling settings for the ad extension. To remove all scheduling set this element to an empty [Schedule](../campaign-api/schedule-data-object.md) object.|[Schedule](../campaign-api/schedule-data-object.md)|
|*Status*|The status of the ad extension. The value will always be *Active* because the Campaign Management service does not return deleted ad extensions.<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|[AdExtensionStatus](../campaign-api/adextensionstatus-value-set.md)|
|*Type*|The type of the ad extension. This value is *ReviewAdExtension* when you retrieve a review ad extension. <br/><br/>**Add:** Read-only<br/>**Update:** Read-only<br/><br/>For more information about ad extension types, see the [Ad Extension Data Object Remarks](../campaign-api/adextension-data-object.md#remarks).|*string*|
|*Version*|The number of times the contents of the ad extension has been updated. The version is set to 1 when you add the extension and is incremented each time it’s revised.<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|*int*|


## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[AdExtension](../campaign-api/adextension-data-object.md)  
[AddAdExtensions](../campaign-api/addadextensions-service-operation.md)  
[GetAdExtensionsByIds](../campaign-api/getadextensionsbyids-service-operation.md)  
[UpdateAdExtensions](../campaign-api/updateadextensions-service-operation.md)  

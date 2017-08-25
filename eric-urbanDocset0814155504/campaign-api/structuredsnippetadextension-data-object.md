---
title: "StructuredSnippetAdExtension Data Object"
ms.custom: ""
ms.date: "08/15/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5cb34c72-dd73-42b5-aa0b-5bf20f7272b1
caps.latest.revision: 13
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# StructuredSnippetAdExtension Data Object
Defines an object that pairs one header with between 3 and 10 snippet values that tell customers more about your business.

In the following example, *Courses* is the header, and *.NET*, *Java*, *Python*, and *PHP* are examples of individual values.

**Courses: .NET, Java, Python, PHP**

You can associate a structured snippet ad extension with one or more campaigns and ad groups. Each campaign or ad group can be associated with between 1 and 20 structured snippet ad extensions. A text ad will only include one structured snippet (one headline with 3 - 10 values) per impression.

## Syntax

```xml
<xs:complexType name="StructuredSnippetAdExtension">
  <xs:complexContent mixed="false">
    <xs:extension base="tns:AdExtension">
      <xs:sequence>
        <xs:element name="Header" type="xs:string" nillable="true"/>
        <xs:element name="Values" type="q66:ArrayOfstring" nillable="true" xmlns:q66="http://schemas.microsoft.com/2003/10/Serialization/Arrays"/> 
      </xs:sequence>
    </xs:extension>
  </xs:complexContent>
</xs:complexType>
```

## <a name="Elements"></a>Elements
The *StructuredSnippetAdExtension* object inherits elements from the [AdExtension](../campaign-api/adextension-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#inheritedelements) below.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Header*|The header that is appended with a colon (*:*) and precedes the snippet values. <br/><br/>Structured Snippet headers must be specified in the same language that you intend it to be shown. For example, if you want header *Amenities* in English you must specify the header as *Amenities*.  If you want header *Ausstattung* in German you must specify the header as *Ausstattung* (*Amenities* in German). For a list of supported headers per language, please see [Structured Snippet Header Languages](~/concepts/ad-languages.md#structuredsnippetheaders).<br/><br/>**Add:** Required<br/>**Update:** Required|*string*|
|*Values*|The snippet values that follow after the *Header:* component. You can choose the values, and each value can have a maximum length of 25 characters. Note that for Traditional Chinese characters, each value can have a maximum length of 12 characters.<br/><br/>**Add:** Required<br/>**Update:** Required|*string* array|

## <a name="InheritedElements"></a>Inherited Elements
The *StructuredSnippetAdExtension* object inherits the following elements from the [AdExtension](../campaign-api/adextension-data-object.md) object. 

> [!NOTE]
> The descriptions below are specific to structured snippet ad extensions, and might not apply to other objects that inherit the same elements from the [AdExtension](../campaign-api/adextension-data-object.md) object.


|Element|Description|Data Type|
|-----------|---------------|-------------|
|*DevicePreference*|Reserved for future use.|*long*|
|*ForwardCompatibilityMap*|The list of key and value strings for forward compatibility. This element can be used to avoid otherwise breaking changes when new elements are added in future releases.<br /><br />There are currently no forward compatibility changes for the *AdExtension* object.<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|*KeyValuePairOfstringstring* array|
|*Id*|The unique Bing Ads identifier of the ad extension.<br/><br/>**Add:** Read-only and Required<br/>**Update:** Read-only|*long*|
|*Scheduling*|Determines the calendar day and time ranges when the ad extension is eligible to be shown in ads.<br/><br/>**Add:** Optional<br/>**Update:** Optional. If you set this element null, any existing scheduling set for the ad extension will remain unchanged. If you set this to any non-null [Schedule](../campaign-api/schedule-data-object.md) object, you are effectively replacing existing scheduling settings for the ad extension. To remove all scheduling set this element to an empty [Schedule](../campaign-api/schedule-data-object.md) object.|[Schedule](../campaign-api/schedule-data-object.md)|
|*Status*|The status of the ad extension. The value will always be *Active* because the Campaign Management service does not return deleted ad extensions.<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|[AdExtensionStatus](../campaign-api/adextensionstatus-value-set.md)|
|*Type*|The type of the ad extension. This value is *StructuredSnippetAdExtension* when you retrieve a structured snippet ad extension.<br/><br/>**Add:** Read-only<br/>**Update:** Read-only<br/><br/>For more information about ad extension types, see the [Ad Extension Data Object Remarks](../campaign-api/adextension-data-object.md#remarks).|*string*|
|*Version*|The number of times the contents of the ad extension has been updated. The version is set to 1 when you add the extension and is incremented each time it?s revised.<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|*int*|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[AdExtensionAssociation](../campaign-api/adextensionassociation-data-object.md)  
[AddAdExtensions](../campaign-api/addadextensions-service-operation.md)  
[GetAdExtensionsByIds](../campaign-api/getadextensionsbyids-service-operation.md)  
[UpdateAdExtensions](../campaign-api/updateadextensions-service-operation.md)  

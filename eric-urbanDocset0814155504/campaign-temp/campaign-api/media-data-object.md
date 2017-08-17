---
title: "Media Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3730b065-feaa-4795-9adc-74dff57f6f82
caps.latest.revision: 10
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Media Data Object
Defines the base object of media.

Do not try to instantiate a *Media*. You can create the following object that derives from it.
-   [Image](../campaign-api/image-data-object.md)  

## Syntax

```xml
\<xs:complexType name="Media">
  \<xs:sequence>
    \<xs:element minOccurs="0" name="Id" nillable="true" type="xs:long" />
    \<xs:element minOccurs="0" name="MediaType" nillable="true" type="xs:string" />
    \<xs:element name="Type" nillable="true" type="xs:string" />
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Id*|The unique Bing Ads identifier of the media.<br/><br/>**Add:** Read-only|*long*|
|*MediaType*|The media type. For more information about media types, see [Remarks](#remarks) below.<br/><br/>**Add:** Read-only|*string*|
|*Type*|The type of media to add to the media library.<br /><br />For media that will be used with a [LocationAdExtension](../campaign-api/locationadextension-data-object.md), the supported values are *Icon* and *Image*.<br /><br />For media that will be used with an [ImageAdExtension](../campaign-api/imageadextension-data-object.md), the supported values are *Image16x9*, *Image15x10*, *Image4x3*, and *Image12x10*.<br /><br />For more information about supported aspect ratios, see the [Image Data Object](../campaign-api/image-data-object.md#imagedata).<br/><br/>**Add:** Required|*string*|

## <a name="remarks"></a>Remarks
For Java and the .NET languages, do not set the *MediaType* element because the value is determined when you instantiate an image.

If you generate the SOAP manually, use the *type* attribute of the `<Media>` node as shown in the following example, to specify that the media is an image.

> [!NOTE]
> Images and icons are both created as [Image](../campaign-api/image-data-object.md) objects. 

```xml
\<Media xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
  \<Media i:type="Image">
    \<Id i:nil="true" />
    <MediaType>Image</MediaType>
    <Type>Icon</Type>
    <Data>IconDataGoesHere</Data>
  </Media>
  \<Media i:type="Image">
    \<Id i:nil="true" />
    <MediaType>Image</MediaType>
    <Type>Image15x10</Type>
    <Data>ImageDataGoesHere</Data>
  </Media>
</Media>
```

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[AddMedia](../campaign-api/addmedia-service-operation.md)  
[GetMediaByIds](../campaign-api/getmediabyids-service-operation.md)  


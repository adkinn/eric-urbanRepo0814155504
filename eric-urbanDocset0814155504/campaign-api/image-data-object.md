---
title: "Image Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 51b291a2-d8db-466c-a511-6a4e9247e223
caps.latest.revision: 8
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Image Data Object
Defines an image object that can be added to an account’s media library.

The *Image* object derives from the *Media* object. For a list of the inherited elements, see the [Media](../campaign-api/media-data-object.md) object.

## Syntax

```xml
<xs:complexType name="Image">
  <xs:complexContent mixed="false">
    <xs:extension base="tns:Media">
      <xs:sequence>
        <xs:element name="Data" nillable="true" type="xs:string" />
      </xs:sequence>
    </xs:extension>
  </xs:complexContent>
</xs:complexType>
```

## <a name="Elements"></a>Elements
The *Image* object derives from the [Media](../campaign-api/media-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#InheritedElements) below.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Data*|A base64 string that represents the image or icon to add to the library. The base64 string can contain a maximum of 102,400 characters.<br /><br />For information about restrictions and supported data types, see [Image Data](#imagedata) below.|*string*|
  
## <a name="InheritedElements"></a>Inherited Elements
The *Image* object derives from the [Media](../campaign-api/media-data-object.md) object, and inherits the following elements. 

> [!NOTE]
> The descriptions below are specific to image media, and might not apply to other objects that inherit the same elements from the [Media](../campaign-api/media-data-object.md) object.

|Element|Description|Data Type|Add|
|-----------|---------------|-------------|-------|
|*Id*|The unique Bing Ads identifier of the media.|*long*|Read-only|
|*MediaType*|The media type. For more information about media types, see the [Media Data Object Remarks](../campaign-api/media-data-object.md#remarks).|*string*|Read-only|
|*Type*|The type of media to add to the library.<br /><br />For media that will be used with a [LocationAdExtension](../campaign-api/locationadextension-data-object.md), the supported values are *Icon* and *Image*.<br /><br />For media that will be used with an [ImageAdExtension](../campaign-api/imageadextension-data-object.md), the supported values are *Image16x9*, *Image15x10*, *Image4x3*, and *Image12x10*.<br /><br />For more information about supported aspect ratios, see the [Image Data](#imagedata) section below.|*string*|Required|


## <a name="imagedata"></a>Image Data
The following MIME types are supported for the *Data* element of the *Image* data object.
-   GIF  
-   JPEG  
-   PNG  

Images with animation are not supported.

The following restrictions apply to [Media](../campaign-api/media-data-object.md) that will be used with a [LocationAdExtension](../campaign-api/locationadextension-data-object.md).

-   If the value of the *Type* element is *Icon*, the maximum supported icon size is 26X26.  
-   If the value of the *Type* element is *Image*, the maximum supported image size is 125X125.  


The following restrictions apply to [Media](../campaign-api/media-data-object.md) types (aspect ratios) that will be used with an [ImageAdExtension](../campaign-api/imageadextension-data-object.md).

|Type|Aspect Ratio|Minimum Dimension|Maximum Dimension|
|--------|----------------|---------------------|---------------------|
|*Image16x9*|16:9|640 width x 360 height, in pixels|1778 width x 1000 height, in pixels|
|*Image15x10*|1.5:1|300 width x 200 height, in pixels|1500 width x 1000 height, in pixels|
|*Image4x3*|4:3|100 width x 75 height, in pixels|1333 width x 1000 height, in pixels|
|*Image12x10*|1.2:1|300 width x 250 height, in pixels|1200 width x 1000 height, in pixels|
> [!NOTE]
> The maximum file size is 5 MB, but the recommended maximum file size is 1MB.

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[AddMedia](../campaign-api/addmedia-service-operation.md)  
[GetMediaByIds](../campaign-api/getmediabyids-service-operation.md)  
[GetMediaMetaDataByIds](../campaign-api/getmediametadatabyids-service-operation.md)  


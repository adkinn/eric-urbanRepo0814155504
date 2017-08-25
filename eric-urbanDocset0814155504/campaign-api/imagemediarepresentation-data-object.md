---
title: "ImageMediaRepresentation Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 238c765c-f0f2-4e6c-8973-577c9a72028e
caps.latest.revision: 9
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# ImageMediaRepresentation Data Object
Defines an image media representation with height and width.

## Syntax

```xml
<xs:complexType name="ImageMediaRepresentation">
  <xs:complexContent mixed="false">
    <xs:extension base="tns:MediaRepresentation">
      <xs:sequence>
        <xs:element type="xs:int" name="Height" minOccurs="0"/>
        <xs:element type="xs:int" name="Width" minOccurs="0"/>
      </xs:sequence>
    </xs:extension>
  </xs:complexContent>
</xs:complexType>
```

## <a name="Elements"></a>Elements
The *ImageMediaRepresentation* object derives from the [MediaRepresentation](../campaign-api/mediarepresentation-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#inheritedelements) below.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Height*|The height of the image in pixels. For more information, see [Remarks](#remarks) below.|*int*|
|*Width*|The width of the image in pixels. For more information, see [Remarks](#remarks) below.|*int*|

## <a name="InheritedElements"></a>Inherited Elements
The *ImageMediaRepresentation* object derives from the [MediaRepresentation](../campaign-api/mediarepresentation-data-object.md) object, and inherits the following elements. 

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Name*|The name of the media representation.<br /><br />For [ImageMediaRepresentation](../campaign-api/imagemediarepresentation-data-object.md), the possible values are *Preview*, *Thumbnail*, and *Original*.|*string*|
|*Type*|The type of the media representation. This value is *ImageMediaRepresentation* when you retrieve a image media representation. |*string*|
|*Url*|The media download URL.|*string*|

## <a name="remarks"></a>Remarks
[!INCLUDE[brand](../campaign-api/includes/brand.md)] stores three representations for each image media of varying height and width.

|Description|Width|Height|
|---------------|---------|----------|
|Thumbnail|120|68|
|Preview|160|90|
|Original size that you uploaded using the [AddMedia](../campaign-api/addmedia-service-operation.md) service operation.|For dimension restrictions, please see [Image](../campaign-api/image-data-object.md).|For dimension restrictions, please see [Image](../campaign-api/image-data-object.md).|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[GetMediaMetaDataByAccountId](../campaign-api/getmediametadatabyaccountid-service-operation.md)  
[GetMediaMetaDataByIds](../campaign-api/getmediametadatabyids-service-operation.md)  
[MediaMetaData](../campaign-api/mediametadata-data-object.md)  


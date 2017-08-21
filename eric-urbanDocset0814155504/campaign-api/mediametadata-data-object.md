---
title: "MediaMetaData Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fa4f2234-dbff-461d-ac31-f30521f1b4d0
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# MediaMetaData Data Object
Defines a media meta data object. The meta data includes download Urls for one or more media representations.

## Syntax

```xml
<xs:complexType name="MediaMetaData">
  <xs:sequence>
    <xs:element type="xs:long" name="Id"  minOccurs="0" />
    <xs:element type="xs:string" name="MediaType" minOccurs="0" nillable="true"/>
    <xs:element type="tns:ArrayOfMediaRepresentation" name="Representations" minOccurs="0" nillable="true"/>
    <xs:element type="xs:string" name="Type" minOccurs="0" nillable="true"/>
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Id*|The system identifier of the media meta data.|*long*|
|*MediaType*|The name of the media subclass.<br /><br />For an [ImageMediaRepresentation](../campaign-api/imagemediarepresentation-data-object.md), the *MediaType* is *Image*.|*string*|
|*Representations*|An array of *MediaRepresentation*-derived objects, for example [ImageMediaRepresentation](../campaign-api/imagemediarepresentation-data-object.md), that each include download Urls for one or more media representations. The number of representations depends on the type of media. For example media for image ad extensions  have multiple height and width representations, and you can access each individually. For more information see [MediaEnabledEntityFilter](../campaign-api/mediaenabledentityfilter-value-set.md).|[MediaRepresentation](../campaign-api/mediarepresentation-data-object.md) array|
|*Type*|The type of media in the library.<br /><br />For an [ImageMediaRepresentation](../campaign-api/imagemediarepresentation-data-object.md),  the only possible value is *Image*.|*string*|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[GetMediaMetaDataByAccountId](../campaign-api/getmediametadatabyaccountid-service-operation.md)  
[GetMediaMetaDataByIds](../campaign-api/getmediametadatabyids-service-operation.md)  


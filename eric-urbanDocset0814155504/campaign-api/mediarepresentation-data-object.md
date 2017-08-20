---
title: "MediaRepresentation Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5a5715f1-8c39-4c71-b112-d4d9e7b0e96e
caps.latest.revision: 9
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# MediaRepresentation Data Object
Defines a media representation base class that includes a  media download Url.

Do not try to instantiate a *MediaRepresentation*. You can create the [ImageMediaRepresentation](../campaign-api/imagemediarepresentation-data-object.md) object that derives from it. 

## Syntax

```xml
<xs:complexType name="MediaRepresentation">
  <xs:sequence>
    <xs:element type="xs:string" name="Name" minOccurs="0" nillable="true"/>
    <xs:element type="xs:string" name="Type" minOccurs="0" nillable="true"/>
    <xs:element type="xs:string" name="Url" minOccurs="0" nillable="true"/>
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Name*|The name of the media representation.|*string*|
|*Type*|The type of the media representation.|*string*|
|*Url*|The media download URL.|*string*|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[GetMediaMetaDataByAccountId](../campaign-api/getmediametadatabyaccountid-service-operation.md)  
[GetMediaMetaDataByIds](../campaign-api/getmediametadatabyids-service-operation.md)  
[MediaMetaData](../campaign-api/mediametadata-data-object.md)  


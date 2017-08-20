---
title: "MediaAssociation Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 834194ec-8871-41f7-a547-881a3920ad56
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# MediaAssociation Data Object
Defines an object that represents the identified media and an associated entity, for example media associated with an ad group.

You can get this object by calling [GetMediaAssociations](../campaign-api/getmediaassociations-service-operation.md), and then use the media identifier with [GetMediaMetaDataByIds](../campaign-api/getmediametadatabyids-service-operation.md), for example.

## Syntax

```xml
<xs:complexType name="MediaAssociation">
  <xs:sequence>
    <xs:element type="xs:long" name="EntityId" minOccurs="0"/>
    <xs:element type="tns:MediaEnabledEntityFilter" name="MediaEnabledEntity" minOccurs="0"/>
    <xs:element type="xs:long" name="MediaId" minOccurs="0"/>
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*EntityId*|The system identifier of the media enabled entity, for example the identifier of an ImageAdExtension.|*long*|
|*MediaEnabledEntity*|Determines the type of media to get. Currently only ImageAdExtension is supported.|[MediaEnabledEntityFilter](../campaign-api/mediaenabledentityfilter-value-set.md)|
|*MediaId*|The system identifier of the media.|*long*|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[GetMediaAssociations](../campaign-api/getmediaassociations-service-operation.md)  
[GetMediaMetaDataByIds](../campaign-api/getmediametadatabyids-service-operation.md)  


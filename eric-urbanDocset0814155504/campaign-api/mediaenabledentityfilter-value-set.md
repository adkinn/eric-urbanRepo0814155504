---
title: "MediaEnabledEntityFilter Value Set"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7a13bb78-7238-457c-92b3-7294630df5b2
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# MediaEnabledEntityFilter Value Set
Defines the possible values representing entities that are enabled for media such as images.

## Syntax

```xml
<xs:simpleType name="MediaEnabledEntityFilter">
  <xs:list>
    <xs:simpleType>
      <xs:restriction base="xs:string">
        <xs:enumeration value="ImageAdExtension" />
      </xs:restriction>
    </xs:simpleType>
  </xs:list>
</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|ImageAdExtension|The media enabled entity is an [ImageAdExtension](../campaign-api/imageadextension-data-object.md).<br /><br />When you call [GetMediaMetaDataByAccountId](../campaign-api/getmediametadatabyaccountid-service-operation.md) or [GetMediaMetaDataByIds](../campaign-api/getmediametadatabyids-service-operation.md), the service will return exactly three [ImageMediaRepresentation](../campaign-api/imagemediarepresentation-data-object.md) objects with varying height and width properties.|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[ImageAdExtension](../campaign-api/imageadextension-data-object.md)


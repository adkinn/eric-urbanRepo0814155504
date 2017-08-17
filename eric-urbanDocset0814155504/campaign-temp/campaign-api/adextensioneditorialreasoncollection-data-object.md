---
title: "AdExtensionEditorialReasonCollection Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 67927f65-2942-400b-b7d9-a4fb5981cfff
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AdExtensionEditorialReasonCollection Data Object
Defines a collection of ad extensions that failed editorial review.

## Syntax

```xml
\<xs:complexType name="AdExtensionEditorialReasonCollection">
  \<xs:sequence>
    \<xs:element minOccurs="0" name="AdExtensionId" type="xs:long" />
    \<xs:element minOccurs="0" name="Reasons" nillable="true" type="tns:ArrayOfAdExtensionEditorialReason" />
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AdExtensionId*|The identifier of the ad extension that failed editorial review.|*long*|
|*Reasons*|A list of *AdExtensionEditorialReason* objects that identify the component of an ad extension that failed editorial review, and the reason for the failure.|[AdExtensionEditorialReason](../campaign-api/adextensioneditorialreason-data-object.md) array|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[GetAdExtensionsEditorialReasons](../campaign-api/getadextensionseditorialreasons-service-operation.md)


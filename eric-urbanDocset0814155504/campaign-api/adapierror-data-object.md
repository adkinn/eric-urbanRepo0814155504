---
title: "AdApiError Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 34ddc5f2-f945-4a22-8c59-5a20a7d52dfb
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AdApiError Data Object
Defines an error object that contains the details that explain why the service operation failed.

## Syntax

```xml
<xs:complexType name="AdApiError">
  <xs:sequence>
    <xs:element minOccurs="0" name="Code" type="xs:int" />
    <xs:element minOccurs="0" name="Detail" nillable="true" type="xs:string" />
    <xs:element minOccurs="0" name="ErrorCode" nillable="true" type="xs:string" />
    <xs:element minOccurs="0" name="Message" nillable="true" type="xs:string" />
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Code*|A numeric error code that identifies the error.|*int*|
|*Detail*|A message that contains additional details about the error. This string can be empty.|*string*|
|*ErrorCode*|A symbolic string constant that identifies the error. For example, UserIsNotAuthorized.|*string*|
|*Message*|A message that describes the error.|*string*|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[AdApiFaultDetail](../campaign-api/adapifaultdetail-data-object.md)


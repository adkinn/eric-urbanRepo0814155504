---
title: "OperationError Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cac8461d-eea4-48c0-9ef9-a74e5acb3ad0
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# OperationError Data Object
Defines an error object that contains the details that explain why the service operation failed.

## Syntax

```xml
<xs:complexType name="OperationError">
  <xs:sequence>
    <xs:element minOccurs="0" name="Code" type="xs:int" />
    <xs:element minOccurs="0" name="Details" nillable="true" type="xs:string" />
    <xs:element minOccurs="0" name="ErrorCode" nillable="true" type="xs:string" />
    <xs:element minOccurs="0" name="Message" nillable="true" type="xs:string" />
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Code*|A numeric error code that identifies the error|*int*|
|*Details*|A message that provides additional details about the error. This string can be empty.|*string*|
|*ErrorCode*|A symbolic string constant that identifies the error. For example, UserIsNotAuthorized.|*string*|
|*Message*|A message that describes the error.|*string*|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[ApiFaultDetail](../campaign-api/apifaultdetail-data-object.md)  
[EditorialApiFaultDetail](../campaign-api/editorialapifaultdetail-data-object.md)  


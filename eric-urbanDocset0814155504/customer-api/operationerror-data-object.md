---
title: "OperationError Data Object"
ms.custom: ""
ms.date: "04/03/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7cad7cf5-9fe8-404f-928a-c4325f648f00
caps.latest.revision: 4
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
    <xs:element minOccurs="0" name="Message" nillable="true" type="xs:string" />
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Code*|A numeric error code that identifies the error|*int*|
|*Details*|A message that provides additional details about the error. This string can be empty.|*string*|
|*Message*|A message that describes the error.|*string*|

## Requirements
[!INCLUDE[reqcus](../customer-api/includes/reqcus.md)]
## See Also
[Handling Service Errors and Exceptions](~/concepts/handling-service-errors-and-exceptions.md)


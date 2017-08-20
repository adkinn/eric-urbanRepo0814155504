---
title: "CustomerInfo Data Object"
ms.custom: ""
ms.date: "08/01/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 379a1668-70b3-433d-a2f6-ef0888f90011
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# CustomerInfo Data Object
Defines a customer identification object that contains information that identifies a customer.

## Syntax

```xml
<xs:complexType name="CustomerInfo">
  <xs:sequence>
    <xs:element minOccurs="0" name="Id" type="xs:long" />
    <xs:element minOccurs="0" name="Name" nillable="true" type="xsd:string" />
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Id*|The system generated identifier of the customer.|*long*|
|*Name*|The name of the customer.|*string*|

## Requirements
[!INCLUDE[reqcus](../customer-api/includes/reqcus.md)]
## See Also
[Customer](../customer-api/customer-data-object.md)


---
title: "UserInfo Data Object"
ms.custom: ""
ms.date: "04/03/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f25618b9-e2b4-4bb8-8cc0-b1e654852d8b
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# UserInfo Data Object
Defines a user identification object that contains information that identifies a user.

## Syntax

```xml
\<xs:complexType name="UserInfo">
  \<xs:sequence>
    \<xs:element minOccurs="0" name="Id" type="xs:long" />
    \<xs:element minOccurs="0" name="UserName" nillable="true" type="xsd:string" />
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Id*|The system generated identifier of the user.|*long*|
|*UserName*|The logon user name of the user.|*string*|

## Requirements
[!INCLUDE[reqcus](../customer-api/includes/reqcus.md)]
## See Also
[User](../customer-api/user-data-object.md)


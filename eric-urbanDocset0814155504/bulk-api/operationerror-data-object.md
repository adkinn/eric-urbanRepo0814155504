---
title: "OperationError Data Object"
ms.custom: ""
ms.date: "07/10/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5d54199c-4e73-4026-91ed-8b8126f65f17
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# OperationError Data Object
Defines an error object that contains the details that explain why the service operation failed.

## Syntax

```xml
\<xs:complexType name="OperationError">
  \<xs:sequence>
    \<xs:element minOccurs="0" name="Code" type="xs:int" />
    \<xs:element minOccurs="0" name="Details" nillable="true" type="xs:string" />
    \<xs:element minOccurs="0" name="ErrorCode" nillable="true" type="xs:string" />
    \<xs:element minOccurs="0" name="Message" nillable="true" type="xs:string" />
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|`Code`|A numeric error code that identifies the error|`int`|
|`Details`|A message that provides additional details about the error. This string can be empty.|`string`|
|`ErrorCode`|A symbolic string constant that identifies the error. For example, *UserIsNotAuthorized*.|`string`|
|`Message`|A message that describes the error.|`string`|

## Requirements
[!INCLUDE[reqbulk](../bulk-api/includes/reqbulk.md)]
## See Also
[ApiFaultDetail Data Object](../bulk-api/apifaultdetail-data-object.md)


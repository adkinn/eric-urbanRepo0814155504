---
title: "OperationError Data Object"
ms.custom: ""
ms.date: "06/07/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 62a0b20c-5375-443c-b091-c6fe110b78b6
caps.latest.revision: 7
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
|*ErrorCode*|A symbolic string constant that identifies the error. For example, *UserIsNotAuthorized*.|*string*|
|*Message*|A message that describes the error.|*string*|

## Requirements
[!INCLUDE[reqadint](../adinsight-api/includes/reqadint.md)]
## See Also
[ApiFaultDetail](../adinsight-api/apifaultdetail-data-object.md)  
[Handling Service Errors and Exceptions](https://msdn.microsoft.com/library/bing-ads-error-handling-guide.aspx)  


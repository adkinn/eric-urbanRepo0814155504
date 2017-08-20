---
title: "BatchError Data Object"
ms.custom: ""
ms.date: "06/07/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: df2f8836-5d59-4db4-ac6c-b3ef49677d54
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# BatchError Data Object
Defines an error object that identifies the item within the batch of items in the request message that caused the operation to fail, and describes the reason for the failure.

## Syntax

```xml
\<xs:complexType name="BatchError">
  \<xs:sequence>
    \<xs:element minOccurs="0" name="Code" type="xs:int" />
    \<xs:element minOccurs="0" name="Details" nillable="true" type="xs:string" />
    \<xs:element minOccurs="0" name="ErrorCode" nillable="true" type="xs:string" />
    \<xs:element minOccurs="0" name="Index" type="xs:int" />
    \<xs:element minOccurs="0" name="Message" nillable="true" type="xs:string" />
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Code*|A numeric error code that identifies the error.|*int*|
|*Details*|A message that provides additional details about the batch error. This string can be empty.|*string*|
|*ErrorCode*|A symbolic string constant that identifies the error. For example, *UserIsNotAuthorized*.|*string*|
|*Index*|The zero-based index of the item in the batch of items in the request message that failed.|*int*|
|*Message*|A message that describes the error.|*string*|

## Requirements
[!INCLUDE[reqadint](../adinsight-api/includes/reqadint.md)]
## See Also
[ApiFaultDetail](../adinsight-api/apifaultdetail-data-object.md)  
[Handling Service Errors and Exceptions](https://msdn.microsoft.com/library/bing-ads-error-handling-guide.aspx)  


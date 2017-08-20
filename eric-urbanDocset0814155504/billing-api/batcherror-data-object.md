---
title: "BatchError Data Object"
ms.custom: ""
ms.date: "04/03/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1a66aadb-a047-442f-890a-935d754f300e
caps.latest.revision: 4
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
|*Index*|The zero-based index of the item in the batch of items in the request message that failed.|*int*|
|*Message*|A message that describes the error.|*string*|

## Requirements
[!INCLUDE[reqbilling](../billing-api/includes/reqbilling.md)]
## See Also
[Handling Service Errors and Exceptions](https://msdn.microsoft.com/library/bing-ads-error-handling-guide.aspx)


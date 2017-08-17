---
title: "BatchError Data Object"
ms.custom: ""
ms.date: "07/10/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ced198be-c33b-4ea8-81d5-13bcdba73cbb
caps.latest.revision: 5
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
    \<xs:element minOccurs="0" name="FieldPath" nillable="true" type="xs:string"/>
    \<xs:element xmlns:q9="http://schemas.datacontract.org/2004/07/System.Collections.Generic" minOccurs="0" name="ForwardCompatibilityMap" nillable="true" type="q9:ArrayOfKeyValuePairOfstringstring"/>
    \<xs:element minOccurs="0" name="Index" type="xs:int" />
    \<xs:element minOccurs="0" name="Message" nillable="true" type="xs:string" />
    \<xs:element minOccurs="0" name="Type" nillable="true" type="xs:string" />
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|`Code`|A numeric error code that identifies the error.|`int`|
|`Details`|A message that provides additional details about the batch error. This string can be empty.|`string`|
|`ErrorCode`|A symbolic string constant that identifies the error. For example, *UserIsNotAuthorized*.|`string`|
|`FieldPath`|Reserved for future use.|`string`|
|`ForwardCompatibilityMap`|The list of key and value strings for forward compatibility. This element can be used to avoid otherwise breaking changes when new elements are added in future releases.<br /><br />**Note:** Forward compatibility changes will be noted here in future releases. There are currently no forward compatibility changes for this data object.|`KeyValuePairOfstringstring` array|
|`Index`|The zero-based index of the item in the batch of items in the request message that failed.|`int`|
|`Message`|A message that describes the error.|`string`|
|`Type`|Reserved for future use.|`string`|

## Requirements
[!INCLUDE[reqbulk](../bulk-api/includes/reqbulk.md)]
## See Also
[ApiFaultDetail](../bulk-api/apifaultdetail-data-object.md)


---
title: "BatchErrorCollection Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e752de9e-198f-45d1-8743-7675e8e46f75
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# BatchErrorCollection Data Object
Defines an error object that contains batch error details for the top level list index and a list of batch errors corresponding to the  nested list index. For example in the *NestedPartialErrors* response element for [AddNegativeKeywordsToEntities](../campaign-api/addnegativekeywordstoentities-service-operation.md), the top level error details correspond to the campaign or ad group in the service request. The nested list of batch errors would include any errors specific to the negative keywords that you attempted to add to the campaign or ad group.

## Syntax

```xml
<xs:complexType name="BatchErrorCollection">
  <xs:sequence>
    <xs:element minOccurs="0" name="BatchErrors" nillable="true" type="tns:ArrayOfBatchError"/>
    <xs:element minOccurs="0" name="Code" nillable="true" type="xs:int" />
    <xs:element minOccurs="0" name="Details" nillable="true" type="xs:string" />
    <xs:element minOccurs="0" name="ErrorCode" nillable="true" type="xs:string" />
    <xs:element minOccurs="0" name="FieldPath" nillable="true" type="xs:string"/>
    <xs:element xmlns:q9="http://schemas.datacontract.org/2004/07/System.Collections.Generic" minOccurs="0" name="ForwardCompatibilityMap" nillable="true" type="q9:ArrayOfKeyValuePairOfstringstring"/>
    <xs:element minOccurs="0" name="Index" type="xs:int" />
    <xs:element minOccurs="0" name="Message" nillable="true" type="xs:string" />
    <xs:element minOccurs="0" name="Type" nillable="true" type="xs:string" />
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*BatchErrors*|A list of batch errors corresponding to the nested list index.|[BatchError](../campaign-api/batcherror-data-object.md) array|
|*Code*|A numeric error code that identifies the error for the top level list index.|*int*|
|*Details*|A message that provides additional details about the batch error for the top level list index. This string can be empty.|*string*|
|*ErrorCode*|A symbolic string constant that identifies the error for the top level list index.|*string*|
|*FieldPath*|Reserved for future use.|*string*|
|*ForwardCompatibilityMap*|The list of key and value strings for forward compatibility. This element can be used to avoid otherwise breaking changes when new elements are added in future releases.<br /><br />**Note:** Forward compatibility changes will be noted here in future releases. There are currently no forward compatibility changes for this data object.|*KeyValuePairOfstringstring* array|
|*Index*|The zero-based top level list index in the request message that failed.|*int*|
|*Message*|A message that describes the error for the top level list index.|*string*|
|*Type*|Reserved for internal use.|*string*|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]



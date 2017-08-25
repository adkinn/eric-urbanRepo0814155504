---
title: "EditorialError Data Object"
ms.custom: ""
ms.date: "07/10/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 43212047-ca50-4485-bad0-ad532f779ad7
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# EditorialError Data Object
Defines an error object that identifies the entity with the batch of entities that failed editorial review.

## Syntax

```xml
<xs:complexType name="EditorialError">
  <xs:complexContent mixed="false">
    <xs:extension base="tns:BatchError">
      <xs:sequence>
        <xs:element minOccurs="0" name="Appealable" nillable="true" type="xs:boolean" />
        <xs:element minOccurs="0" name="DisapprovedText" nillable="true" type="xs:string" />
        <xs:element minOccurs="0" name="Location" nillable="true" type="xs:string" />
        <xs:element minOccurs="0" name="PublisherCountry" nillable="true" type="xs:string" />
        <xs:element minOccurs="0" name="ReasonCode" nillable="true" type="xs:int" />
      </xs:sequence>
    </xs:extension>
  </xs:complexContent>
</xs:complexType>
```

## <a name="Elements"></a>Elements
The `EditorialError` object inherits elements from the [BatchError](../bulk-api/batcherror-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#inheritedelements) below.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|`Appealable`|Reserved for future use.|`boolean`|
|`DisapprovedText`|The text that caused the entity to be disapproved.<br /><br />For text length violations, this element specifies the number of characters by which the specified text exceeds the maximum.|`string`|
|`Location`|The element or property of the entity that caused the entity to be disapproved.|`string`|
|`PublisherCountry`|The corresponding country or region for the flagged editorial issue.|`string`|
|`ReasonCode`|A numeric code that identifies the error. For more information, see [Editorial Failure Reason Codes](~/concepts/bing-ads-editorial-failure-reason-codes.md).|`int`|

## <a name="InheritedElements"></a>Inherited Elements
The `EditorialError` object inherits the following elements from the [BatchError](../bulk-api/batcherror-data-object.md) object. 

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
[Editorial Failure Reason Codes](~/concepts/bing-ads-editorial-failure-reason-codes.md)  


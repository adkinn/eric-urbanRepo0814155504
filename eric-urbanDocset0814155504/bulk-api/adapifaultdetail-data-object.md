---
title: "AdApiFaultDetail Data Object"
ms.custom: ""
ms.date: "07/10/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6a2d1e81-a6c2-43f5-a2e6-791efb1542eb
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AdApiFaultDetail Data Object
Defines a fault object that operations return when generic errors occur, such as an authentication error.

## Syntax

```xml
<xs:complexType name="AdApiFaultDetail">
  <xs:complexContent mixed="false">
    <xs:extension base="tns:ApplicationFault">
      <xs:sequence>
        <xs:element minOccurs="0" name="Errors" nillable="true" type="tns:ArrayOfAdApiError" />
      </xs:sequence>
    </xs:extension>
  </xs:complexContent>
</xs:complexType>
```

## <a name="Elements"></a>Elements
The `AdApiFaultDetail` object inherits elements from the [ApplicationFault](../bulk-api/applicationfault-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#inheritedelements) below.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|`Errors`|An array of [AdApiError](../bulk-api/adapierror-data-object.md) objects that contains the details that explain why the service operation failed.|[AdApiError](../bulk-api/adapierror-data-object.md) array|

## <a name="InheritedElements"></a>Inherited Elements
The `AdApiFaultDetail` object inherits the following element from the [ApplicationFault](../bulk-api/applicationfault-data-object.md) object. 

|Element|Description|Data Type|
|-----------|---------------|-------------|
|`TrackingId`|The identifier of the log entry that contains the details of the API call.|`string`|

## Requirements
[!INCLUDE[reqbulk](../bulk-api/includes/reqbulk.md)]

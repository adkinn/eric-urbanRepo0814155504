---
title: "ApiFaultDetail Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 050bdc0b-17e9-46ef-aaa5-6dc4fea96f76
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# ApiFaultDetail Data Object
Defines a fault object that operations return when web service-specific errors occur, such as when the request message contains incomplete or invalid data.

## Syntax

```xml
<xs:complexType name="ApiFaultDetail">
  <xs:complexContent mixed="false">
    <xs:extension xmlns:q2="https://adapi.microsoft.com" base="q2:ApplicationFault">
      <xs:sequence>
        <xs:element minOccurs="0" name="BatchErrors" nillable="true" type="tns:ArrayOfBatchError" />
        <xs:element minOccurs="0" name="OperationErrors" nillable="true" type="tns:ArrayOfOperationError" />
      </xs:sequence>
    </xs:extension>
  </xs:complexContent>
</xs:complexType>
```

## <a name="Elements"></a>Elements
The *ApiFaultDetail* object derives from the [ApplicationFault](../campaign-api/applicationfault-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#inheritedelements) below.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*BatchErrors*|An array of batch errors that identifies the items in the batch of items in the request message that caused the operation to fail. Each object contains the details that explain why the item caused the failure.|[BatchError](../campaign-api/batcherror-data-object.md) array|
|*OperationErrors*|An array of operation errors that contains the reasons that explain why the service operation failed when the error is not related to a specific item in the batch of items.|[OperationError](../campaign-api/operationerror-data-object.md) array|

## <a name="InheritedElements"></a>Inherited Elements
The *ApiFaultDetail* object derives from the [ApplicationFault](../campaign-api/applicationfault-data-object.md) object, and inherits the following element. 

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*TrackingId*|The identifier of the log entry that contains the details of the API call.|*string*|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]

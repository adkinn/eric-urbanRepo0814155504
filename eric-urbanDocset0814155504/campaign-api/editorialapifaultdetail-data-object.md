---
title: "EditorialApiFaultDetail Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f83f51bc-cb4b-4379-9a2d-bc9149a7b3da
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# EditorialApiFaultDetail Data Object
Defines a fault object that operations such as [AddAdGroupCriterions](../campaign-api/addadgroupcriterions-service-operation.md), [UpdateAdGroupCriterions](../campaign-api/updateadgroupcriterions-service-operation.md), [SetAdExtensionsAssociations](../campaign-api/setadextensionsassociations-service-operation.md), and [UpdateAdExtensions](../campaign-api/updateadextensions-service-operation.md) return when one or more criterion or ad extensions in your request message fail editorial review.

## Syntax

```xml
<xs:complexType name="EditorialApiFaultDetail">
  <xs:complexContent mixed="false">
    <xs:extension xmlns:q14="https://adapi.microsoft.com" base="q14:ApplicationFault">
      <xs:sequence>
        <xs:element minOccurs="0" name="BatchErrors" nillable="true" type="tns:ArrayOfBatchError" />
        <xs:element minOccurs="0" name="EditorialErrors" nillable="true" type="tns:ArrayOfEditorialError" />
        <xs:element minOccurs="0" name="OperationErrors" nillable="true" type="tns:ArrayOfOperationError" />
      </xs:sequence>
    </xs:extension>
  </xs:complexContent>
</xs:complexType>
```

## <a name="Elements"></a>Elements
The *EditorialApiFaultDetail* object derives from the [ApplicationFault](../campaign-api/applicationfault-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#InheritedElements) below.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*BatchErrors*|An array of batch errors that identifies the items in the batch of items in the request message that caused the operation to fail. Each object contains the details that explain why the item caused the failure.|[BatchError](../campaign-api/batcherror-data-object.md) array|
|*EditorialErrors*|An array of editorial errors that contains the details that explain why the criterion or ad extension was disapproved.|[EditorialError](../campaign-api/editorialerror-data-object.md) array|
|*OperationErrors*|An array of operation errors that contains the details that explain why the service operation failed when the error is not related to a specific item in the batch of items.|[OperationError](../campaign-api/operationerror-data-object.md) array|

## <a name="InheritedElements"></a>Inherited Elements
The *EditorialApiFaultDetail* object derives from the [ApplicationFault](../campaign-api/applicationfault-data-object.md) object, and inherits the following element. 

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*TrackingId*|The identifier of the log entry that contains the details of the API call.|*string*|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]

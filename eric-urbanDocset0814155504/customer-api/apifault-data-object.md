---
title: "ApiFault Data Object"
ms.custom: ""
ms.date: "04/03/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 496cabf1-69b5-44ca-a4d1-4babcb0c84b9
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# ApiFault Data Object
Defines a fault object that operations return when web service-specific errors occur, such as when the request message contains incomplete or invalid data.

## Syntax

```xml
<xs:complexType name="ApiFault">
  <xs:complexContent mixed="false">
    <xs:extension base="q1:ApplicationFault" xmlns:q1="https://adapi.microsoft.com">
      <xs:sequence>
        <xs:element minOccurs="0" name="OperationErrors" nillable="true" type="tns:ArrayOfOperationError" />
      </xs:sequence>
    </xs:extension>
  </xs:complexContent>
</xs:complexType>
```

## <a name="Elements"></a>Elements
The *ApiFault* object derives from the [ApplicationFault](../customer-api/applicationfault-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#InheritedElements) below.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*BatchErrors*|An array of *OperationError* objects that contains the reasons that explain why the service operation failed when the error is not related to a specific item in the batch of items.|[OperationError](../customer-api/operationerror-data-object.md) array|

## <a name="InheritedElements"></a>Inherited Elements
The *ApiFault* object derives from the [ApplicationFault](../customer-api/applicationfault-data-object.md) object, and inherits the following element. 

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*TrackingId*|The identifier of the log entry that contains the details of the API call.|*string*|

## Requirements
[!INCLUDE[reqcus](../customer-api/includes/reqcus.md)]
## See Also
[Handling Service Errors and Exceptions](~/concepts/handling-service-errors-and-exceptions.md)


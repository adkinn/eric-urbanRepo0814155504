---
title: "ApiBatchFault Data Object"
ms.custom: ""
ms.date: "04/03/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ed5a41c0-15de-4846-98c9-b35fe358d533
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# ApiBatchFault Data Object
Defines a fault object that operations return when web service-specific errors occur, such as when the request message contains incomplete or invalid data.

## Syntax

```xml
<xs:complexType name="ApiBatchFault">
  <xs:complexContent mixed="false">
    <xs:extension base="tns:ApiFault">
      <xs:sequence>
        <xs:element minOccurs="0" name="BatchErrors" nillable="true" type="tns:ArrayOfBatchError" />
      </xs:sequence>
    </xs:extension>
  </xs:complexContent>
</xs:complexType>
```

## <a name="Elements"></a>Elements
The *ApiBatchFault* object derives from the [ApiFault](../billing-api/apifault-data-object.md) object, that derives from the [ApplicationFault](../billing-api/applicationfault-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#InheritedElements) below.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*BatchErrors*|An array of *BatchError* objects that identifies the items in the batch of items in the request message that caused the operation to fail. Each object contains the details that explain why the item caused the failure.|[BatchError](../billing-api/batcherror-data-object.md) array|

## <a name="InheritedElements"></a>Inherited Elements
### <a name="InheritedElementsApiFault"></a>Inherited Elements from ApiFault
The *ApiBatchFault* object derives from the [ApiFault](../billing-api/apifault-data-object.md) object and inherits the following element.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*BatchErrors*|An array of *OperationError* objects that contains the reasons that explain why the service operation failed when the error is not related to a specific item in the batch of items.|[OperationError](../billing-api/operationerror-data-object.md) array|

### <a name="InheritedElementsApplicationFault"></a>Inherited Elements from ApplicationFault
The *ApiFault* object derives from the [ApplicationFault](../billing-api/applicationfault-data-object.md) object, and inherits the following element. 

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*TrackingId*|The identifier of the log entry that contains the details of the API call.|*string*|

## Requirements
[!INCLUDE[reqbilling](../billing-api/includes/reqbilling.md)]
## See Also
[Handling Service Errors and Exceptions](https://msdn.microsoft.com/library/bing-ads-error-handling-guide.aspx)


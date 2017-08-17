---
title: "ApiFault Data Object"
ms.custom: ""
ms.date: "04/03/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f29720e4-2247-4d8a-9d5b-9d0459db9dac
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# ApiFault Data Object
Defines a fault object that operations return when web service-specific errors occur, such as when the request message contains incomplete or invalid data.

## Syntax

```xml
\<xs:complexType name="ApiFault">
  \<xs:complexContent mixed="false">
    \<xs:extension base="q1:ApplicationFault" xmlns:q1="https://adapi.microsoft.com">
      \<xs:sequence>
        \<xs:element minOccurs="0" name="OperationErrors" nillable="true" type="tns:ArrayOfOperationError" />
      \</xs:sequence>
    \</xs:extension>
  \</xs:complexContent>
\</xs:complexType>
```

## <a name="Elements"></a>Elements
The *ApiFault* object derives from the [ApplicationFault](../billing-api/applicationfault-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#InheritedElements) below.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*BatchErrors*|An array of *OperationError* objects that contains the reasons that explain why the service operation failed when the error is not related to a specific item in the batch of items.|[OperationError](../billing-api/operationerror-data-object.md) array|

## <a name="InheritedElements"></a>Inherited Elements
The *ApiFault* object derives from the [ApplicationFault](../billing-api/applicationfault-data-object.md) object, and inherits the following element. 

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*TrackingId*|The identifier of the log entry that contains the details of the API call.|*string*|

## Requirements
[!INCLUDE[reqbilling](../billing-api/includes/reqbilling.md)]
## See Also
[Handling Service Errors and Exceptions](https://msdn.microsoft.com/library/bing-ads-error-handling-guide.aspx)


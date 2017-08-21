---
title: "AdApiFaultDetail Data Object"
ms.custom: ""
ms.date: "04/03/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8baa6bbf-ffd5-41ae-ab79-3918c9e33204
caps.latest.revision: 8
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
The *AdApiFaultDetail* object derives from the [ApplicationFault](../customer-api/applicationfault-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#InheritedElements) below.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Errors*|An array of *AdApiError* objects that contains the details that explain why the service operation failed.|[AdApiError](../customer-api/adapierror-data-object.md) array|


## <a name="InheritedElements"></a>Inherited Elements
The *AdApiFaultDetail* object derives from the [ApplicationFault](../customer-api/applicationfault-data-object.md) object, and inherits the following element. 

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*TrackingId*|The identifier of the log entry that contains the details of the API call.|*string*|

## Requirements
[!INCLUDE[reqcus](../customer-api/includes/reqcus.md)]
## See Also
[Handling Service Errors and Exceptions](~/concepts/handling-service-errors-and-exceptions.md)

